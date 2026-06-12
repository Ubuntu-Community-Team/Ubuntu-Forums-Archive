---
title: "Dual-Boot Killed windows, don't care, just need files"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by 98xjdmb on 2009-03-16
Ok, so here's the story. I installed ubuntu onto my dell which is many years old and isn't worth all the work i spend on it. When i installed i simply installed to dual-boot so that ubuntu is on my second (120Gb) drive and windows can stay on its own drive. When i boot up everything works great, but if i try to boot into xp all i get is a beautiful BSOD. Also, Ubuntu recognizes the drive that windows is on as a "Media Drive" but can't mount it. Just now as an experiment i booted up into Ubuntu and then physically removed the drive that windows is on and all is fine. I could honestly care less if windows works, but I need to find a way to forcibly get on that drive and get important documents, music, and photos. Short of repairing windows with the disk (which i can't find) and then dealing with reloading the grub, what are some ways i can get that drive mounted?

---

### Post by Mark Phelps on 2009-03-16
There are various ways, but one way I've used is the following:
1) Get an adapater that allows you to connect the drive to your PC using a USB port
2) Plugin the drive using the adaptor
3) It most likely will result in a drive icon suddenly appearing on your desktop
4) Double-click the icon to open a Nautilus window to the drive and proceed from there.

If you don't get the icon, open a terminal window and enter "sudo fdisk -lu" (that's a lower-case L, not a one).  If Ubuntu sees the drive, it will be listed -- probably something like /dev/sdb.

Presuming the partition you want is sdba (first partition on that drive), do the following in a terminal:
1) sudo mkdir /media/windows
2) sudo mount /dev/sdba /media/windows -t ntfs-3g

You should NOW see a drive icon on your desktop; proceed from there.

---

### Post by 98xjdmb on 2009-03-16
> **Mark Phelps said:**
> There are various ways, but one way I've used is the following:
1) Get an adapater that allows you to connect the drive to your PC using a USB port
2) Plugin the drive using the adaptor
3) It most likely will result in a drive icon suddenly appearing on your desktop
4) Double-click the icon to open a Nautilus window to the drive and proceed from there.

If you don't get the icon, open a terminal window and enter "sudo fdisk -lu" (that's a lower-case L, not a one).  If Ubuntu sees the drive, it will be listed -- probably something like /dev/sdb.

Presuming the partition you want is sdba (first partition on that drive), do the following in a terminal:
1) sudo mkdir /media/windows
2) sudo mount /dev/sdba /media/windows -t ntfs-3g

You should NOW see a drive icon on your desktop; proceed from there.

So using the usb adapter should be different than just having it plugged in normally?

---

### Post by Mark Phelps on 2009-03-17
Yes ... it's reading the drive through a USB interface, instead of through an IDE or SATA interface hooked into the main bus.

This results in a LOT slower transfer, but since you're only interested in copying files in a one-time operation, that shouldn't be much of a problem.

---

### Post by markosjal on 2009-03-17
If the Windows drive is NTFS, you MUST install NTFS support in Ubuntu, regardless of whether it is USB or IDE. . I am reading and writing my Windows NTFS disk with no issues.

Just search for NTFS in Synaptic package manager , before wasting time with the USB interface. It should not matter if the drive is USB or IDE or SATA if the NTFS support is what you lack, and the drive is physically connected in one form or another

---

### Post by upchucky on 2009-03-17
careful,

you said win boots and get a BSOD, there is a problem in all versions of linux reading a messed up NTFS filesystem. the messed up ntfs needs to be repaired first before ubuntu can read/write it properly.

the libntfs-based ntf-sprogs package has a tool called ntfsfix which does not actually fix inconsistencies, but does clean the filesystem journal. this lets the ntfs partition be mounted again in read/write without needing any windows tools to fix it.

---

### Post by Mark Phelps on 2009-03-18
Ubuntu 8.10 has NTFS support built-in because it comes with the ntfs-3g package.  

To see if it's installed in your system, open a terminal and type "ntfs-3g --help".

You can also install the ntfsprogs package to get additional NTFS capabilities.

Both packages are availabe in synaptic.

---

### Post by 98xjdmb on 2009-03-23
Well, i basically trashed everything, reinstalled XP, a new bios, and made everything like it came from dell. Then reinstalled what i need. Should have done it to begin with. Thanks for the help all

---

