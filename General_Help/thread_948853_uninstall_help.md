---
title: "uninstall help?"
date: 2008-10-15
forum: General Help
---

### Post by jimi_hendrix on 2008-10-15
hello

so before ibex releases i want to try out some other distros since im reinstalling anyway when it does release

what can i do to whipe ubuntu off the partition safely (i assume sudo rm -rf / wont work...)

---

### Post by Elfy on 2008-10-15
Just install over the top of your install if that's what you want to do and use the installers to format.

---

### Post by jerome1232 on 2008-10-15
Do you have data in the ubuntu install you need to preserve? Can you back it up to an external disk?

If you don't have data that needs to be saved then just install an alternate distro and let it format the whole disk, nothing extra must be done.

'sudo rm -rf /' will just delete all files on your Ubuntu install and create an amusing borkage of your system. [COLOR="Red"](including your backup if it is mounted!)[/COLOR]

---

### Post by jimi_hendrix on 2008-10-15
no important data there...i have to do my school work on my vista partition because my printer doesnt like ubuntu

---

### Post by jimi_hendrix on 2008-10-15
and how would i tell which partition is ubuntu...i cant remember which one it is :D

---

### Post by jerome1232 on 2008-10-15
> **jimi_hendrix said:**
> and how would i tell which partition is ubuntu...i cant remember which one it is :D

from ubuntu type the following commands, and we can help you figure it out.

```
sudo fdisk -l
mount
```

---

### Post by jimi_hendrix on 2008-10-15
right now on vista for school...when i can i will post the output

---

### Post by jimi_hendrix on 2008-10-19
if i just install over ubuntu will it break grub?

---

### Post by linuxluver on 2008-10-19
yes but your new distro should install a bootloader

---

### Post by jimi_hendrix on 2008-10-19
ok its gentoo (ive heard good things about it and it is one of the few whose livecd has booted correctly)

---

### Post by linuxluver on 2008-10-19
well, ive never been able to install that on my machine, although I'll try it again today since im already totally reshuffling my HD anyway.
I dont know whether it installs a boot loader or not

---

### Post by jimi_hendrix on 2008-10-19
if it doesnt can i still boot into vista to fix it?

---

### Post by linuxluver on 2008-10-19
if it doesnt install a bootloader, then no.
i suggest copying personal files and folders from vista to cd and install gentoo. if it messes up, then you still have your school stuff from vista so you could wipe the HD. REMEMBER TO ALWAYS BACKUP PERSONAL STUFF BEFORE YOU DO ANYTHING TO A HARDDRIVE!!

---

### Post by jimi_hendrix on 2008-10-19
ok cool...last questions since ive never had to mount anything yet:

whats a mount point (it asks for them in the install) and what partition format thing does ubuntu use (windows uses something like nfts)

---

### Post by Elfy on 2008-10-19
a mount point is where a partition gets .. mounted, usually in /mnt although ubuntu uses /media default

so if you mounted sda1 in /mnt/tmp that is where it would be available

There is more than one choice to use for ubuntu - it defaults to ext3

---

### Post by linuxluver on 2008-10-20
yes a mount point is basically where you can access a hard drive.
Ubuntu(and all other Linux) can use either the ext2 format(slower,older) or the ext3 format(newer,faster)
Windows ME and earlier used the FAT16/32 formats
Win XP,2000,NT,Vista uses NTFS
Windows 7 will use WinFS

---

