# 📅 Calendar Holidays

A comprehensive, automatically updated repository of holiday data for multiple countries. This project maintains current and future holiday information synchronized from the Calendarific API, providing structured JSON data for integration into applications and services.

---

## 🌍 Overview

**Calendar Holidays** is a curated collection of holiday data spanning multiple countries and years. The repository is automatically updated weekly to ensure accuracy and completeness. It serves as a reliable data source for developers building calendar applications, scheduling systems, or any service requiring holiday information.

### Supported Countries
- 🇮🇳 India (IN)
- 🇸🇦 Saudi Arabia (SA)
- 🇺🇸 United States (US)
- 🇦🇪 United Arab Emirates (AE)
- 🇮🇷 Iran (IR)

---

## 📊 Data Structure

The repository maintains a consistent directory structure:

```
holidays/
├── metadata.json          # Central metadata with sync information
├── IN/                    # India holidays
│   ├── 2026.json
│   ├── 2027.json
│   └── ...
├── SA/                    # Saudi Arabia holidays
├── US/                    # United States holidays
├── AE/                    # United Arab Emirates holidays
└── IR/                    # Iran holidays
```

### Data Format

Each country's JSON file contains an array of holiday objects with the following schema:

```json
[
  {
    "name": "New Year's Day",
    "description": "New Year's Day",
    "type": "National public holiday",
    "primary_type": "public_holiday",
    "canonical_url": "https://...",
    "locations": "All",
    "states": "All",
    "date": {
      "iso": "2026-01-01",
      "datetime": {
        "year": 2026,
        "month": 1,
        "day": 1
      }
    }
  }
]
```

### Metadata Format

The `metadata.json` file provides synchronization information and holiday counts:

```json
{
  "version": 3,
  "updated": "2026-07-23T01:28:48Z",
  "countries": {
    "IN": {
      "2026": {
        "holidayCount": 22,
        "lastUpdated": "2026-07-23T01:28:48Z"
      }
    }
  }
}
```

---

## 🚀 Usage

### Direct File Access

Access holiday data directly via GitHub's raw content URL:

```bash
# Get United States holidays for 2026
curl https://raw.githubusercontent.com/zehdso/calendar-holidays/main/holidays/US/2026.json

# Get metadata
curl https://raw.githubusercontent.com/zehdso/calendar-holidays/main/holidays/metadata.json
```

### Integration Examples

**JavaScript/Node.js:**
```javascript
async function getHolidays(country, year) {
  const url = `https://raw.githubusercontent.com/zehdso/calendar-holidays/main/holidays/${country}/${year}.json`;
  const response = await fetch(url);
  return response.json();
}

// Usage
const usHolidays = await getHolidays('US', 2026);
console.log(usHolidays);
```

**Python:**
```python
import requests
import json

def get_holidays(country, year):
    url = f"https://raw.githubusercontent.com/zehdso/calendar-holidays/main/holidays/{country}/{year}.json"
    response = requests.get(url)
    return response.json()

# Usage
in_holidays = get_holidays('IN', 2026)
print(json.dumps(in_holidays, indent=2))
```

---

## 🔄 Automation

### Update Schedule

This repository is automatically updated **every Monday at 2:00 AM UTC** via GitHub Actions. The workflow:

1. ✅ Fetches the latest holiday data from the Calendarific API
2. ✅ Processes and validates the data
3. ✅ Updates country-specific JSON files
4. ✅ Maintains metadata with sync timestamps
5. ✅ Commits changes automatically

### Data Coverage

- **Current Year**: Latest year data
- **Future Years**: Up to 4 years ahead
- **Automatic Cleanup**: Outdated year files are automatically removed

---

## 📋 File Listing

| Country | Code | Coverage |
|---------|------|----------|
| India | `IN` | 2026-2030 |
| Saudi Arabia | `SA` | 2026-2030 |
| United States | `US` | 2026-2030 |
| United Arab Emirates | `AE` | 2026-2030 |
| Iran | `IR` | 2026-2030 |

---

## 🔗 Data Source

Holiday data is sourced from **[Calendarific API](https://calendarific.com/)**, a comprehensive international holiday database providing accurate and up-to-date information for numerous countries.

---

## 📝 License

This project is publicly available for use. Please refer to the license terms for specific usage rights.

---

## 🤝 Contributing

Contributions and suggestions are welcome! If you'd like to:
- Add support for additional countries
- Report data accuracy issues
- Suggest improvements

Please open an issue or submit a pull request.

---

## ⚙️ Technical Details

### Technology Stack
- **Language**: Shell Script (Bash)
- **Data Format**: JSON
- **Automation**: GitHub Actions
- **API Integration**: Calendarific v2

### Repository Statistics
- **Updates**: Weekly
- **Last Updated**: Check `metadata.json` for precise timestamp
- **Data Format Version**: v3

---

## ❓ FAQ

**Q: How often is the data updated?**  
A: The repository is automatically updated every Monday at 2:00 AM UTC.

**Q: Can I add more countries?**  
A: Yes! You can submit a pull request to add new countries to the `COUNTRIES` environment variable in the GitHub Actions workflow.

**Q: How far into the future does the data extend?**  
A: Data covers the current year plus 4 years into the future (configurable via `FUTURE_YEARS` in the workflow).

**Q: Is the data accurate?**  
A: Data is sourced from Calendarific API, a reputable holiday database. However, we recommend verifying critical dates.

---

## 📞 Support

For issues, questions, or feature requests, please open an issue on GitHub.

---

**Last Updated**: 2026-07-23  
**Version**: 3.0  
**Maintainer**: [@zehdso](https://github.com/zehdso)
