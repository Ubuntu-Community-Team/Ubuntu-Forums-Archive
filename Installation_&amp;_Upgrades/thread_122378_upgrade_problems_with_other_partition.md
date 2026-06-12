---
title: "upgrade problems with other partition"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by hyde200j on 2006-01-27
I recently upgraded Ubuntu from Hoary to Breezy and in the process have lost access to my Windows XP partition through the GRUB loader - the only way I accessed it prior to the problem. I have tried a few things but I'm a shameful newbie at this. First, in the GUI I checked System>Admin>Disks Manager which shows the NTFS system supposedly at /dev/hda2. The status is "inaccessable". So if I try mount /dev/hda2 in terminal, it can't find it in fstab or mtab files in /etc. I also tried editing /boot/menu.lst to include Windows in GRUB loader, but that did not work (likely because I don't know exactly what the modification to menu.lst should include.

In case you're curious how exactly I updated (as root):
first editted /etc/apt/sources.list
apt-get update
apt-get upgrade-dist
restart

I'm fairly certain I'm outta luck, but any advice would be helpful (even if I can only grab a select few more files from Windows beyond my barebones backup before I rebuild)

Thanks

---

### Post by hyde200j on 2006-01-27
Nevermind I got er figured.
A note to people like myself:
In menu.lst file:
In the format hd(x,y) x refers to harddrive and y refers to partition, not the other way around.
Also remember that these numbers start at zero (where they start at 1 in GUI).
Silly problems.

Any explanation as to why "mount /dev/hda2" doesn't work is still appreciated.

---

