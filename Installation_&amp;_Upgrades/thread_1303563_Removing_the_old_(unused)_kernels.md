---
title: "Removing the old (unused) kernels?"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by MS-Hater on 2009-10-28
I, like so many people in the world, care a lot about having free hard drive space... which is why I'm wondering if it's safe to remove the old kernels from the hard drive, since I don't use them any more. here are the files I'm looking at removing:

initrd.img-2.6.28-11
abi-2.6.28-11-generic
config-2.6.28-11-generic
System.map-2.6.28-11-generic
vmcoreinfo-2.6.28-11-generic
vmlinuz-2.6.28-11-generic

I'm also considering setting my sights on the 2.6.28-15 versions of those files too. I know that I'd have to edit the grub boot menu.lst file and remove those entries, but my questions are:

am I going to break the system?
what steps am I missing (if any)?

TIA.

---

### Post by earthpigg on 2009-10-28
hi,

have you tried searching synaptic for the word 'linux', and removing them from there? that is why we have package managers, after all :D

i strongly advise *against* simply deleting the files.

i also suggest you leave at least 2 kernels in place. i prefer to keep the current one, and one kinda old one.

---

### Post by drs305 on 2009-10-28
I wrote this guide about limiting the number of kernels displayed during boot. It evolved into a post about StartUp-Manager - a GUI app that tweaks Grub's menu, including kernels shown on the menu. You can make the changes without manually editing menu.lst

It also has a section on how to remove kernels from your system, which StartUp-Manager doesn't do.

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

I recommend StartUp-Manager for the original Grub. It works for some, but not all, settings with Grub 2.

---

