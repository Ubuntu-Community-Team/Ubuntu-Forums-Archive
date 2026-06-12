---
title: "fujitsu-siemens problem"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by madnoob on 2009-06-16
Hi, everyone!
I just installed Jaunty on my FS V5535 laptop and it installs ok, but when i choose ubuntu form grub list (any choice, recovery mode and even memtest) the computer restarts. I installed ubuntu second, as i also have vista installed. What can i do to make Jaunty work cause i heard many good things about it, and i used previous versions of ubuntu before and was very satisfied with them. Thanks!):P

---

### Post by dstew on 2009-06-16
Instead of pressing 'enter' at the boot menu, press 'e' for edit. This will show what commands are being executed by grub for that particular menu item.  Usually there are root, kernel, initrd and boot commands. Post to the forum the commands, maybe we can figure out what the problem is without getting too involved.

---

### Post by madnoob on 2009-06-16
Thanks for the fast response!
Here is what i got from pressing e:

for ubuntu 9.04 :

uuid  30a3a952-3f45-464e-8491-ad11c76776d5
kernel  /boot/vmlinuz-2.6.28-11-generic root=UUID=30a3a952-3f45-474e-->
initrd  /boot/initrd.img-2.6.28-11-generic
quiet

for ubuntu 9.04 (recovery mode):

uuid  30a3a952-3f45-464e-8491-ad11c76776d5
kernel  /boot/vmlinuz-2.6.28-11-generic root=UUID=30a3a952-3f45-474e-->
initrd  /boot/initrd.img-2.6.28-11-generic

for memtest:

uuid  30a3a952-3f45-464e-8491-ad11c76776d5
kernel  /boot/memtest86+.bin
quiet

---

### Post by dstew on 2009-06-16
That seems OK to me. Do you have a Windows menu item that works?

---

### Post by madnoob on 2009-06-17
Yes, i have Vista and it loads ok. Is there any way of "refreshing" the boot file using the live CD in Ubuntu? .I  remember using the live CD to restore Ubuntu after installing windows, but not for 9.04. 
 If it helps, i can write here the step by step "procedure" of the installation. Maybe i messed something up, altough it's not my first time installing ubuntu. Thanks!

---

### Post by dstew on 2009-06-17
> Is there any way of "refreshing" the boot file using the live CD in Ubuntu?Yes, you use the Live CD to re-install grub. It is worth a try. See [this thread]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by madnoob on 2009-06-21
Hi again!
I tried reinstalling Grub with the live CD, but it didn't solve the problem. I downloaded a "fresh" iso from ubuntu.com and installed again. It's the same: when i select ubuntu from the Grub list , the computer restarts. Vista still works. When installing, i chose ext3 journaling as the file system for a 20GB partition and "/" as mount point.The partition type is "logical", not "primary" (ok?) . I also made a 2GB swap partition (i have 2 GB RAM installed). I'm out of clues right now, but still wiling to make this work. 8-[. Thanks!

---

### Post by madnoob on 2009-06-21
Problem solved!! It was a bios issue. I updated my bios from the fujitsu-siemens site and now Jaunty loads just fine.:guitar:. I was really curious how fast Jaunty boots up and it IS QUITE FAST :). I discovered the solution after finding the same problem on internet with another fujitsu laptop and followed the "recipe". Now comes another thing : the nasty SIS 3d driver. Hopefully it won't make me give up Ubuntu. Thanks!

---

