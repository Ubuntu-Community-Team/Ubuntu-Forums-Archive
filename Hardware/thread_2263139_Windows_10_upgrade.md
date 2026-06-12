---
title: "Windows 10 upgrade"
date: 2015-01-29
forum: Hardware
---

### Post by ndiniz on 2015-01-29
Will Updating to windows 10 when it comes out make it easier to install Ubuntu to an external drive, and for that matter, will it be able to happily live alongside windows if I choose to do a dual boot?

---

### Post by weatherman2 on 2015-01-29
How could it be easier to install Ubuntu on an external drive than it is now?  I've been doing that for years.  It seems very easy to me.

Difficulties with UEFI are due to the firmware/BIOS setup in the hardware (as originally designed for Windows 8) not directly due to the version of Windows you have installed.

---

### Post by ndiniz on 2015-01-29
OK, I have windows 8, and I'd love to do a dual boot with it, but I'm not sure how to go about doing it?

---

### Post by yancek on 2015-01-29
You can find a lot of sites with advice and instruction but the link below is to the Ubuntu site, start there:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2015-01-29
Did you install Windows or is it pre-installed, or really is it UEFI or BIOS booting?
You need to make external drive boot in the same mode either UEFI or BIOS. And make sure you have the grub2 boot loader installed to the external, so it can boot on its own and does not interfere with Windows boot loader on internal drive.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not highlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)

---

### Post by Mark Phelps on 2015-01-30
> **ndiniz said:**
> Will Updating to windows 10 when it comes out make it easier to install Ubuntu to an external drive...?

No.  MS has Windows To Go, which is the version that installs on an external drive -- but that is the Enterprise version, and is not available to consumers.  This is the same situation as currently with Windows 8.

---

