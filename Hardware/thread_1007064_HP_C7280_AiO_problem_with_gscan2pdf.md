---
title: "HP C7280 AiO problem with gscan2pdf"
date: 2008-12-10
forum: Hardware
---

### Post by shadok on 2008-12-10
Hi!

I updated an ubuntu 8.04 Installation to 8.10, and gscan2pdf does not work properly anymore:
- I'm still able to scan
- But, I don't get the possibility to change some Scan Options, as no Scan Options are shown.

With Ubuntu 8.04, everything worked well.

My Scanner is a HP Photosmart C7280, I'm using HPLIP, the Photosmart Scanner is connected through Ethernet, Printing works, the HP Device Manager shows the Printer and the status information, etc.

Thanks for some advice,
Regards,
Christophe

---

### Post by David Valentine on 2009-02-18
I am running Intrepid x64 with the HP C7280 AiO, and I do get scanner options in gscan2pdf.  Are you still having troubles?  You might try deleting .gscan2pdf in your home directory and reinstall gscan2pdf...

---

### Post by shadok on 2009-02-18
Hi David,

I resolved the problem since then. 

If I remember well, reinstalling gscan2pdf + deleting the configuration was not enough, the problem remained. 

I think (I can't remember in details), I deleted the "sane" configuration (better, renamed it), and reinstalled sane and the HP drivers. And now, gscan2pdf works as it should (and as it did on a debian installation I have too). 

Kind Regards from Germany,

   Christophe

---

