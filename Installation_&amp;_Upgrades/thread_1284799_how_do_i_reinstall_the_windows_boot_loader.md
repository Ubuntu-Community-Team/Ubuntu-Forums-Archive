---
title: "how do i reinstall the windows boot loader"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by jarrah-95 on 2009-10-07
i have recently had a problem that removed the windows bootloader in my system and i need to re install it but still keep grub2 to boot into ubuntu as that is what i still usualy use. 
is there any way to boot windows directaly from grub 2 or do i just have to continue to chain load into the windows bootloader

---

### Post by wilee-nilee on 2009-10-07
> **jarrah-95 said:**
> i have recently had a problem that removed the windows bootloader in my system and i need to re install it but still keep grub2 to boot into ubuntu as that is what i still usualy use. 
is there any way to boot windows directaly from grub 2 or do i just have to continue to chain load into the windows bootloader

So is this a dual boot or wubi, and you must have installed grub2 yourself.
If you run sudo grub-update in linux it should load windows into grub.
 
I don't know the answer to the windows boot-loader, but if you are dual booting with Linux as the second install; you want grub to be the boot-loader.

---

### Post by jarrah-95 on 2009-10-07
this i s a full install ( no wubi) and will updating allow me to boot straght into windows as the windows boot loader that it use to chainload into has an error

---

### Post by pmlxuser on 2009-10-07
simple answer , you can't keep both grub and windows MBR ... windows allow only windows to boot. so only grub is the option for you to be able to boot both windows and ubuntu.

so install windows then reinstall grub so that your system is configured to boot from both windos and ubuntu...

---

### Post by jarrah-95 on 2009-10-07
is there any way to reinstall the bootloader for windows this is what i need

---

### Post by Mark Phelps on 2009-10-07
> **jarrah-95 said:**
> ... is there any way to boot windows directaly from grub 2 or do i just have to continue to chain load into the windows bootloader

The GRUB loaders only hand off control to the windows boot loaders for MS Windows partitions, so if the MS Windows boot loader is hosed, you won't be able to boot no matter what you do with any version of GRUB.

I've read that the SuperGrubDisk is supposedly able to restore an MS Windows MBR -- but I've not actually tried it.

The actual way to restore a Vista boot loader is by booting from the Vista DVD and running startup repair a few times.  If you don't have a Vista DVD, go to the NeoSmart Technology forums.  They have a link where you can download an image to burn a repair CD.

---

### Post by Bartender on 2009-10-07
[Here's]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") the link Mark refers to.

Seems kind of silly to have to download a 120MB file in order to fix the tiny Windows MBR, but if this disc makes the process easy I guess it's worth it!!

EDIT:  I wonder if there's a similar download for XP?

---

### Post by naster4o on 2009-10-07
First i'm sorry for my bad english.
What windows you have? If you have windows xp you can use the recovery console. Can find it on windows xp install cd. Put the disk in the cd/dvd-rom, chose Recovery console /on the first screen is press R/
Now you have to type this two commands:
**fixmbr** and **fixboot** /you need and the administrator password to use the Recovery Console/
But after that you won't have a dual boot.
You can use only windows.

---

### Post by willy1946 on 2009-10-07
Naster4o is half right. If your MBR is currently occupied by the Grub boot manager and you wush to retain it for dual boot, then in the Windows Recovery Console just run **fixboot **and forget about **fixmbr**. This should fix your Windows boot loader but leave the Grub boot manager intact.

---

### Post by jarrah-95 on 2009-10-07
ok thanks for the ideas but i now have a wierd suituation after having vista and xp and having truble with vista i have a vista dvd and a xp install but i think that it runs of the vista bootloader first and then the xp one so when i get home ill try the visa disk and if that works than itl be right but if the xp ones still stuffed then how can i get it to work without a windows xp disk
thanks

---

### Post by Mark Phelps on 2009-10-08
The download image is NOT for just fixing the Windows MBR, it's for repairing Vista boot loader problems -- entirely different issue.

There is NO Windows Recovery Console in Vista -- so there's no point in recommending that folks use that.

If you installed Vista after XP, it most probably installed the Vista boot loader files to the XP partition.  After that, any attempt to boot into either brings up the Vista-built OS menu file.

When you boot from the Vista repair CD, it knows what partition to repair because it searches for the boot loader files and repairs those -- regardless of what partition they were installed to.

You may be able to use an XP disk to repair XP boot problems because it doesn't know about the new Vista boot loader files.  In that case, fixboot and fixmbr and Recovery Console, all should work for the XP partition.

---

### Post by jarrah-95 on 2009-10-08
i ahve just realised the real problem wasent the bootloader but the whole system. when i ran remastersys it removed the whole system so now i only have ubuntu witch in a way is good as this means that it has given me a reason to find linux apps for what i wanted to do i windows and may not even reinstall windows again. but in the off chaince i do is there any way to install windows from an immage as that is all i have of windows xp
thanks

---

