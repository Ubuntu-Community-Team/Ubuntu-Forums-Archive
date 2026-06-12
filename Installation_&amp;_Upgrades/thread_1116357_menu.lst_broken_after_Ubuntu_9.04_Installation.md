---
title: "menu.lst broken after Ubuntu 9.04 Installation"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by OniLink10 on 2009-04-04
Today I upgraded from Ubuntu 8.10 to the Beta of Ubuntu 9.04. Problem is, now menu.lst is messed up, and now I get Error 17: Unable to Mount Partition when I try to boot. I went into the GRUB Setup and saw this:
root ()/ubuntu/disks
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=1db4b521-4762-43cf-81ab-c9eb037e087a ro ROOTFLAGS=syncio single
initrd /boot/initrd.img-2.6.28-11-generic

I knew that root ()/ubuntu/disks should be root (hd0,1) from previous problems, but even after changing it to that, I still get Error 17. I went into the GRUB Command-Line and tried this:
root (hd0,1)
setup (hd0)

I saw this on Google, and tried it, but it gave me Error 17. Anyone have any advice? I don't want to lose everything. I have a Windows XP Installation lost in there, along with lots of C++ Code, .SO Files, Sprites, and Music for my Game in there! D:

---

### Post by ronparent on 2009-04-04
Assumming the file system is still intact, try this from a live cd terminal:

sudo grub
grub> find /boot/gtub/stage2

the output from this command will find root; enter that root in

grub> root (hd?,?)
setup (hd0)

If Stage2 is not found then we will have to find out if the file structure is intact and if grub is installed?

---

### Post by OniLink10 on 2009-04-04
> **ronparent said:**
> Assumming the file system is still intact, try this from a live cd terminal:

sudo grub
grub> find /boot/gtub/stage2

the output from this command will find root; enter that root in

grub> root (hd?,?)
setup (hd0)

If Stage2 is not found then we will have to find out if the file structure is intact and if grub is installed?

Thank you. For some odd reason, Ubuntu was moved to hd0,2, when I remember installing it on hd0,1. Maybe it has to do with the Swamp Partition I created? Ah well, thanks!

---

