---
title: "HELP! nVidia GeForce 6600 Go"
date: 2008-05-16
forum: Hardware
---

### Post by Da_MerV on 2008-05-16
Hi,

I just made the switch to ubuntu. I've been thinking about Linux options for a while, but I always gave up because I thought it was too complicated. Then I discovered LiveCD.

So anyway, I get it installed. I upgrade 7.10->8.04. Then I go for GFX. I try to set it to advanced effects, and then normal effects, but both fail. So I do some searching around and I find the drivers panel under admin. It says no proprietary drivers are in use.

This is why I did not like Vista. My hardware has no drivers! Without drivers, what's the point? They only have the XP driver. My hardware is not being used to it's potential, so I switch to ubuntu in hopes of some better use.

I have a switch on the front of my laptop that allows me to switch between ext gfx card and on-board (Intel 915 I think). So after failing with the ext, I tried the on-board hoping that drivers would exist for it. Unfortunately, it didn't even make it to the login screen. Once it booted, it showed a strange pattern that was changing it intensity, with colors familiar to the human theme. Nothing helpful however, so I shut it down fearing damage to my PC.

What I want to do:
-Get my GFX card recognized
-Use my laptop's potential
-Get those sexy Compiz-fusion abilities or whatever they're called

My laptop's specs:
-Alienware Area-51M 5500 15.4" WUXGA
-Pentium M 750 1.86 GHz 2MB 533FSB
-2x 1GB RAM
-60GB 5400RPM HDD
-nVidia Go 6600 256MB DDR1 MXM2

I'm new to Linux. Please tell me how I can help you to help me.

Thanks in advance!

---

### Post by buntunub on 2008-05-16
Im not sure I understand your setup entirely, but for the 6600, Ubuntu should have no trouble recognizing it. All you have to do is enable the Restricted Driver Manager under System > Administration > Hardware Drivers, and it will install the driver for you.

---

### Post by Da_MerV on 2008-05-16
I went there and it says "There are no proprietary drivers are in use on this system."

And its 6600 go, the mobile version.

---

### Post by jimv on 2008-05-16
Just so you know that there is hope, I have a GeForce 6100 Go and it works.

Try this in a terminal:

sudo apt-get install nvidia-glx-new

and then:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nvidia-xconfig

---

### Post by Da_MerV on 2008-05-16
Ok i just tried that first step, here's what I got:

merv@merv-laptop:~$ sudo apt-get install nvidia-glx-new
[sudo] password for merv: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-new has no installation candidate
merv@merv-laptop:~$ 

Remember I'm a complete noob at Linux. No clue what that terminal stuff means.

---

### Post by Da_MerV on 2008-05-17
Will [this]("http://www.nvidia.com/object/linux_display_ia32_169.12.html") work?
It's doesn't say Go but my friend says it doesn't matter.
Also, I have no idea how to set up those fun gfx (ie cube, fire, etc)

---

### Post by jimv on 2008-05-17
Well that's odd.

Try this:

```
sudo apt-get update
sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig
```

If that doesn't work, try:

```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```

---

### Post by jimv on 2008-05-17
> **Da_MerV said:**
> Will [this]("http://www.nvidia.com/object/linux_display_ia32_169.12.html") work?
It's doesn't say Go but my friend says it doesn't matter.
Also, I have no idea how to set up those fun gfx (ie cube, fire, etc)

You shouldn't have to download the driver from Nvidia's site.  That's what the commands I posted should be installing for you.

---

### Post by buntunub on 2008-05-17
> **Da_MerV said:**
> Will [this]("http://www.nvidia.com/object/linux_display_ia32_169.12.html") work?
It's doesn't say Go but my friend says it doesn't matter.
Also, I have no idea how to set up those fun gfx (ie cube, fire, etc)

There is no need to go through manual install. Use [this]("http://www.albertomilone.com/nvidia_scripts1.html") and it will do everything required automatically.

---

### Post by Da_MerV on 2008-05-17
> **jimv said:**
> Well that's odd.

Try this:

```
sudo apt-get update
sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig
```

If that doesn't work, try:

```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```

Here's what I got, both failed:

merv@merv-laptop:~$ sudo apt-get update
[sudo] password for merv: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Reading package lists... Done
merv@merv-laptop:~$ sudo apt-get install nvidia-glx-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-new has no installation candidate
merv@merv-laptop:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx has no installation candidate
merv@merv-laptop:~$

---

### Post by Da_MerV on 2008-05-17
> **buntunub said:**
> There is no need to go through manual install. Use [this]("http://www.albertomilone.com/nvidia_scripts1.html") and it will do everything required automatically.

I just tried it. Very bad. When it started, the cursor was an X and it said ubuntu is running in low graphics mode. My beautiful 1920x1200 screen is now forced down to 800x600. What do I do? And what are repositories?

---

### Post by Da_MerV on 2008-05-17
UPDATE:
So I uninstalled the driver from Envy. This successfully returned my 1920x1200 resolution. Then a balloon said I had 22 available updates. After installing these, I checked System>Admininistration>Hardware Drivers once again. But instead of being completely blank, there was an item now under device driver that said NVIDIA accelerated graphics driver (latest cards). I enabled it, restarted, and voila! I can now enable the Extra visual effects!

Hooray! My main problem is solved. Now what do I do to get the extra-sexy eye candy like cube and those things?

---

### Post by jimv on 2008-05-17
you need the compizconfig-settings-manager package

---

### Post by Da_MerV on 2008-05-18
Hooray! It works! Thanks everyone, now I have my laptop just like all those youtube videos.

---

