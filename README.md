# SIGN LEADS USA - State Page System

## Quick Start

### Files Overview
- **index.html** - Main landing page with interactive US heat map
- **texas-sign-leads.html** - Example state page (Texas with 250+ leads)
- **state-template.html** - Template for creating new state pages

## How to Add a New State

### Step 1: Copy the Template
```bash
cp state-template.html [state-name]-sign-leads.html
# Example: cp state-template.html california-sign-leads.html
```

### Step 2: Update Configuration (Lines 125-126)
```javascript
const STATE_CODE = 'CA'; // Two-letter code
const STATE_NAME = 'California'; // Full name
```

### Step 3: Update Header Title (Line 6)
```html
<title>CALIFORNIA SIGN LEADS - COMPLETE DATABASE</title>
```

### Step 4: Update Header Text (Line 62)
```html
<h1>CALIFORNIA SIGN LEADS - COMPLETE DATABASE</h1>
```

### Step 5: Add Region/County Filter Options (Lines 71-73)
```html
<select id="countyFilter" onchange="filterLeads()">
    <option value="all">All Regions</option>
    <option value="los-angeles">Los Angeles</option>
    <option value="san-diego">San Diego</option>
    <!-- Add your regions -->
</select>
```

### Step 6: Add Your Lead Data (Lines 130-142)
```javascript
const allLeads = [
    {
        county: 'los-angeles',
        temp: 'hot',
        name: 'Target Westwood',
        subtitle: 'Retail Expansion',
        location: '10861 Weyburn Ave, Los Angeles',
        contact: 'Target Corporate',
        phone: '(612) 304-6073',
        opening: 'Spring 2026',
        signage: ['Monument sign', 'Channel letters', 'Interior wayfinding'],
        revenue: '$45K - $65K'
    },
    // Add more leads...
];
```

### Step 7: Register State in index.html (Line 222)
```javascript
'CA': { name: 'California', leads: 0, hasPage: true, url: 'california-sign-leads.html' },
```

## Lead Data Structure

Each lead object requires:
- **county**: Region identifier (lowercase, use hyphens)
- **temp**: 'hot' or 'warm'
- **name**: Business/project name
- **subtitle**: Brief description
- **location**: Full address
- **contact**: Company or person
- **phone**: Contact number
- **opening**: Expected date
- **signage**: Array of signage types needed
- **revenue**: Estimated revenue range

## Automatic Features

### Real-Time Sync
- Lead counts automatically sync between state pages and the main map
- Changes persist across browser sessions
- Updates reflect instantly across open tabs

### Heat Map Colors
The map automatically color-codes states based on lead count:
- **Red**: Full database available (hasPage: true)
- **Light Gray**: 100+ leads
- **Medium Gray**: 50-99 leads
- **Dark Gray**: 10-49 leads
- **Darker Gray**: 1-9 leads
- **Darkest**: Coming soon (0 leads)

### Access Control
- Currently open for testing (all states clickable)
- States without pages show "Premium Access Required" modal
- Comment out line 262 in index.html to enable access control:
  ```javascript
  // window.location.href = data.url; // Comment this line
  ```

## Testing

1. Open `index.html` in your browser
2. Lead counts should update automatically
3. Click Texas to see the full state page
4. Add new states following the steps above

## Production Deployment

When ready for production:
1. Enable access control (see Access Control above)
2. Integrate with your authentication system
3. Replace `alert()` calls with real CRM integration
4. Add analytics tracking

## File Structure
```
/
├── index.html (main landing page)
├── texas-sign-leads.html (example state)
├── california-sign-leads.html (your new states)
├── florida-sign-leads.html
└── state-template.html (template)
```

## Notes

- State codes must be 2 letters (standard US postal codes)
- Lead counts sync via localStorage
- Browser storage persists data indefinitely
- Works across multiple tabs
- Template includes all styling and functionality
