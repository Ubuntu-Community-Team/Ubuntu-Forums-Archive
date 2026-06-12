---
title: "Difficult to Describe, Plz HELP!!!!!!!!!!"
date: 2008-10-06
forum: Hardware
---

### Post by ddhazxiao on 2008-10-06
hi all,

now my problem is when i start up my laptop it says follow:

[COLOR="Red"]Windows Could Not Start Because of a Computer Disk Hardware Configuration Problem

Could not read from the selected boot disk. Check boot path and disk hardware.

Please check the Windows documentation about hardware disk configuration and your hardware reference manuals for additional information.
[/COLOR].......

this afternoon i wanted to install win xp into my external hard disk, (I now know it's impossible)=.= , after install CD copied all the files into the external hard disk, when it tried to reboot, (the legendary Blue Screen came out), and it kept on showing blue screen no matter how i tried, then i tried to boot from the main hard disk in my laptop, it was installed with Ubuntu 8.04 and Win Vista. however i can't enter into the Ubuntu generic boot menu. 

plz help me!!!! ... Thanks!!!!!!!!!!!!!!!

---

### Post by caljohnsmith on 2008-10-06
How about first posting:
```
sudo fdisk -lu
sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | strings | grep -i grub
sudo dd if=/dev/sdb bs=512 count=1 2>/dev/null | strings | grep -i grub
```
And we can work from there. :)

---

