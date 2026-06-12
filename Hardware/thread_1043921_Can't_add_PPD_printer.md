---
title: "Can't add PPD printer"
date: 2009-01-19
forum: Hardware
---

### Post by jason50146 on 2009-01-19
I'm trying to add a networked laser printer to Kubuntu Intrepid.  When I get to the point where it asks to point to the PPD file, the "three dots" button does nothing.  I expect clicking on that button should open a navigation dialogue where I can point to the file.  

When I enter the path manually, I noticed the error below in the terminal.  It looks like system-config-print-kde is not able to retrieve the information I have entered.

Thoughts?

```
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer-kde.py", line 1774, in on_btnNPForward_clicked
    self.nextNPTab()
  File "/usr/share/system-config-printer/system-config-printer-kde.py", line 1967, in nextNPTab
    self.ppd = self.getNPPPD()
  File "/usr/share/system-config-printer/system-config-printer-kde.py", line 2870, in getNPPPD
    ppd = cups.PPD(unicode(self.filechooserPPD.getText()))
AttributeError: getText

```

---

