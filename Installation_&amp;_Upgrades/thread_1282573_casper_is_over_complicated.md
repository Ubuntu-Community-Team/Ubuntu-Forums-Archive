---
title: "casper is over complicated"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by sfxpt on 2009-10-04
Hi, 

I tried to do a frugal installation of Ubuntu (ie, install root fs as-is without
expanding) but failed. This is what I've been doing:

copy the /casper from cdrom onto usb pen, 

then add a boot entry as following into grub:

```
title Try Ubuntu without any change to your computer
    kernel /casper/vmlinuz boot=casper 
    initrd /casper/initrd.gz

```This approach has always been working with all other Linux distros that I used, Debian-live, Grml, Slax family, puppy Linux, etc. Why casper make it so complicated?

This is ubuntu 9.04. The symptom is that, vmlinuz and initrd.gz were found as expected, but casper fails when trying to mount sqausfs root:

[IMG]http://ubuntuforums.org//img246.imageshack.us/img246/7649/screenshotcasper904nok.png[/IMG]
[IMG]http://ubuntuforums.org//img246.imageshack.us/img246/7649/screenshotcasper904nok.png[/IMG]

---

### Post by sfxpt on 2009-10-04
Why my screen shot is lost, two times?

[IMG]http://img246.imageshack.us/img246/7649/screenshotcasper904nok.png[/IMG]

trying the 3rd time. . .

---

### Post by sfxpt on 2009-10-04
FYI, Here are my "homeworks"

I've found this, but it seems not for ubuntu 9.04. I tried apply the same
method with ubuntu 9.04 but wasn't successful.

How to Install Ubuntu Linux on a USB Flash Drive
[http://www.ixibo.com/2009/04/how-to-install-ubuntu-linux-on-a-usb-flash-](http://www.ixibo.com/2009/04/how-to-install-ubuntu-linux-on-a-usb-flash-)
drive/

I know there are easy ways to install Ubuntu Linux on USB drive. EG,

Easy Way To Install Ubuntu Linux On USB Drive
[http://www.technixupdate.com/easy-way-to-install-ubuntu-linux-on-usb-](http://www.technixupdate.com/easy-way-to-install-ubuntu-linux-on-usb-)
drive/

Install Ubuntu 9.04 to a USB pen drive
[http://www.talkonsomething.com/2009/08/install-ubuntu-9-04-to-a-usb-pen-](http://www.talkonsomething.com/2009/08/install-ubuntu-9-04-to-a-usb-pen-)
drive/

but my USB is already well partitioned, and I want to install Ubuntu into
a partition without interfering the files on the partition and other
partitions.

Thanks

---

### Post by sfxpt on 2009-10-04
> **sfxpt said:**
> 
I know there are easy ways to install Ubuntu Linux on USB drive. . .
but my USB is already well partitioned, and I want to install Ubuntu into
a partition without interfering the files on the partition and other
partitions.


A good example to back it up:

> when I tried to boot from my hard-disk I found that Ubuntu had replaced my hard-disk's bootloader with the one one my SD card. This raises a few problems like

[LIST]
[*]My hard-disk can no longer boot without the SD card.
[*]My SD card could only boot on my computer.
[/LIST]

[http://ubuntuforums.org/showthread.php?t=1281808](http://ubuntuforums.org/showthread.php?t=1281808)

---

### Post by sfxpt on 2009-10-04
please help.

---

### Post by bobbob1016 on 2009-10-04
1st, 2 hours between starting the thread and bumping (reposting on the same thread without adding new info, "please help" isn't new info) is bad ettiquite.

2nd, your title is *very* vague.

3rd, you haven't clearly stated what you are trying to do.  I had to read it 3 times before I figured you are trying to either install from, or install on a USB stick, and boot from it.

4th, I googled "ubuntu usb install" [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick), unetbootin will install to your USB drive no problem.

---

