---
title: "Problems with X after upgrade (Nvidia FX5200)"
date: 2006-05-11
forum: Hardware &amp; Laptops
---

### Post by jambe on 2006-05-11
After installing the latest XOrg updates using apt-get on ubuntu breezy, x fails to start. I can get it to work using the vesa driver but that is pretty limited...

It looks like xorg-common is at version 6.8.2-77.1

I get the unhelpfull "Fatal server error: no screens found" Message. I am thinking it might a compatibility error with the nvidia driver and the version of X. Is that possible. I can't seem to compile a new version of the nvidia driver with out jumping throught hoops (such as changing my gcc version etc).

Anyone else have this problem?

---

### Post by Mustard on 2006-05-11
I've had no errors with a FX5200 using nvidia-glx drivers since the latest xorg updates.  I guess it's a problem specific to the drivers you have downloaded from nvidia.

---

### Post by Dr. Nick on 2006-05-11
When you updated xorg did you also update the kernel? If you updated kernel make sure to install the linux-restriced package for your specific kernel version.

The nvidia-glx package has always seemed to work well for me, I quit using nvidias sites drivers since they become a pain to keep updated with new kernels

---

### Post by Dr. Nick on 2006-05-11
Oops

---

### Post by bernardfrancois on 2006-05-11
I had a similar problem. See [http://www.ubuntuforums.org/showthread.php?t=174129](http://www.ubuntuforums.org/showthread.php?t=174129) . It's not solved yet, but I'll re-install the nvidia driver.

---

### Post by jambe on 2006-05-11
I have tried booting up with an earlier kernal which used to work so I would expect that to go if the restricted-modules hadn't been updated. apt-get seems to think that they are at the latest version. I'll check that they match the kernal though.

I'm also trying the install nvidia script here to see if that works. [http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

---

### Post by Dr. Nick on 2006-05-11
What I worry about is that if people try to install different nvidia drivers then xorg wont know which one to use, for example both nvida-glx and the nvidia installer drivers use "nvidia" I dont know if xorg will get confused.

This is just my opinion, I am no expert just thinking logically, so if you decide to try different methods I would try to delete your past atttempts

---

### Post by bernardfrancois on 2006-05-11
How to do all this stuff (removing old drivers and install the new ones) is described in this howto: [http://www.ubuntuforums.org/showthread.php?t=75074&highlight=howto+latest+nvidia+drivers](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=howto+latest+nvidia+drivers)

I just used it, and it resolved my problem. I followed the instuctions under 'METHOD 2' in the howto.

---

### Post by jambe on 2006-05-11
I've managed to stuff up my dselect/dpkg selections now, is there anyway to just tell it to just mark everything installed as "install" currently it wants to delete about 1.4Gb's of software!

Not having a good day...

---

### Post by Dr. Nick on 2006-05-11
what exactly did you do to make it want to remove so much data?

---

### Post by jambe on 2006-05-11
I think I must have unselected X some how (maybe thinking I would reinstall it), which naturally made it dselect every package the relys on x (quite a few).

I think I have managed to reselect everything, still don't have the nvidia driver working though.

---

### Post by jambe on 2006-05-11
I spoke to soon, reinstalling x seems to have done the trick (a bit of a drastic thing to do, but it worked). I needed to run the dselect install process twice as the first time it didn't install x for some reason?

Many thanks for all your kind help.

---

### Post by Dr. Nick on 2006-05-11
No Problem, Glad you got it. That makes for a better day.

---

