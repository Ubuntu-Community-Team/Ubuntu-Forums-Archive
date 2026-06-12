---
title: "Boot manager? Evil XP?"
date: 2008-10-08
forum: Hardware
---

### Post by w1nst0nsm1th on 2008-10-08
Not  sure if this is the correct forum but here follows my problem.
I'd been running ubuntu  and xp on my laptop for a couple of months (hp nx5000 1g ram) Had to reinstall xp cause of virus' and whatnot. Reinstalled successfully but now the partition running ubuntu (10gig) has completly vanished. I backed my data on the ubuntu partition on an external hd but viewing it from a microsoft OS says the backup folders are empty. Did the Xp instalation do something or is it hardware ? I don't want to reinstall the ubuntu os coz i'd lose my stuff.  Can anyone help?

---

### Post by damis648 on 2008-10-08
In Windows XP, go to Run and type
```
diskmgmt.msc
```
and look at the partitions for your main disk... is the Ubuntu partition still there? Or has XP just overwritten GRUB?

---

### Post by w1nst0nsm1th on 2008-10-08
Did that (thanks) the partirion is there marked '9.51 Healthy : unknown partition' along with a small 251mb partition which i assume is the 'swap'. What does that mean?

---

### Post by damis648 on 2008-10-08
That means that GRUB was overwritten. Just do the following:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Good Luck!

---

### Post by w1nst0nsm1th on 2008-10-08
Okay, When i boot it doesn't go into the grub options screen. So i figure I need to reinstall the Grub boot manager. Correct? If yes how do i do that?

---

### Post by damis648 on 2008-10-08
The link was in my previous post.

---

### Post by w1nst0nsm1th on 2008-10-08
Yeah that looks within my humble abilities. thanks

---

### Post by w1nst0nsm1th on 2008-10-14
After loading grub on the live cd and running Grub in terminal, this is what hasn't worked:

grub> find /boot/grub/stage1
 (hd0,6)
 (hd0,6)

grub> root (hd0,6)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... success
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,6)"... success
)
 Running "install /boot/grub/stage1 d (hd0) /boot/grub/stage2 p /boot/grub/menu
.lst "... failed

(Followed some other tutes that also didn't work)

Also found a 'grubconfig' program with a GUI on another linux live cd (puppy linux)
which lets you re-embed Grub. I clicked all the relevant boxes to but
it on 'MBR', it said 'success'. Rebooted and it goes ******' XP
again.. ahhh

Any Ideas? I mean don't i want it to boot off MBR (hd0) as opposed to
the OS's respective partition
(hd0,6)?

---

### Post by caljohnsmith on 2008-10-14
Please post:
```
sudo fdisk -lu
```
It sounds like you might have a problem with your HDD's partition table, but post the above first and we can work from there.

---

