---
title: "Dual Boot - Odd configunration"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by hodgemanU on 2006-01-09
I have an interesting dual boot question.

XP installed on 2 80Gb SATA's configured in RAID0
Ubuntu installed on 80Gb IDE drive hda.

My bios/MB doesn't have a feature to quickly change the boot device, so I have to go into the bios each time I want to change the OS.

Ubunty 5.10 x64 sees the SATA, but not as RAID, my question is:

Can I use something like chain0/chainloader to boot from the IDE?
Or can I add a line to my XP's boot.ini file to boot from the IDE drive?

I thought about just using a boot floppy, as that would be really easy, but if anyone knows of a more elegant solution, please let me know.

HM

PS - Sorry if this has been addressed already and THANKS IN ADVANCE :D

---

### Post by lha on 2006-01-09
Simplest solution I can think of is to copy boot sector from Ubuntu's bootable partition to a file on your Windows' partition and use NTLDR (Windows' bootloader) to load it. [Short instructions]("http://www.techspot.com/vb/all/windows/t-23581-Dual-Booting-Windows-and-Linux-2-different-drives.html") and [longer instructions]("http://hacks.oreilly.com/pub/h/2337") are available, and many others, too. There's also a program for Windows, [BootPart]("http://www.winimage.com/bootpart.htm"), that seems to be able to do this.

---

### Post by Sef on 2006-01-09
> My bios/MB doesn't have a feature to quickly change the boot device, so I have to go into the bios each time I want to change the OS.

Can't you save the changes you make to your boot order, so you don't have to change it every time?

---

### Post by hodgemanU on 2006-01-09
Thanks, I had tried that before, and didn't have any luck.
BUT..... reformated the drive and used it for something else, and forgot all about the above linked docs.

Thanks.

Sef:
It does save correctly, but if I want to switch, then I have to go into the bios.

or If I leave, and let the machine set to linux, the kids cannot play their games.

---

### Post by lha on 2006-01-09
[QUOTE=hodgemanU]Thanks, I had tried that before, and didn't have any luck.
BUT..... reformated the drive and used it for something else, and forgot all about the above linked docs.
[/QUOTE]

Those links tell you that you have to install grub to boot sector of a partition, not to mbr. Maybe your grub was on mbr and that's why it didn't work out. Ubuntu installs grub to mbr as a default.

As I have no further information on you raid configuration, I can only guess. Maybe you could use chainload to boot Windows. You could give it a try too. But just don't overwrite anything on your drives containing Windows...

---

### Post by hodgemanU on 2006-01-09
Thanks, It is installed to the MBR, how do I install it to a partition?
HM

---

### Post by lha on 2006-01-13
There's [a thread]("http://ubuntuforums.org/showthread.php?t=24113") on this you might want to read. Also, it's **a good idea to make backups** of files you can't afford to lose.

Reboot with Ubuntu live cd. (Some other Linux live cd may be good for this, too.) Open a terminal and type grub <enter>. You'll be greeted with
```

    GNU GRUB  version 0.95  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub>
```

Now grub wants to know where your /boot is. In single hd default installation it would be in hda1, so you would type
```
root (hd0,0)
``` but this is **NOT what YOU want**. Replace (hd0,0) with correct partition. If you don't know what it is, try following:
```
find /boot/grub/stage1
```
It shows you the partition you are interested in. It could be (hd2,0). If it is, type
```
root (hd2,0)
```
and
```
setup (hd2,0)
```.
Type
```
quit
``` to exit and then reboot and try BootPart again.

Now you have grub on a partition and on the mbr of your linux drive. When you change bios settings to boot from Linux drive, grub on mbr will be used and when you use ntldr to boot Linux, a copy of grub from boot sector of a partition will be used. They both use the same configuration files, so this is shouldn't cause any troubles.

---

