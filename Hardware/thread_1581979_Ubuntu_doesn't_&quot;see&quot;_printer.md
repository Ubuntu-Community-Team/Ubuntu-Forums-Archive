---
title: "Ubuntu doesn't &quot;see&quot; printer"
date: 2010-09-25
forum: Hardware
---

### Post by notquitestr8t on 2010-09-25
I found a driver for my printer and it worked....once. Now when I attempted to print, the printer comes up and it shows printing status but nothing comes out of the printer. Unpluging and plugging the printer back in does nothing. 
Cannon IP4700 w/USB connection
Printer screen says connected to local host
Tried restarting CUPS but that does not seem to help. Printer status is Idle. Restarting printer does not help.
It appears that Ubuntu isn't sensing the printer connection.
Running Lucid Lynx 10.04 x64
Any suggestions are welcome. I hate having to boot to Windows just to print.
CO

---

### Post by r_avital on 2010-10-11
Since the time it worked once, have there been any updates to the kernel?

I may be way off base here, but:  When you go to System>Administration>Printing, select Server from the menu, then select Connect.  See the drop-down, what options do you have in there?  I'm connected to /var/run/cups/cups.sock - even though it still reads "connected to localhost" in the status-bar of that window.  Then again, I'm connected to the printer via a print-server on my lan, so I'm not sure this applies.

Also make sure that the ghostscript and ghostscript-cups packages are installed.

Again, no idea if any of this will help, and if it doesn't, apologies in advance.

---

### Post by notquitestr8t on 2010-10-14
Thanks for your input. I was able to resolve. Removing and reinstalling CUPS did the trick for me.

---

### Post by termin on 2010-10-14
mark this thread as solved by going to the thread tools at the top of the page

---

