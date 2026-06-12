---
title: "Unable to boot with hot swap hard drives"
date: 2008-06-26
forum: Hardware
---

### Post by Christopher1940 on 2008-06-26
I have a dual boot system with Ubuntu Linux on 1 hard drive and Windows Vista on another. I have edited the boot loader so the machine boots to Windows but I can change it at start up to boot to  Linux. I also have an Adonics 3 drive hot swap bay set up but when it is powered up I get a Grub Error 17 on boot up. If not powered up it boots up correctly.

Currently the Linux hard drive is internal. Previously I had it in one of the hot swap bays and it worked fine there. The disks in the hot swap bays are data only and they worked fine until I moved the Linux hard drive into the desktop box.

Any suggestions would be appreciated.

---

### Post by Ng Oon-Ee on 2008-06-26
Hi, this sounds like a problem similar to [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=836542"). Go ahead and read my post there (can't miss it, its the long one on the first page).

I'd suggest booting in using your previous settings (ie, without the hot swap powered up) and editing your menu.lst to use UUIDs (explanation how and why in the afore-mentioned thread).

You may have to modify fstab as well, but I doubt it as I think it defaults to using UUIDs. It may help if you copy your fstab and paste it here.

---

