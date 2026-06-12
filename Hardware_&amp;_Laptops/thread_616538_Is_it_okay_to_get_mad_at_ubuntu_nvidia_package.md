---
title: "Is it okay to get mad at ubuntu nvidia package?"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by malfist on 2007-11-18
This happened last time I used ubuntu, I installed the nvidia's driver (GeForce FX 5200 Ultra) from nvidia themself. I launch gnome, everything works, everything is nice. Ubuntu tells me I'm using a restricted driver but so what, it works. Then comes the reboot, I'm sorry, ubuntu is running in low res mod, would you like to configure? Ubuntu is currently using the vesa driver, would you like to select a new driver.

I installed the nvidia driver, I configured xorg.conf, why is it running vesa! WHY? So then I scroll through the options of drivers, and guess what? No nvidia driver, so I select xorg's nv driver, that should work until I can make it use the nvidia driver again. Guess what? No luck, X crashed, stuck with vesa.

So I log in, low res an all, with vesa, no 3D, worse than vista areo or windows ME on a bad day. So I notice there is not a restricted driver in use waring or icon, so I check it out. Guess what? The nvidia driver is no longer selected! Yeah! I love it when ubuntu 'helps' me, it reminds me of windows! I love it.

So then I select it, tell it to use the nvidia driver, does it use the nvidia driver that I installed? No! It apt-get's nvidia-glx-new or whatever the package is called. That's not what I wanted, that's why the other is installed. Then it tells me I need to reboot! What? I installed a driver for my graphics card, why does it want me to reboot? Maybe it wants me to restart X, so I do. Nope, still low res, still needing a reboot. WFT? The nvidia driver from nvidia didn't make me do that, and it even compiled a kernel module.

So I reboot, and now what I am I stuck with, low res again, but I'm using the nvidia driver! W00t! To bad when I configured xorg, it's being ignored. So I switch to terminal and reinstall the already installed nvidia driver from nvidia and go back to gnome. Well, other than the login screen displays at a really low res everything works, well except for the title bars, they're at something like 6 point font, and well, I really don't know what will happen when I reboot again, and well I don't really know how well nvidia uninstalled apt-get's nvidia driver, and well, I don't know what other problems that will arise from it that I can't trace back to it.



Please, someone fix it! It didn't do this the 7.04!

---

### Post by FrostDust on 2007-11-18
I had the *same *thing happen to me. While I would have new driver work with my card, I would have at least expected the RDM to know that the 5200 was incompatible, and not given me the runaround for half an hour while I tried to figure out what was going on.

---

### Post by jigglysnot on 2007-11-18
same thing happened to me. Pentium 4 with Nvidia Geforce FX 5200.

I then installed the Nvidia drivers again using Envy. I think it still gave me the same low-res thing, and de-selected Nvidia driver from its Restricted Drivers.

After a bunch of messing around with menus (Restricted Drivers, Ubuntu's default screen resolution/ monitor menu, and Nvidia's), I was able to get it to work.. O_O""

---

### Post by FrostDust on 2007-11-18
> **jigglysnot said:**
> same thing happened to me. Pentium 4 with Nvidia Geforce FX 5200.

I then installed the Nvidia drivers again using Envy. I think it still gave me the same low-res thing, and de-selected Nvidia driver from its Restricted Drivers.

After a bunch of messing around with menus (Restricted Drivers, Ubuntu's default screen resolution/ monitor menu, and Nvidia's), I was able to get it to work.. O_O""

When you say "able to get it to work", do you mean with the compiz-compatible driver? If so, I would love being able to use my 5200 for that.

---

### Post by malfist on 2007-11-18
I rebooted and guess what? Ubuntu 'helped' me and ignored my Xorg.conf and told me that it was running in res using vesa.

Why the hell, and how the hell do I stop it from doing this?

---

### Post by malfist on 2007-11-19
Each time I reboot, I have to reinstall the nvidia driver. This is really annoying. Really, it is.

---

### Post by malfist on 2007-11-20
It won't even use the binary driver from the repos! I've had enough, this is my third installation of gusty, and none of them worked. Gonna try gentoo or yopper or something.

---

### Post by linuxonbute on 2007-11-20
Hi Guys,

see the solution in this thread:

[http://ubuntuforums.org/showthread.php?t=616688](http://ubuntuforums.org/showthread.php?t=616688)

---

### Post by malfist on 2007-11-20
Nope, that made things even worse.

---

### Post by malfist on 2007-11-20
Envy fixed it. Thank god for envy.

---

