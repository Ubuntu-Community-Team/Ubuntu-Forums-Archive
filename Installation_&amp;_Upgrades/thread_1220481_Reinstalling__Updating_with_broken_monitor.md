---
title: "Reinstalling / Updating with broken monitor"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by thepipirate on 2009-07-22
Well, I'm using an old HP Pavillion dv5000 laptop.  One challenge: the built in monitor is broken (and more than the value of the laptop to repair).  So, I can only get any information (other than hard drive spinning lights, etc) once X starts, at which point my external monitor starts to work.  The only other piece of information is the backlight on my external monitor turning on and off, but I'm not really sure 

When trying to update to 9.04, I did... something bad.  I think I may have messed up menu.lst, but it looks OK to me (attached).  When I boot without a boot CD, I get nothing - neither do I get to anything I can see on the screen, nor does the machine ask for an IP from the router.  So, I booted to a boot CD, ran through the manual partitioner, set / to the appropriate partition, checked the menu.lst. Same symptoms on boot up (although now I'm not sure if it is getting an IP from the router - the computer I was using to check that is no longer here).

What might be nice is to get logs of what happens when I turn on the computer without the boot CD.  I tried turning on bootlogd, but /var/log/boot stays empty.

With the boot CD, it boots normally and I have the usual functionality upon reaching X (can mount other disk, etc)


So, any ideas? Are there logs for grub sitting around somewhere? Should I try formatting the entire disk (I'd rather not lose the Windows partition, although I rarely use it...)?

---

