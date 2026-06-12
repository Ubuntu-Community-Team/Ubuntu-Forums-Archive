---
title: "kernel upgrade and grub entries"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by stoppage on 2009-07-03
Part of a recent Hardy upgrade included an updated kernel version to 2.6.24-24. I decided on the option to retain current grub entries. Now synaptec shows 2.6.24-24 as installed and „uname -r „ returns 2.6.24-23. If I change grub entries will I then be using latest kernel? Obliged for any help here.

---

### Post by drs305 on 2009-07-03
Yes. You can manually edit /boot/grub/menu.lst or install and use StartUp-Manager. It's a great gui app that tweaks the menu.lst file. You can set the menu display, timeout, default kernel to use, number of kernels to display and much more. There is a link on how to use it in my signature line (StartUpMgr).
```

sudo apt-get install startupmanager

```
System, Administration, StartupManager to start once installed.

---

### Post by stoppage on 2009-07-03
One more question....when editing grub do I also change kernel details on (recovery mode) entry? And that's a great app., thank you

---

### Post by drs305 on 2009-07-04
> **stoppage said:**
> One more question....when editing grub do I also change kernel details on (recovery mode) entry? And that's a great app., thank you

If you are referring to changing the default starting kernel, you don't have to change anything in the details of the recovery kernel. StartUp-Manager changes a value for the *operating* kernel - the recovery mode kernel is not automatically selected but remains directly below it's associated kernel option.

If you are 'removing' a kernel via SUM, it 'removes' the recovery mode option as well and you don't have to manually do anything. The word 'remove' is in quotes because the kernel/recovery mode options only remove the options from the menu, they continue to reside on the computer unless removed by synaptic or the command line. But both the kernel and recovery modes are 'removed' from the display at the same time. 

It works the same with regard to the recovery option with actually removing the kernels via synaptic - removing the kernel removes both the kernel and the recovery mode options from the menu AND the machine. Note the recovery mode really is not a different piece of software, it is just a slightly different command line (the word "single" is added).

So unless you are manually removing a kernel entry from menu.lst, everything is taken care of automatically regarding the recovery mode entry. If you manually edit menu.lst, remove both the kernel and recovery mode options.

---

### Post by stoppage on 2009-07-04
Understood. Thanks for the help.

---

