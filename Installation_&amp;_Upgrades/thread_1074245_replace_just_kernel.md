---
title: "replace just kernel?"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by TimDaniels on 2009-02-19
I impulsively deleted the kernel in a attempt to replace kernel 2.6.24-19-generic with a later version that seemed to sit in /lib/modules.  But, duhh, that was the one that was running.  So, before I re-install the entire OS, I was wondering if there's a way to install just the kernel, and where would I get the latest kernel for Ubuntu 8.08?

Also, I've been dual-booting with Vista - Vista's boot manager can optionally pass control to Grub, and vice versa.  By re-installing just Ubuntu's kernel, could I avoid having regenerate an enty in Vista's BCD boot menu for Ubuntu's Grub boot manager?

*TimDaniels*

---

### Post by TimDaniels on 2009-02-19
> **TimDaniels said:**
> .... where would I get the latest kernel for Ubuntu 8.08?

I meant 8.04, i.e. Hardy Heron.

*TimDaniels*

---

### Post by glotz on 2009-02-19
Try sudo apt-get install linux. Or use your package manager of choice.

(I think that'll pull in also the headers, you might want to do away with those unless you do compile kernels.)

---

### Post by TimDaniels on 2009-02-19
> **glotz said:**
> Try sudo apt-get install linux. Or use your package manager of choice.

(I think that'll pull in also the headers, you might want to do away with those unless you do compile kernels.)

There's a problem with that:  I can't run the OS since the kernel is gone.  I can get to Grub, but Grub can't find a kernel, so Ubuntu doesn't run, and so there's no terminal on which to enter those commands.

*TimDaniels*

---

### Post by glotz on 2009-02-19
I see, I thought you were still in that session.

Have you got the desktop CD or any LiveCDs? If yes fire one up and copy its kernel to your disk and modify /boot/grub/menu.lst to point to it. Then boot Ubuntu off it and install the kernel you had.

---

### Post by TimDaniels on 2009-02-19
> **glotz said:**
> I see, I thought you were still in that session.

Have you got the desktop CD or any LiveCDs? If yes fire one up and copy its kernel to your disk and modify /boot/grub/menu.lst to point to it. Then boot Ubuntu off it and install the kernel you had.

I now have a downloaded .ISO file containing the latest 8.04 version of Ubuntu.  To use the kernel contained in that file, I have some questions:
1) What is the location of the kernel?
2) Can I transfer just the kernel using the installer that loads when I put in the .ISO CD?
3) Where in the old 8.04 should the kernel be put/installed?
4) How does one install the kernel?  (Is it just a copy and paste?)

Given the above newbie questions, would it be easier to just install the new version of Ubuntu 8.04 from the .ISO file?


*TimDaniels*

---

### Post by glotz on 2009-02-19
Well, well... Since you have the reinstall as a failsafe option, if you're interested you could try fixing it too. :)

Reinstall could be faster though.

You need these files
boot/vmlinuz-*version*
/boot/config-*version*
/boot/abi-*version*
/boot/System.map-*version*
and then the corresponding
/lib/modules/*version*/kernel

It's just copy/paste I think. Try firing up Synaptic on the live CD and searching for linux-image package. Select one it shows installed (a green blip before it) Then right click it > properties > installed files. Copy those over. Then as the last step, change (if needed) /boot/grub/menu.lst to point to which ever *version* of the kernel you just copied over. Then remove the CD and boot away.

**EDIT**: Damn, now that I reread your first post it looks like you already have more kernels! If you do, all you have to do is to point /boot/grub/menu.lst to one.

---

### Post by TimDaniels on 2009-02-19
> **glotz said:**
> [....]now that I reread your first post it looks like you already have more kernels! If you do, all you have to do is to point /boot/grub/menu.lst to one.

Does that mean to edit the /boot/grub/menu.lst so that the address /lib/modules/*kernel-version* appears as the default entry for the kernel selection?

*TimDaniels*

---

### Post by glotz on 2009-02-19
Actually it only points to vmlinuz and initrd (forgot all about this baby) in /boot, it's very self explanatory when you take a look at it. Please do **ls** of the original /boot/ and **cat** of the original /boot/grub/menu.lst and paste them here.

---

### Post by TimDaniels on 2009-02-20
> **glotz said:**
> Actually it only points to vmlinuz and initrd (forgot all about this baby) in /boot, it's very self explanatory when you take a look at it. Please do **ls** of the original /boot/ and **cat** of the original /boot/grub/menu.lst and paste them here.

Too late.  I'm re-installing right now.  Thanks.

*TimDaniels*

---

