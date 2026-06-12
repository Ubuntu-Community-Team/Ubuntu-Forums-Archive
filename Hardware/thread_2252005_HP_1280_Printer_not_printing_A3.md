---
title: "HP 1280 Printer not printing A3"
date: 2014-11-08
forum: Hardware
---

### Post by Deanobats on 2014-11-08
Hi all, I'm on 14.04 64bit and using HPLIP-3.14.3 to print wirelessly to a HP Officejet Pro 8100 (all fine) and via USB to an old but still pretty good HP 1280 A3 printer. The issue that I have is that it will print fine to A4 on the HP 1280, but when I try to print A3, I set the paper size to A3, the preview looks fine, but only an A4 crop of the image is printed onto the A3 paper. I've tried setting the default paper size to A3, messing around with the paper tray options and pretty much every other setting I can find, but to no avail. Any suggestions? A quick google has shown that this has been a problem with older HPLIP versions, but this seems oto be because usually the A3 option has been left off. In this case, it's there, but setting it seems to make no difference.
Ta for any suggestions!

Dean

---

### Post by Deanobats on 2014-11-08
Having run a few more tests, the image is scaling correctly to A3, but only an A4 'window' is being printed (see attached for the test page output onto A3 paper).

---

### Post by Deanobats on 2014-11-09
I've now tracked down and had a good look at the Deskjet-1280.ppd file and all seems to be in order, the A3 entries are there, the paper sizes check out as well. Mysterious, and rather a shame as it's a good printer and useful for the occasions I need to print out in A3.

---

### Post by Deanobats on 2014-11-11
Well, I've admitted defeat on this one, no way does it print to A3 in any shape or form that I can see. The image scales to A3, it's just that the printer will only print an A4 'window' of it onto the paper. In the end I installed the Windows XP drivers onto an XP VM that I'm running under VirtualBox. If I want to print to A3 I have to save the document to a windows compatible format, open the VM, open the document and print from there. It works fine. Though it's obviously a little cumbersome.

---

### Post by strife666 on 2014-11-24
Got same problem with clean install ubuntu 14.04 using deskjet 9800.  Problem solved by installing printer-driver-hpijs (3.14.3-0ubuntu3.2) and choosing that driver during printer setup than the default.

---

### Post by GTsavci on 2015-09-30
Thanks a lot strife666. Installing printer-driver-hpijs and choosing that driver from printer settings solved my printing issue on A3 paper with my HP 1280 Deskjet printer. Thanks again.

---

