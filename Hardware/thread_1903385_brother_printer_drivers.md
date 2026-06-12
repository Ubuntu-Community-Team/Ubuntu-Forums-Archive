---
title: "brother printer drivers"
date: 2012-01-02
forum: Hardware
---

### Post by netopalis45 on 2012-01-02
I have been trying to set up my Brother 490CW printer on my laptop with Ubuntu 11.10 64-bit. I have the drivers for the 32-bit and they work perfectly on my other Ubuntu computers but I have not been able to find drivers for the 64-bit. Are there any out there?

---

### Post by crazy bird on 2012-01-02
Check here: [https://sites.google.com/site/tipsandtricksforubuntu/printer-info/brother](https://sites.google.com/site/tipsandtricksforubuntu/printer-info/brother).

---

### Post by jpateusa on 2012-01-02
I had the same printer MFC490CW. I did install it on Ubuntu 11.10. Here is the page for the drivers. You must follow the instructions for installation. As for the scanner portion to work, follow the instructions and then follow the additional link. You have to move some files for it to work.

Printer:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-490CW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-490CW) (you must follow the install instructions for this to work) 
Scanner:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan3](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan3)
Scanner After Install:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101) (use brscan3) only if using 11.10. Not needed in previous releases, I think.

Jason

---

### Post by netopalis45 on 2012-01-02
I already have those drivers and I get an error in Software Center that says "Wrong architecture 'i386'"

---

### Post by crazy bird on 2012-01-02
> **netopalis45 said:**
> I already have those drivers and I get an error in Software Center that says "Wrong architecture 'i386'"
 
If you get such messages, then the drivers are only for 32-bit CPU systems. Some other Brother owners tried installing the correct Brother driver using the Windows driver in combination with WINE. You could try that.

---

### Post by librechick on 2012-01-03
He has a brother printer and you are going to suggest installing canon drivers? That won't work.

---

### Post by crazy bird on 2012-01-03
> **librechick said:**
> He has a brother printer and you are going to suggest installing canon drivers? That won't work.
 
Yes, stupid me :D
Edited my post to the correct manufacturer ;-)

---

### Post by netopalis45 on 2012-01-16
I have tried installing the Windows drivers with Wine but it hangs at the end of the installation and doesn't work

---

### Post by kurt18947 on 2012-01-16
I've installed Brother drivers on several machines.  The printer drivers do not have 64 bit versions.  On 64 bit systems you must install from the command line using --force-all to make an end-run around the architecture error message. this is also the reason that before installing, make sure **ia32-libs or ****lib32stdc++** are installed.  These are part of what enables 64 bit OSs to use 32 bit drivers.   For example:

 dpkg  -i  --force-all  (lpr-drivername).  

Do not include the parentheses.  For whatever reason scanner drivers are available in 64 bit but I still use the command line install.  A tip when typing files names -- cd to the directory where the .deb file is then type 'dir'.  You'll get a listing of files including the .deb you're looking for.  You can then copy/paste the file name to avoid typos.

---

