---
title: "Installed printer does nothing"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by njKeever on 2007-12-09
I have read every post I can find and to no avail. My HP Deskjet 712C printer is installed, and programs will send things to the print queue, but there they stay. The printer never even attempts to print.

---

### Post by Sef on 2007-12-09
Sorry to tell you this, but the [712C]("http://hplip.sourceforge.net/supported_devices/unsupported.html") is one of the few HP printers no supported by HPLIP, and there are not plans do support it by HP.

However, [Openprinting.org]("http://www.openprinting.org/show_printer.cgi?recnum=HP-DeskJet_712C") has a way of making it work.

---

### Post by njKeever on 2007-12-09
Thank you very much for your reply. It does seem that they support my printer, but I cannot figure out how. I have downloaded the PPD file and used it to install the printer, but it still will not print.

---

### Post by njKeever on 2007-12-12
Wow, after HOURS of searching I finally found the incredibly simple solution at: [http://ubuntuforums.org/showthread.php?t=579519](http://ubuntuforums.org/showthread.php?t=579519). Please mark this thread as solved.

---

### Post by njKeever on 2007-12-12
Of course I open my mouth too soon. While this code did fix my problem, I have to run it everytime I restart. Is there a simple way of making whatever "sudo aa-complain cupsd" does permanent?

---

