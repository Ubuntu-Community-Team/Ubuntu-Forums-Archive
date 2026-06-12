---
title: "[SOLVED] Please help very urgent!!! dpkg gone fubar!"
date: 2008-11-17
forum: General Help
---

### Post by cyberfin on 2008-11-17
Please help me anyone who can!

I was dumb enough to follow this tutorial to try [changing the bootsplash]("http://www.ubuntugeek.com/how-to-change-the-bootsplash-in-ubuntu-810-intrepid-ibex.html") and during the step where I was supposed to install splashy_0.3.10-1_i386.deb I accidentally ctrl+c'd (I intended to do that to another terminal window but misclicked and ended doing it in the terminal that was in the middle of dkpg'ing).

The result is that now every time I try installing something (through apt-get, aptitude, synaptic, anything!) I get this message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

```

So I run the suggested command and it goes on to do the following:

```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
```

Which ends up going on until it says I've run out of diskspace!

What gives?

Pweety pwease!

---

### Post by plucky on 2008-11-17
> Which ends up going on until it says I've run out of diskspace!

What gives?


Post output of ```
df -h
```.

If you have a /boot partition,then it might be full,which would cause the problem.

Also post output of ```
cd /boot
ls -l
``` which will show the files in your /boot partition.


Good Luck

---

### Post by cyberfin on 2008-11-25
Well,

I chose finally to backup as much as I could and do a fresh install of 8.10. However I still find it annoying that dpkg has this error which seems impossible to solve if it's not by succesfully installing what was being installed. If the installation isn't successfull for whatever reason, you're stuck in the situation forever.

I find it hard to believe there is no reset or clear option for dpkg, even if it leaves a dirty install, as the idea at the time was to backup through some apps (that needed installing) but that could not be performed due to the error.

Anyway, problem solved (in a manner).

---

