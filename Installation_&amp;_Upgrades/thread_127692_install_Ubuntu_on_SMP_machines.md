---
title: "install Ubuntu on SMP machines"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by nymphaeles on 2006-02-09
knowing that my machine is a dual Intell Xeon, is there a way to start the install fresh with smp kernel instead of the default 386 :-k

---

### Post by taurus on 2006-02-09
You can upgrade to SMP kernel once it's done!  I upgraded my machine to smp since I have a P4 3.0 GHz with HT...  :)

---

### Post by Cashel on 2006-02-09
This seems completely uneccesary, but if you have a working kernel you should be able to pass that along to grub (like kernel /mnt/point/yadda/yadda) .. you can normaly.. where in the install process you'd do it I couldnt say... 

On another note.. you using the 64 bit ubuntu or the 32? I am finding on my machine (Athlon X2) that the 64 bit distro is more of a headache then a benefit. Since 32 bit libs dont coexist nicely with 64 bit ones (that is, unless you create a chroot environment), I'm finding a lot of the stuff I want to install just wont work properly. At least with out major reconstruction.. So I'm switching back to the 32 bit installation and just making sure to compile my own kernel (Which you should always do anyways I think).

If your experience is any different let me know! Maybe we should start a 32 bit vs 64 bit lib's thread :)

Cashel

---

### Post by nymphaeles on 2006-02-09
My machine is a Dell precision 610 that has dual pentium II Xeon 450MHz.  I did a test install awhile ago using Fedora Core 4, it had no problem recognizing the 2 CPUs and installed the appropriate smp kernel.  I did a Ubuntu 5.10 install yesterday, and the smp kernel was not installed.  I understand that I can always apt-get the appropriate kernel, but it is much nicer if there is a switch that I can put in to tell the install to do smp kernel to start with.

---

### Post by Sutekh on 2006-02-09
How many CDs does Fedora Core 4 come with to install? 4 CDs if memory serves.

The reason the 386 is the only kernel included is to get Ubuntu installed in a way that is compatible with *most* systems, using a single CD.

It would be nice to have more kernels on the CD (I need a SMP for my AMDX2), but I'd rather have one CD to install then use apt-get later on to download things I need.

---

### Post by taurus on 2006-02-09
[QUOTE=nymphaeles]My machine is a Dell precision 610 that has dual pentium II Xeon 450MHz.  I did a test install awhile ago using Fedora Core 4, it had no problem recognizing the 2 CPUs and installed the appropriate smp kernel.  I did a Ubuntu 5.10 install yesterday, and the smp kernel was not installed.  I understand that I can always apt-get the appropriate kernel, but it is much nicer if there is a switch that I can put in to tell the install to do smp kernel to start with.[/QUOTE]
Yes, there is a switch for such a task.  It's called synpatic!!!  Again, install the default kernel first, i386, and fire up synaptic and get the latest version for smp.  Edit your /boot/grub/grub.conf or /etc/lilo.conf to boot from the new one and you are good...

---

### Post by mlomker on 2006-03-29
[QUOTE=taurus]Yes, there is a switch for such a task.  It's called synpatic!!!  [/QUOTE]

I think what he was looking for was a kernel boot switch that'd tell it to load an alternate kernel during installation.  Perhaps you misunderstood what he was asking but he perceived your post as confrontational and reported it.  

I, personally, am not aware of such an option.  Sutekh provided the most likely reasoning for why Ubuntu did it that way.  Quite a few other distros will automatically detect SMP but they are multi-CD distros (Redhat and Debian come to mind).

---

