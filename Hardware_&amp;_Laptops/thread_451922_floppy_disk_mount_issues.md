---
title: "floppy disk mount issues"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by voided3 on 2007-05-22
Hello, I just installed a floppy drive in my computer so I can make boot loaders for my other older comps. When I switch between disks, I get mounting issues sometimes; for example, I insert a disk, then right click on the disk on the desktop (I use Xubuntu Feisty BTW) and mount it. This works fine. Then I go to unmount it the same way, and it does it but gives me an error saying that it "cannot unmount 'floppy disk'". Then, when I insert the next disk and mount it, it works again, but the unmount is exactly the same as before however now it still thinks it is mounted. When I go to put in a third disk, it simply won't mount at all. I have used Xubuntu for over half a year now, but this is the first time I have used a floppy drive with it, so is there something that I am doing wrong? Thanks!

P.S.- the drive is completely functional and runs fine in Windows as well

---

### Post by voided3 on 2007-05-22
P.P.S.- I don't know if it's supposed to be this way, but there also is not an entry for fd0 in my fstab file or my /media folder, yet there is a folly icon on my desktop. Any ideas?

---

### Post by voided3 on 2007-05-22
Well, I added this to my fstab: 

> /dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

...and added a "floppy0" folder in the /media folder using a root window, then restarted, but I still get errors mounting a disk, except they now mention an unspecified filesystem type. Any suggestions?

---

### Post by voided3 on 2007-05-22
Alright, I also tried "mount /dev/fd0" and this is the output:
```

mount: /dev/fd0: can't read superblock

```

Sounds mroe like a hardware problem now, but once again I have no issues in Windows with the drive or this particular diskette. This just keeps getting weirder...

---

### Post by Yatti on 2007-05-26
Im also dealing with this problem... I can't mount\unmount from thunar for some reason... When I try from terminal it gives the same superblock error..

---

