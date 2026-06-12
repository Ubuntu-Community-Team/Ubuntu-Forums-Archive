---
title: "686 kernel panic after upgrade"
date: 2005-11-23
forum: General Help
---

### Post by olavi on 2005-11-23
Today Update manager asked me to upgrade the kernel. So I did. After installing, it asked me to reboot. So I did, and got "kernel panic: can't find root filesystem" or something like that.

Well, at least the 386 version seems to work fine.

Is this a common problem? I'm using an IDE disk with ReiserFS filesystem as root.

---

### Post by ebrowne on 2005-11-23
If I'm reading your post properly you can still use your previous kernel version.  Please check the entry in GRUB perhaps it's looking for root in the wrong place.  This happen on my system when I do a kernel update bacuse I boot off a SATA drive that't not the first device in the BIOS so I have to edit the menu.list in /boot/grub to account for that.

Hope this helps

---

### Post by olavi on 2005-11-23
[QUOTE=ebrowne]If I'm reading your post properly you can still use your previous kernel version.[/QUOTE]

Not only the previous kernel version, but also the new 386 kernel.

i686 2.6.12-10 does not work
i386 2.6.12-10 works
i686 2.6.12-9 works

I can't try the solution yet, but I'll post some info tomorrow.

I guess I should report a bug, as this is something that shouldn't happen.

---

### Post by olavi on 2005-11-24
Damn! My /boot partition is full! Zero bytes free.

I didn't know Ubuntu saves the previous kernels, so I thought 32 MB is fine like it was with Gentoo, where you manually upgraded the kernel.

Now I'm in real trouble. Any suggestions? If I remove the boot partition and use the root partition instead, Ubuntu probably can't find it any more. :(

---

### Post by Xian on 2005-11-24
[QUOTE=olavi]If I remove the boot partition and use the root partition instead, Ubuntu probably can't find it any more. :([/QUOTE]
It will if you edit your fstab file and remove the line for /boot.
Don't forget to move the contents of that partition over to /.

---

### Post by olavi on 2005-11-24
[QUOTE=Xian]It will if you edit your fstab file and remove the line for /boot.
Don't forget to move the contents of that partition over to /.[/QUOTE]

I wonder... what about Grub and future upgrades to menu.lst? There's the (hd 0,5) items I think I'll have to change.

I might be able to live with only 32 MB /boot. Does Ubuntu save all the kernels or just the last two versions? Latter would work fine for me. I'm not going to delete the old kernels manually on each kernel update, though.

---

### Post by Burning Bronx on 2005-11-24
It doesn't delete old kernels at all. You can still remove them manually or via Synaptic.

---

### Post by Sebby on 2005-11-24
Once I've ensured that a new kernel is working alright, I remove the old one(s) using Synaptic.

---

