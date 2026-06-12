---
title: "No partitions found during 7.10 installation (HPdv6000)"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by dpm_edinburgh on 2007-11-09
Hi all,
  I'm having a real nightmare trying to get any sort of usable distribution installed on my HP dv6000.
Finally, I managed to get Ubuntu 7.10 to actually start in graphical mode.  I clicked Install on the desktop, and made my way through the screens, until I come to screen four of seven, selecting the partitions for install.
  Basically, the list which should show my partitions on my hard drive is completely empty.  I know I have two NTFS partitions for Vista, and an unusable (i.e. no X, no text editors, no network drivers, GRUB overwritten my Windows boot loader etc.) installation of Gentoo on an ext3 partition (top tip- don't install Gentoo unless you know what you're doing!).
  I have exactly the same problem in the latest version of Fedora Core, too - no partitions found.  Bizarrely, openSuse installs fine (but I find suse much less usable than Ubuntu).
  Does anybody have any suggestions?  I've read through most of the threads on the dv6000, but none mention any problems detecting partitions.
  My specs are:

AMD Turion 64bit.
SATA hard drives.
NVIDIA Graphics.

Any help is greatly appreciated!

---

### Post by dpm_edinburgh on 2007-11-09
To be specific, I have a dv6525em laptop.  I also downloaded and ran the GParted LiveCD and booted with that.  It detected my partitions fine, and I deleted the old Linux partitions, created a new ext3 primary partition and a linux-swap.

Ubuntu still does not see any of my partitions.

---

### Post by dpm_edinburgh on 2007-11-12
Nobody?

---

### Post by dpm_edinburgh on 2007-11-14
One last time :(

---

### Post by .gurkburk on 2007-12-14
Well, im having the exact same problem.
Im running a completely different laptop though, dell XPS M1330.

I got 1 vista partition, and 3 linux partitions (boot/swap/root) and 2 from the manufacturer (1 small recovery partition and one for the media-direct function from dell).

Windows vista detects and shows all these partitions.
The old ubuntu (pre 7.10...) installation can show all these with fdisk -l (I havent gotten X to work in the old version... but terminals fine).
Installation of 7.10 displays the disc as empty, with installation-guide (both liveCD and alternative disc) aswell as going terminal and doing fdisk -l

Scary stuff.. no idea how to work it out :-p

---

### Post by JeremyStein on 2007-12-17
I had a similar situation -- no partitions listed.  I have an old HP Pavilion 310n whose restore partition I managed to destroy.  Maybe that's what caused the problem.

I was able to get it working by running gparted on an old Ubuntu 6.06 Live CD.  I wiped out everything, created a fresh partition and then gave 7.10 another chance.

---

### Post by Bartender on 2007-12-17
dpm -
This is just a hunch.  I'm thinking something didn't go right with GParted.

Try downloading GParted LiveCD again.  Maybe even try downloading an older version.  Burn at slow speed, 4X or so.  Wipe those partitions out again, then rebuild them and format as ext3.

When you use GParted, do you do one task at a time and apply it?  Or do you stack up several tasks and apply all at once?  They recommend one task at a time, apply, then move on.

---

