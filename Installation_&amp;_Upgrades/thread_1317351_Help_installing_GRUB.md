---
title: "Help installing GRUB"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Corgana on 2009-11-06
So I had a hard drive with WinXP and Win7 on it, and I used gparted and deleted the XP partition and expanded 7 (also added "boot" flag to it), and now I get the message "BootMGR is missing"

So I boot up my Ubuntu livecd, and try to install GRUB, but at the command

```
find /boot/grub/stage1
```

i get this

```
Error 15: File not found
```

Any help? Also I heard I could use ms-sys to fix it, but the latest version (that works with windows 7) isn't listed on synaptic..

Please help, I'm running off a LiveCD

---

### Post by darkod on 2009-11-06
I am no expert in Ubuntu, but if you are running off the live CD and you never had Ubuntu on the hdd, that should mean you never had GRUB/GRUB2 as a bootloader.

Isn't it normal that the find command is giving you file not found?

PS. And why are you trying to install just grub? Simply install Ubuntu if that's what you want and that will install grub too. Your Win7 bootloader should be detected by grub automatically and you will have it as option in the grub menu/list.

---

### Post by doran23 on 2009-11-06
do i need a OS on my hard drive to install ubuntu, using a disk. and how would i do that.

---

### Post by darkod on 2009-11-06
By using a disk I assume you mean a CD. No, you don't need to have any OS installed.

But if you plan to have both Windows and Ubuntu on your computer it is usually better Windows to be installed first.

It is also better to sit down first and plan the partitions on your hdd, depending on the hdd size. Ubuntu can choose this for you but you have more control if you do it yourself.

There are plenty of guides on goole. If you get stuck with a direct question, ask.

---

### Post by Corgana on 2009-11-06
> **darkod said:**
> I am no expert in Ubuntu, but if you are running off the live CD and you never had Ubuntu on the hdd, that should mean you never had GRUB/GRUB2 as a bootloader.

Isn't it normal that the find command is giving you file not found?

PS. And why are you trying to install just grub? Simply install Ubuntu if that's what you want and that will install grub too. Your Win7 bootloader should be detected by grub automatically and you will have it as option in the grub menu/list.

I deleted the Windows bootloader (accidentally, with the XP partition) and I don't have a windows disk to fix it. I figured I should just install grub because I plan on installing ubuntu when I get a new HD in the mail. Not to mention grub is a lot more versatile. I just can't find any tutorials on installing a bootloader on a HD that doesn't already have a bootloader on it.

---

### Post by darkod on 2009-11-07
1. If you want to have Ubuntu, just install it, that will install GRUB2 (by default I think), and with working Ubuntu and internet access you will easily find how to add the Win7 boot in GRUB2. I know the syntax just in GRUB, the ver2 is too new for me.

In grub it would be something like this in the menu.lst:
title Windows 7
rootnoverify (sd0,0) (depending on which partition the windows 7 boomgr file is, what was the C: drive)
makeactive (maybe not needed, try)
chainloader /bootmgr

2. If you want just GRUB without Ubuntu, I suggest you go for GRUB and not GRUB2. In that case there are plenty of rescue CDs images on internet which will allow you to boot from the CD and install grub. Sorry I don't have any links at hand.

If you are more familiar with windows you could try this:
- search on google and download grub4dos 0.4.4 (latest version)
- search and download grubinst zip package
- unzip grubinst and there will be program grubinst_gui.exe (if in vista right click and select run as administrator otherwise won't work)
- take a usb stick and plug it in (easier than cd)
- in grubinst_gui.exe under disk option select the usb stick (be careful not to select the hdd of the computer you are working on or you will delete it's MBR)
- in the files section click Refresh button and it will let you choose Whole Disk (MBR)
- check the Don't search for floppy box
- click on Install and it's done
- from the unzipped grub4dos package copy grldr and menu.lst on your usb stick

Now you have a working bootable usb stick with grub. If you leave menu.lst as it is it even gives you option to search for boot records on the hdd including Win7, Vista, WinXP etc. That should allow you to boot in your computer with the deleted loader.

All of the above is to create a bootable usb stick with grub on it. Burning an image of a rescue CD is a much better option. You can boot with it and read on internet how to install the grub on the hdd once you have booted with the rescue CD. The command is simple, something like grub-install or just install and the correct drive (using sd0 would make it install to the MBR of the first sata hdd I think. So it would be install (sd0) written from a grub comand line.

You should be able to get to a grub command line from the rescue cd.

PS. Grub rescue cd link:
[http://linux.wareseeker.com/System/super-grub-disk-gparted-system-rescue-001.zip/334862](http://linux.wareseeker.com/System/super-grub-disk-gparted-system-rescue-001.zip/334862)

Then just google for "How to install grub on my hdd". I haven't see this rescue cd myself, just the first link that appeared in google. After you boot from it check what options it gives. The description says it can locate lost boot files. Anyway you should be able to go to grub command line and do "install (sd0)". Not sure if you would need to copy menu.lst to your first partition or edit it (maybe grub install will make a copy of menu.lst itself and you just need to add your entries).
You have the entry for windows 7 for grub above.

---

