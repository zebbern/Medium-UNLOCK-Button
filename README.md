# Installation

1. **Install [Tampermonkey](https://tampermonkey.net/).**  
   Works with Chrome, Firefox, and more.

2. Go to extensions and enable developer mode or else it wont work

![image](https://github.com/user-attachments/assets/014993ae-db63-43c7-8abd-9417c55b33ff)

---

3. **Create a New Script** in Tampermonkey.  
   - Copy the script below.  
   - Save and enable.

```javascript
// ==UserScript==
// @name         Medium UNLOCK Button (COM Only)
// @namespace    https://tampermonkey.net/
// @version      1.0
// @description  Adds a "UNLOCK" button on Medium github.com/zebbern for more
// @match        *://*/*
// @grant        none
// ==/UserScript==

(function() {
    'use strict';

    const host = window.location.hostname.toLowerCase();

    // Show button ONLY if:
    // 1) The domain includes "medium"
    // 2) The domain ends with ".com"
    if (!host.includes('medium') || !host.endsWith('.com')) {
        return; // Do nothing
    }

    // Create UNLOCK button
    const unlockBtn = document.createElement('button');
    unlockBtn.textContent = 'UNLOCK';

    // Basic styling
    unlockBtn.style.position = 'fixed';
    unlockBtn.style.bottom = '20px';
    unlockBtn.style.right = '20px';
    unlockBtn.style.zIndex = '9999';
    unlockBtn.style.padding = '12px 18px';
    unlockBtn.style.fontSize = '14px';
    unlockBtn.style.fontFamily = 'sans-serif';
    unlockBtn.style.backgroundColor = '#0077cc';
    unlockBtn.style.color = '#ffffff';
    unlockBtn.style.border = 'none';
    unlockBtn.style.borderRadius = '4px';
    unlockBtn.style.cursor = 'pointer';
    unlockBtn.style.boxShadow = '0 3px 8px rgba(0, 0, 0, 0.2)';
    unlockBtn.style.opacity = '0.9';
    unlockBtn.style.transition = 'all 0.2s ease';

    // Hover effect
    unlockBtn.addEventListener('mouseenter', () => {
        unlockBtn.style.opacity = '1';
        unlockBtn.style.transform = 'translateY(-2px)';
        unlockBtn.style.boxShadow = '0 6px 12px rgba(0, 0, 0, 0.2)';
    });
    unlockBtn.addEventListener('mouseleave', () => {
        unlockBtn.style.opacity = '0.9';
        unlockBtn.style.transform = 'translateY(0)';
        unlockBtn.style.boxShadow = '0 3px 8px rgba(0, 0, 0, 0.2)';
    });

    // On click, redirect to Freedium
    unlockBtn.addEventListener('click', () => {
        const withoutProtocol = window.location.href.replace(/^https?:\/\//, '');
        window.location.href = 'https://freedium.cfd/' + withoutProtocol;
    });

    // Add button to the page
    document.body.appendChild(unlockBtn);
})();

```

## Usage

- **Open any Medium page** (e.g. a member-only article).  
- Click **UNLOCK** in the bottom-right corner.  
- Enjoy your **Freedium** version!  

---

### Made with ❤️ by [zebbern](https://github.com/zebbern)

### sh to freedium.cfd for providing the full pages
