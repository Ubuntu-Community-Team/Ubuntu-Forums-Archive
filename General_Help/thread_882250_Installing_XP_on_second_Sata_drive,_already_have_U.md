---
title: "Installing XP on second Sata drive, already have Ubuntu on first sata drive"
date: 2008-08-06
forum: General Help
---

### Post by kgk on 2008-08-06
I have two SATA drives installed in my computer.  The first has Ubuntu running and the second has nothing.

I boot from CD to try and install XP onto the second drive, and it gives me the "This disk does not contain a Windows XP-comptaible partition [MBR]" garbage.

So I go back a screen, delete partition, create partition, but it gives me the same message.

So I boot into Ubuntu, open up Gparted, and delete the partition on that second drive, apply.  Then format it as NTFS and apply.  Try again and it gives me the same error.

I've formatted it as NTFS and it's still not working, what the hell?

:confused::confused::confused:

I don't want to have to "install XP on the primary", create a small partition for the GRUB bootloader and then reinstall Ubuntu on the second drive.  The first boot drive has Ubuntu, so it already runs GRUB before booting.  I want to install XP onto the second drive.  And for some reason, even after formatting the second drive as NTFS using GParted, it still gives me that garbage error.

---

### Post by logos34 on 2008-08-06
You created a **primary **partition and formatted as NTFS?  Windows won't install on a logical partition. 

Another problem might be that windows is complaining because the drive is second in the Bios boot order.  Switch it so the target disk is the Bios boot drive--windows won't install otherwise, in my experience. You can always change it back afterward.  Manually add a [windows entry to grub like this.]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")

---

### Post by Victormd on 2008-08-06
Another alternative is to remove (physically disconnect) all your drives and leave only the drive you want windows on. You're going to have to install Grub again anyway. Install windows (use the windows installer to format). You can then re-connect the HDs, and install grub.

---

### Post by rbmorse on 2008-08-06
I strongly encourage you to follow Victormd's advice to remove all drives from the system except the one to which you wish to install Windows.

---

### Post by riggity_ryan on 2008-08-06
> **logos34 said:**
> Manually add a [windows entry to grub like this.]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")

Thanks for the link.  I just reinstalled windows on the second hard drive of my PC and Grub wouldn't load it.  I couldn't figure out why because Ubuntu could mount my second hard drive and I could boot into Windows if I set my BIOS to boot from the second hard drive.  Turned out these lines of code disappeared from my Windows boot when I updated Grub after installing windows:

```
map        (hd0) (hd1)
map        (hd1) (hd0)
```

---

### Post by logos34 on 2008-08-07
but you can boot windows from grub when you add those lines back, right?

---

### Post by Victormd on 2008-08-07
> **riggity_ryan said:**
> Thanks for the link.  I just reinstalled windows on the second hard drive of my PC and Grub wouldn't load it.  I couldn't figure out why because Ubuntu could mount my second hard drive and I could boot into Windows if I set my BIOS to boot from the second hard drive.  Turned out these lines of code disappeared from my Windows boot when I updated Grub after installing windows:

```
map        (hd0) (hd1)
map        (hd1) (hd0)
```

Those lines were probably never there to begin with. You only need them if the windows installation is on a different drive. If windows is on the same drive, different partition, then you don't need to add the map option. Let us know if that worked...

---

### Post by logos34 on 2008-08-07
> **Victormd said:**
> Those lines were probably never there to begin with. You only need them if the windows installation is on a different drive. If windows is on the same drive, different partition, then you don't need to add the map option. 

Kgk's windows installation is on a separate drive (please read post #1), so the map lines will be necessary in order to chainload XP on the other disk

---

### Post by Shazaam on 2008-08-07
kgk...
Just for reference this is part of my menu.lst (edited for size, 3 hard drives)
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e06f1698-28a5-4a45-b21d-c533ec1935fd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda9 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
#root		(hd0,8)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda9 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-generic
quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,8)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda9 ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		PuppyLinux (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz root=/dev/sda6 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		MEPIS at sda7, kernel 2.6.22-1-mepis-smp (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-1-mepis-smp root=/dev/sda7 nomce quiet splash vga=791 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-15-generic root=/dev/sda8 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-15-generic root=/dev/sda8 ro single 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


title openSUSE 11.0
    root (hd2,0)
    kernel /boot/vmlinuz-2.6.25.11-0.1-default root=/dev/disk/by-id/scsi-SATA_WDC_WD1600BB-22WD-WMAL91327844-part1 resume=/dev/sdc5 splash=silent showopts vga=0x31a
    initrd /boot/initrd-2.6.25.11-0.1-default

title Failsafe -- openSUSE 11.0
    root (hd2,0)
    kernel /boot/vmlinuz-2.6.25.11-0.1-default root=/dev/disk/by-id/scsi-SATA_WDC_WD1600BB-22WD-WMAL91327844-part1 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.25.11-0.1-default


title Mandriva
root (hd2,4)
kernel /boot/vmlinuz BOOT_IMAGE=linux root=UUID=829db9a2-9d91-4350-8a18-89eb18d90dbf  splash=silent vga=788
initrd /boot/initrd.img

title Mandriva-nonfb
root (hd2,4)
kernel /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=829db9a2-9d91-4350-8a18-89eb18d90dbf 
initrd /boot/initrd.img

title Mandriva-failsafe
root (hd2,4)
kernel /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=829db9a2-9d91-4350-8a18-89eb18d90dbf  failsafe
initrd /boot/initrd.img



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```
Yeh, the SuSe and Mandriva entries are ugly but they were basically a copy/paste from their respective menu.lst files with a little editing added. :)

---

### Post by riggity_ryan on 2008-08-07
> **Victormd said:**
> Those lines were probably never there to begin with. You only need them if the windows installation is on a different drive. If windows is on the same drive, different partition, then you don't need to add the map option. Let us know if that worked...

Actually the crazy part is they were there before.  Before I reinstalled Windows I had a working dual boot with Windows and Ubuntu.  I'm not quite sure why those lines disappeared.

kgk: It sounds like you're trying to do what I just did last night with my PC.  I had Ubuntu and Windows dual booting on two different drives, but needed to reinstall Windows while keeping Ubuntu untouched.  This is how I went about it:

Prep work:
The first step is to make sure your BIOS is set to auto detect both hard drives at boot time.  How to do this varies from PC to PC.  I have two IDE hard drives on the primary cable and had to set my Primary Slave to "Auto-Detect."  Sometimes auto detect on the slave is turned off for a quicker boot time.

Installing Windows:
Windows wants to be the primary drive so it can use it's boot loader, so for now let it: Have only the hard drive you want to install Windows on hooked up and set it to Master/Single.
Windows needs to be the primary drive in order to use its boot loader.  That's why it was complaining about not having a Windows compatible partition on the primary drive.  Linux can boot as primary or secondary.

Getting grub back:
Now that Windows is installed you need to put your computer back to how you want it.  Probably with your Linux hard drive as the Primary w/ Slave and the Windows hard drive as Slave.

Next you need an Ubuntu Live CD to boot back into your PC.  Follow catlett's instruction to reinstall grub into the mbr, they're pretty straight forward: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

When you run "find /boot/grub/stage1" make sure this hard drive matches the one your /boot/grub/menu.lst says is your Linux hard drive.  I only mention this because mine used to be (hd1) but switched to (hd0) after reinstalling Windows.  If this happens you need to update your menu.lst to reflect the change.

I'm not sure if this helped, but because I changed my menu.lst I also ran this in the terminal just to be on the safe side:
```

> sudo -i
> mount -t ext3 /dev/sda1 /media/disk
> mount -t proc none /media/disk/proc
> mount -o bind /dev /media/disk/dev
> chroot /media/disk /bin/bash
> update-grub
> exit
> umount /media/disk/dev
> umount /media/disk/proc
> umount /media/disk

```
Where /dev/sda1 is my Linux partition.


After all that you should be able to reboot and be able to boot into both Ubuntu and Windows.

After this if you're PC says it can't find your hard drive, go into your BIOS and make sure your boot sequence boots your Linux hard drive before your Windows hard drive.


When possible, it's always best to first install Windows then install Ubuntu.  This saves you all the trouble above because grub will be the last boot loader installed.

---

### Post by Victormd on 2008-08-08
> **logos34 said:**
> Kgk's windows installation is on a separate drive (please read post #1), so the map lines will be necessary in order to chainload XP on the other disk

I know, that's what I said. I was just pointing out that they didn't exist to begin with, they didn't disapear. Then I say that yes, he will need them... I just tried to give a brief explanation as to why they weren't there initially...

Sorry for the mix-up.

---

