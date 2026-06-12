---
title: "Grub Rescue"
date: 2010-05-13
forum: Hardware
---

### Post by tigerglebe on 2010-05-13
Ok, got a system with two (currently) operating systems installed on it.  FreeDOS 1.0 Full is on hda3 while Ubuntu is on hda1.  I installed FreeDOS second (yes, I know it was a mistake) and now it gives me grub rescue prompt instead of an editable menu.  I would like to fix this but not sure how.

Suggestions please?

---

### Post by onandcorei on 2010-05-13
Insert live CD of Ubuntu(any distribution may be,but I think it's easy from Ubuntu Live :D)
Go to Terminal or any similar application to that.
Type grub.If it's not installed type:
**_sudo apt-get install grub_**
I think you have just one HDD.Your OSs are installed on this one.
Enter the commands below from grub prompt:
grub>root (hd0,0) or root (hd0,2)
grub>setup (hd0)
grub>quit
Then eject the disk and restart your computer.

---

### Post by tigerglebe on 2010-05-13
> **onandcorei said:**
> Insert live CD of Ubuntu(any distribution may be,but I think it's easy from Ubuntu Live :D)
Go to Terminal or any similar application to that.
Type grub.If it's not installed type:
**_sudo apt-get install grub_**
I think you have just one HDD.Your OSs are installed on this one.
Enter the commands below from grub prompt:
grub>root (hd0,0) or root (hd0,2)
grub>setup (hd0)
grub>quit
Then eject the disk and restart your computer.


Tried and rebooted.  It didn't save and dumped me back to the grub menu.  If I do the rootnoverify, chainloader I can boot into FreeDOS.  So I know at least one partition is fine which is a good sign for me.  I may try to reinstall to see if it fixes itself.

---

### Post by tigerglebe on 2010-05-13
> **tigerglebe said:**
> Tried and rebooted.  It didn't save and dumped me back to the grub menu.  If I do the rootnoverify, chainloader I can boot into FreeDOS.  So I know at least one partition is fine which is a good sign for me.  I may try to reinstall to see if it fixes itself.

Re-installed.  However, now it only shows the Linux menu option and not the DOS side.

Fixed it.  Once as I got into the system I went to /boot/grub and from the command line did a sudo leafpad menu.lst.  From there I edited it to include the lines:

title Freedos
rootnoverify    (hd0,2)
chainloader +1
makeactive

Saved it and rebooted.

---

