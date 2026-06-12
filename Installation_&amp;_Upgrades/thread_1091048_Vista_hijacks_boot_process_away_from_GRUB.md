---
title: "Vista hijacks boot process away from GRUB"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by nullcore on 2009-03-09
I would prefer to use GRUB as my boot manager, but each time I boot into Vista, it changes the boot flags.  My HDD has 3 partitions, all primary partitions:

1 - Ubuntu
2 - Vista
3 - Storage

Partition 1 should be the boot partition, and loads GRUB properly.  From there I can successfully boot into either Ubuntu or Vista.  Upon booting into Vista however, I find that Windows has removed the boot flag from partition 1 and flags partition 2 as the boot partition.  Subsequent boots therefore go directly to Vista, requiring me to use either a Gparted or Ubuntu live CD to re-flag partition 2.

I've already re-installed GRUB via the following process in a command prompt as su:

```
grub
find /boot/grub/stage1
```
Which returns (hd0,0) as expected.
```
root(hd0,0)
setup (hd0,0)
quit
```

I don't think it's a GRUB problem.  GRUB is where it's supposed to be, and functions as expected.  Somehow, Vista just thinks it knows more about what I want my computer to do than I do, and steals the boot process away from GRUB every time it loads.

I can't change to boot partition from within Vista.  Tried that.  Changing it elsewhere seems to be useless as soon as Vista runs.  Any ideas?

---

### Post by nullcore on 2009-03-09
Ok, so I managed to add GRUB into Vista's boot manager and it works, but I'd still rather use GRUB from the get-go.

I just thought of this... I guess I could maybe set GRUB as Vista's bootloader's default, and set the timeout down to 0.  It would look like it was going straight to GRUB at least.  I'll try that next time I boot into Vista (in Ubuntu for the time being - home sweet home).

I'd still like to get Vista's bootloader completely out of the equation, if for no other reason than the principle of the matter.

I swear, if I didn't want Vista for directX 10 gaming, I'd be out in the street with everything Vista-related and a baseball bat, re-enacting that scene from *Office Space*.

---

### Post by meierfra. on 2009-03-09
Two ways to solve  your problem:

1)  Use 

```
sudo grub
root(hd0,0)
setup (hd0)
quit
```


This installs grub to the MBR rather than the boot sector of the Ubuntu partition. If Grub is installed in the MBR, the boot flag won't matter.

2)   Set the boot flag to the ubuntu partition. Also open "menu.lst" via "gksudo gedit /boot/grub/menu.lst" and remove the line "makeactive" from the Windows item. (It is the "makeactive" which sets the boot flag to the Windows partition each time you boot into Windows)

---

### Post by Mark Phelps on 2009-03-09
The problem (I know this will be a BIG surprise!!) is Vista -- it overwrites some of the GRUB info when you boot back into Vista on a dual-boot machine where both OS's share the same physical drive.

You have to reinstall  GRUB so that Vista can't corrupt it anymore.

The following link discusses this:  

[http://www.supergrubdisk.org/wiki/WindowsErasesGrub]("http://www.supergrubdisk.org/wiki/WindowsErasesGrub")

You'll need to download and burn the SuperGrubDisk (from the same site) and follow the directions in the link to repairing your system.

---

### Post by meierfra. on 2009-03-09
> The problem (I know this will be a BIG surprise!!) is Vista -- it overwrites some of the GRUB info when you

I would be very surprised if the problem described on the Super Grub page has anything to do with the current case: 

1) That problem  only happens in very rare case.
2) It cannot  be fixed by putting  the boot flag on the Ubuntu partition,
3) It only happens if Grub is installed in the MBR and the stage1.5 files are used. (but the OP has installed grub to the boot sector of the Ubuntu partition.)

The boot flag is definitely  changed by the "makeactive" command in "menu.lst". Indeed, that is the only purpose of "makeactive".

(But I have to admit,  following the direction from the Super Grub page will cure your problem, since it will install Grub to the MBR. But I don't recommend doing this, since it will install Grub without the stage1.5 files.)

---

### Post by adrian15 on 2009-03-13
> **meierfra. said:**
> I would be very surprised if the problem described on the Super Grub page has anything to do with the current case: 

1) That problem  only happens in very rare case.
2) It cannot  be fixed by putting  the boot flag on the Ubuntu partition,
3) It only happens if Grub is installed in the MBR and the stage1.5 files are used. (but the OP has installed grub to the boot sector of the Ubuntu partition.)

The boot flag is definitely  changed by the "makeactive" command in "menu.lst". Indeed, that is the only purpose of "makeactive".

(But I have to admit,  following the direction from the Super Grub page will cure your problem, since it will install Grub to the MBR. But I don't recommend doing this, since it will install Grub without the stage1.5 files.)

You are right meierfra. The main boot problem comes from nullcore. From the user as often happens ;). He is using the old method of activating a partition so that it is bootable from the standard MBR code.

As long as Windows needs its partition to be active so that it can boot... you will always loose the ability to boot the Ubuntu partition (Grub installed on Ubuntu partition's boot record).

I advice nullcore just to fix boot of linux: [http://www.supergrubdisk.org/wiki/Howto_Fix_Grub](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub) .

If Windows Vista boots and Grub menu disappears without any reason then he can read: [http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)

adrian15

---

