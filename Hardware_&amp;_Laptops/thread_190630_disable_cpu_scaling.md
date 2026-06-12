---
title: "disable cpu scaling"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by cmontburns on 2006-06-06
hi

anyone tell me how  i disable cpu frequency scaling on install as this daemon always freezes my pc totally.

Its a 64 bit sempron 3000 on a gigabyte k8ns moboard - not sure if there is a bios problem in there somewhere but i have this problem on any distro which attempts to activate cpu scaling.

on other distros i use nocpuscaling on boot paramater , this does the trick as I know it is this daemon causing the freeze ups.

cheers

CM

---

### Post by xtacocorex on 2006-06-06
Try removing the package:

sudo apt-get remove powernowd

This should take away the capability of frequency scaling.

---

### Post by cmontburns on 2006-06-06
sorry forgot to explain this occurs on install uc so I need a boot option or expert mode or something?


on other distros they have interactive mode for daemons and sucklike -  such as bed bat ;-) based ones


think i found a solution - gonna try nopowernow on boot parameters...

wish me luck ... am goin in !!
cheers again

cm

---

### Post by cmontburns on 2006-06-06
nope that didnt seem to work any one any ideas how i disable powernow cpu scaling on boot ?

like a cheat code or somthing?


cheers

CM

:confused:

---

### Post by rubinstein on 2006-06-07
I think you can disable it in your BIOS, look for something like "Cool'n Quiet" and disable it.

---

### Post by cmontburns on 2006-06-07
oddly its not in the bios settings anywhere - fact am beginning to think its not on my board somehow and it shud have been ROFL

saying that my mobo is not on the ubuntu supported list mind ...

shame now have to go back to mandriva :-(

---

### Post by rubinstein on 2006-06-08
Maybe you can tweak your CPU Clock Ratio temporarely so that the clock speed of your prozessor is for example 1000 Mhz; maybe when it's so low powernowd behaves different.

When you have installed Ubuntu, you can remove the powernowd package and set your prozessor to its normal speed.

May sound weird, but if it works?

---

