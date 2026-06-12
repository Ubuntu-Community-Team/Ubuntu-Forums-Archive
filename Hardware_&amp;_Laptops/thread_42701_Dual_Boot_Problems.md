---
title: "Dual Boot Problems"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by igb on 2005-06-19
I am having some problems getting Ubuntu to co-exist with Windows 2000. After installing Ubuntu Windows reports "inaccessible boot device" and blue screens part way into starting the GUI.

I have had this problem before with FC2 on the same hardware. It seems that the 2.6 kernel reports different geometries to the 2.4 kernel. Here's a summary of what I have tried so far:

Wipe all partitions. 
Set disk access mode to LBA.
Install Windows 2000
Install Ubuntu - blue screen when loading Windows.
Run fixmbr from Windows recovery console - still blue screens.

Note that SuSE 9.2 (2.6 kernel) or SuSE 9.0 (2.4 kernel) will coexist quite happily with Windows 2000 on the same hardware.

Any suggestions as how to make Windows bootable?

Ian.

---

### Post by Xian on 2005-06-19
If you've wiped all your partitions and reset the MBR in Windows recovery mode, and it still won't boot then I honestly don't know what else it could be save for some type of bios config. I think on my box I had to set the disk access to Large, which was weird because most people say LBA, and then I toggled the manual and autommatic settings but forget which I actually settled with.

---

