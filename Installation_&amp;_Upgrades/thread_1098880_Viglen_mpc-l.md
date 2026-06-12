---
title: "Viglen mpc-l"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by archerry on 2009-03-17
Having upgraded from server 8.04 to 8.10, I rebooted to get the message:
"kernel panic -not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"
I solved this with:
```
sudo update-initramfs -k all -u
```
BUT...
Now the unit boots to a screen with squares of blue dots across the top of the screen, and overlaid with short, narrow vertical green stripes.
If I log in and then code:
```
startx
```
this fails and returns to a functioning command line.
Two questions:
1. How do I cure the login screen?

2. How do I get the xserver to work properly?

I would install 8.10 directly, but all the variants I have tried fail to detect the HDD.

---

### Post by SixedUp on 2009-05-16
I've just seen this myself, but took a slightly different approach to resolving it.

I had a stable Ubuntu Server 8.04.2 (running the 386 kernel, obviously) and wanted to upgrade to Jaunty. When I did the online upgrade to 8.10, the upgrade completed successfully, but when I rebooted I got exactly the same error as you.

By booting the Intrepid recovery kernel I got a lot more debug information on the console, and it looked to me as though the system had failed to detect the hard drive, or more likely, didn't have a driver built into the kernel for the IDE chipset (which seems like a bug to me)

So at this point I booted the Intrepid system using the old Hardy kernel (which was still available from the grub menu), which then allowed me to bring the system up. I then did a further online upgrade to Jaunty, which succeeded, giving me a fully working Jaunty server install on the Viglen.

Hope that's of some use.

---

### Post by archerry on 2009-05-28
SixedUp
The missing HDD driver is a bug, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318805](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318805)

I have rebuilt the unit with xubuntu 7.10, and upgraded to 8.04.
I do not know how to get xserver to give anything other than a default low resolution on my 17" CRT, the xorg.conf file is almost bare.
I was fortunate enough to have a copy of the original .conf file, but this is not really satisfactory as I want to attach the unit to a flat screen TV.
I have tried installing xserver-xorg-video-geode, but that has not helped.
How do I get the unit to auto detect & configure the video etc?

---

### Post by SixedUp on 2009-05-29
Archerry, I run my MPC-L headless with no xserver, accessing it via SSH so I don't think I can help you much more.

However, you may want to take a look at [this bug in launchpad]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-geode/+bug/236019"), which looks very similar to what you are describing, and is specifically reported from an MPC-L. 

In terms of getting the system to re-detect the video hardware etc, my understanding is that it will do that at each reboot. It was around 8.04 time that Ubuntu picked up the versions of Xorg that start to do a lot more auto-confgiuration and depend much less on the /etc/X11/xorg.conf file. However, I think you can still specify your configuration in there, including the resolutions that your hardware can support. The format is a little arcane though :(

You ought to be able to get a working default version of that file by using the command ```
sudo dpkg-reconfigure xserver-xorg
``` If it turns out that the problem is with the geode graphics driver then it might be worth trying the vesa driver, which ought to work, albeit slowly.

Good luck!

---

