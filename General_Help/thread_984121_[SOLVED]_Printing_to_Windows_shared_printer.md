---
title: "[SOLVED] Printing to Windows shared printer"
date: 2008-11-16
forum: General Help
---

### Post by jay302_99 on 2008-11-16
Hey folks -
I have a box running Windows XP Pro with an HP Deskjet 3940 installed and shared. I can print fine from another XP box, I can connect the printer locally to the Ubunto box and print fine. I can connect to the shared printer from the Ubunto box with no problems. 

Here's where the problem lies.
When I send a test page to the printer, the print queue shows it sent 150K. When I check the print queue on the winXP box, it shows a size of 7.24 MB. It stalls out at 64K. Data type of the print job is RAW, it doesn't seem to be spooling properly. 

I have run into this problem trying other distros, but never got a fix for this.
Any ideas?

---

### Post by jay302_99 on 2008-11-22
Am I the only one that's run into this?

---

### Post by jay302_99 on 2008-11-30
I guess I'll go back to Windows.

---

### Post by jay302_99 on 2008-11-30
I found it, it was a ridicoulously simple fix.

Basically disabling bi-directional support on the XP box did the trick.
I guess I just wasn't searching for the right terms when I searched the forums.

[http://ubuntuforums.org/showthread.php?t=472987](http://ubuntuforums.org/showthread.php?t=472987)

[http://lists.samba.org/archive/samba/2005-October/112851.html](http://lists.samba.org/archive/samba/2005-October/112851.html)

---

