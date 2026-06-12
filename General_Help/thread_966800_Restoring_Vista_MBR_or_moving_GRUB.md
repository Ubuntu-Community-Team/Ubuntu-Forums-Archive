---
title: "Restoring Vista MBR or moving GRUB"
date: 2008-11-01
forum: General Help
---

### Post by Visti on 2008-11-01
Hi guys,
I have a slight problem with my laptop. It has Vista on it, as preinstalled. However, I just installed gOS on an 8gb USB disk, by just doing a normal install on it and as it was installing, I remember that it didn't ask me where to install GRUB, so it seems to be installed on the harddisk's MBR. 

Ah, well.. I guess. Not exactly what I wanted, but I start up the computer and get the GRUB menu where I can choose gOS and Vista, which is fine. (What I originally wanted was for the menu to only appear when the USB disk was inserted)

But when I remove the USB disk I get a grub error (22, which is deleted partition, I think). So is there a way I can restore Vista's boot loader (Didn't get a DVD, but I do have an Acer recovery partition, but it doesn't seem to fix the problem through auto-recovery, which is the only option).

Alternatively, perhaps editing GRUB, so that it just shows the menu regardless of the missing partition would also be just fine.

---

### Post by cdtech on 2008-11-01
Microsoft has a site for this:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Or you could use the "Super Grub" disk:

This would be for people who only have the OEM Vista installed on their computer.

Download the "Super Grub ISO" and creat a bootable CD. You can read about it here:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by ugm6hr on 2008-11-01
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

EasyBCD does this with a GUI and no CD.

---

### Post by TeXtonyx on 2008-11-01
Well, I think that the UBCD rescue disk can fixmbr and fixboot.
I don't see how Easybcd can do this when it's installed to the Vista
drive and it seems like you can't boot Vista. It works if you can.

It takes less effort to fix grub. Boot to the Ubuntu live cd and
open a terminal. Type
sudo grub
grub> find /boot/grub/stage1 

With the USB drive connected I think it will find stage1 on the
USB drive. But you want stage1 on the hard drive, so disconnect
the USB drive before you boot. Now run,
grub> find /boot/grub/stage1 
If you find stage1 on the hard drive, continue,
grub>root (hd0,0) (if that is the location "find" reports"
setup (hd0,0) (I think that will install grub to the MBR)
grub>quit

Now if you don't find grub's stage1 files on hd0=sda, then you
will reinstall grub so that the stage1 files are on hd0 not USB.
I think the Super Grub disk is a better way of doing this than 
the Ubuntu live cd.

---

### Post by ugm6hr on 2008-11-01
> **TeXtonyx said:**
> Well, I think that the UBCD rescue disk can fixmbr and fixboot.
I don't see how Easybcd can do this when it's installed to the Vista
drive and it seems like you can't boot Vista. It works if you can.
Vista should boot if the USB drive is plugged in (using Grub).
> 
It takes less effort to fix grub. Boot to the Ubuntu live cd and
open a terminal. Type
sudo grub
grub> find /boot/grub/stage1 

With the USB drive connected I think it will find stage1 on the
USB drive. But you want stage1 on the hard drive, so disconnect
the USB drive before you boot. Now run,
grub> find /boot/grub/stage1 
If you find stage1 on the hard drive, continue,
grub>root (hd0,0) (if that is the location "find" reports"
setup (hd0,0) (I think that will install grub to the MBR)
grub>quit

Now if you don't find grub's stage1 files on hd0=sda, then you
will reinstall grub so that the stage1 files are on hd0 not USB.
I think the Super Grub disk is a better way of doing this than 
the Ubuntu live cd.
I'm certainly no expert on Grub - but I believe you cannot install Grub to your HD without a Linux partition on the HD.

My personal suggestion:
EasyBCD to fix Vista's MBR on HD.
Install GRUB to MBR of USB. SuperGRUB will allow this.

Then - change boot priority in BIOS to:
1. USB
2. HD

---

### Post by TeXtonyx on 2008-11-01
Yes, ugm6hr, you are right.

---

