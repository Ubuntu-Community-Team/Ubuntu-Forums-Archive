---
title: "OOps with Menu.lst"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by IanB2 on 2009-02-17
Help ..... I've messed up my Mum-in-Law's laptop recent upgrade to the latest Kernel ..... when the upgrade was installing, I clicked 'keep the existing menu.lst' by mistake.

I'd like to insert the missing lines from the menu.lst so I'm able to run the latest kernel, as we're having some hardware issues with a webcam, which the new kernel may help with.

Its the 8.04 installation. Any help would be much appreciated.

---

### Post by taurus on 2009-02-17
Look to see the exact name/number of the new kernel in /boot

Applications -> Accessories -> Terminal
```
ls -la /boot
```
and edit /boot/grub/menu from a terminal.

```
gksudo gedit /boot/grub/menu.lst
```
Copy the entry for the old kernel and paste it above it.  Now, replace the old kernel with the newer one.  Save it and reboot.

---

### Post by IanB2 on 2009-02-18
Brilliant and many thanks .... worked a treat!

---

### Post by Pablo Pablovski on 2009-02-18
I did this exact same thing (didn't update menu.lst when updating the installed kernels), and haven't been able to get the system to boot with 2.6.27.12 since (it's fine with .....11). 

If I edit menu.lst as suggested, the system boots in low graphics mode. From there, letting the system re-configure itself doesn't seem to do anything - just a blank screen - and I'm forced to restore the "old" version of menu.lst and reboot (which I do remotely, from my iPod Touch - cool!).

I suspect I need to compile a kernel module for my graphics card - I have an nvidia 8800GTS running the 190.29 Beta driver - but I don't really know how to do that or, indeed, if that's actually what the problem is. 

Any helpful suggestions / directions?

TIA
PP

---

