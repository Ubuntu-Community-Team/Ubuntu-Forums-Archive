---
title: "firefox - downloads failing - have to restart firefox"
date: 2008-11-16
forum: General Help
---

### Post by bagpussnz on 2008-11-16
Hi,
I saw this on 8.04 - and it still happens on 8.10.
After firefox has been running for awhile, I click on a link to download something, the directory chooser opens - and I select a valid directory, but the file never downloads.

It's as if when you select the directory, it never gets passed to the download manager.

In the error console, I see,
Error: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIHelperAppLauncher.saveToDisk]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: file:///usr/lib/xulrunner-1.9.0.3/components/nsHelperAppDlg.js :: anonymous :: line 448"  data: no]
Source File: file:///usr/lib/xulrunner-1.9.0.3/components/nsHelperAppDlg.js
Line: 448

If I close and restart firefox, then the download succeeds - has anyone seen this?

Cheers,
Ian.

---

### Post by kostkon on 2008-11-16
> **bagpussnz said:**
> Hi,
I saw this on 8.04 - and it still happens on 8.10.
After firefox has been running for awhile, I click on a link to download something, the directory chooser opens - and I select a valid directory, but the file never downloads.

It's as if when you select the directory, it never gets passed to the download manager.

If I close and restart firefox, then the download succeeds - has anyone seen this?

Cheers,
Ian.
No, but it's really strange.

Can you see the download in the download manager window? What status does it have (e.g. paused etc.)?

Have you tried reinstalling Firefox?

---

