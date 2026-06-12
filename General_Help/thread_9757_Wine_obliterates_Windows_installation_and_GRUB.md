---
title: "Wine obliterates Windows installation and GRUB"
date: 2004-12-31
forum: General Help
---

### Post by Quest-Master on 2004-12-31
What a welcome I received back home from Chicago.

Before I left, I tried to Wine a few programs, neither worked, returned some errors about the registry being corrupted and such. I wasn't worried at the time; had a flight to catch, and didn't bother me at all.

I return home, and GRUB is apparently gone and my Windows has gone to hell. User accounts are all destroyed, hardware drivers are gone, none of the software is working anymore due to registry errors, and various needed DLLs have gone missing. 

At first, I believed it was the work of my not-so-technologically-advanced father who hated Linux, but I found he didn't touch it. I do some research on similar cases, and it hits me; Wine did it.

There is a disclaimer that Wine can corrupt your Windows installation; I pay no attention as I ask myself, how much do I hear about Wine doing evil?

Seems it had to be me. Luckily, my data is still intact, but just about everything else is broken. I suppose that's the end of Windows for me unless I reinstall.

I'm in Knoppix now, and gratefully, my Linux partitions are still existant. I need to find out how to get GRUB back to how it was before Wine's silent destruction so I can at least go back to Ubuntu.

---

### Post by YokoZar on 2004-12-31
I highly recommend you:

1) Don't install wine on top of a windows installation

and

2) Use my up to date wine packages available in the Ubuntu backports project or at the Winehq.org downloads page.

---

### Post by TravisNewman on 2004-12-31
yes, NEVER use your windows partition as the wine location. That's asking for trouble. Nothing will work when you try to run it with wine, and nothing will work in Windows when you try to go back into it

---

### Post by Quest-Master on 2004-12-31
Windows was working perfectly fine before this occurred though.

I don't really care about getting it working anymore, but more on restoring GRUB. That is my priority right now and I want it to be done before New Year's. ;d

---

### Post by Quest-Master on 2005-01-01
:(

Looks like GRUB is gone. /usr/share/grub no longer exists. Meaning, can't boot into Ubuntu for now. I don't want to do another reinstall of Ubuntu either. It'd be the fourth in less than a month. :x

I figured it was gone while trying to built a GRUB boot floppy.

---

### Post by Quest-Master on 2005-01-01
Looks like GRUB is still there. Everything is remaining in /boot/grub, menu.lst, all of that good stuff.

Now, just need to get it to boot instead of WinXP.

---

### Post by mr_ed on 2006-01-11
I had to do this as well, since installing Warcraft III on Wine 0.9.5 hosed my boot sector.  (I, however, didn't install Wine onto my Windoze partition.  ;))

With the Ubuntu Live CD (this may work with Knoppix, but I know for sure it works with the Ubuntu Live CD):

This also assumes that your Ubuntu (and hence your GRUB info) is on /dev/hda2

Boot it
Open up a Terminal
Type
```

sudo su
<enter your password>
chroot /dev/hda2 /bin/bash
grub-install /dev/hda

```

Now reboot without the CD.  You should be good to go!

---

