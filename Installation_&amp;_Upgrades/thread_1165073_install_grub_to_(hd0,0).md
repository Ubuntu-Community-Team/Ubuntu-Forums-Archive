---
title: "install grub to (hd0,0)"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by gamez on 2009-05-20
Hello,
during the installation of versions before jaunty, I was able to indicate "(hd0,0)" in a textfield as the target partition for grub; today, this is replaced by a drop-down menu which gives me troubles.

1) Possible choices which reflect the 1st partition (and not the drive's MBR) are "/dev/sda1" and "/dev/sda-1"; what is the difference, why do they appear more than once in the list, and what do they mean?

2) When going into the advanced settings and back out again, the choice made in (1) is always reverted to "/dev/sda". Is this a known bug? How can I be sure that the choice is kept?

Since I want to be 100% sure that grub is placed in the 1st partition and not the MBR, I kindly ask for your advise.

Thank you, g.

---

### Post by Brandon Williams on 2009-05-20
I can't answer your questions about doing this within the gui, but I might be able to propose a workaround.

Is it possible to tell the installer not to install grub at all? And is it possible to get to a shell prompt? I know the answers to both of these are "yes" for the alternate installer, which is what I tend to use, but I don't know whether it's true for the graphical installer. I suspect that it is.

A possible workaround is to tell the installer not to install grub at all, get yourself to a shell prompt, and then run grub.
```
$ grub
grub> root (hd0,0)
grub> setup (hd0,0)
```

---

### Post by gamez on 2009-05-22
After some tries I figured out that I had to chose the same partition I indicated in an earlier step of the setup as the one to be mounted as root; in my case it was /dev/sda1.

g.

---

