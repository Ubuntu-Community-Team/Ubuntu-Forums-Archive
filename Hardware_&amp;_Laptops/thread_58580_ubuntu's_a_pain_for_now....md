---
title: "ubuntu's a pain for now..."
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by unixpusher on 2005-08-20
In the last 7 years, I've gone from slackware to redhat to mandrake, figured out maybe it was time for a newer, fresher distro. I decided to try ubuntu, having heard so much praise about it. 

Getting used to the debian way to admin the box was interesting, I expected I would have to relearn how to config stuff. The problem was trying to get shit to work ok.

I needed to install the newest ati drivers, failed, had to use agp-get to install xorg-fglrx-driver an older driver someone prepackaged. My opengl apps still wouldn't run right, untill i manually fixed the xmu lib package by creating symlinks.

The sound didn't work with xmms untill I started kaffeine, even if pre-started alsa.. 
then no sound in vmware , can't open /dev/dsp
vmware was a pain to install, because of the way ubuntu installs kernels headers.

Font size on apps were real small and I was unable to use the kde fontsize tool to get the bigger fonts i wanted, like in firefox ( shouldn't have to mess with the chrome settings files ). Had to go to 1024x768... lame, probably something to do in adapting kde to ubuntu, because it works fine on mandrake

then we get to my dvd burner... spent a night going crazy over that
Couldn't get decent read speed out of it, even after trying 4 different fixes i read about. supposely I could have fixed it by recompiling, but I was not going to recompile my kernel just for that....
Also, that POS gam_serve keeps files open on the cdrom drive, kde or /sbin/mount wouldn't work to umount untill i killed gam_serve...
Next, k3b couldn't burn, it was trying to use the device as a scsi device... didn't have to use scsimod since 2.2, that was the last drop.

I've spent way more time than i wanted too TRYING to get to the same point I was at with Mandrake. I work on unix boxes all day, at night I want to enjoy mine. I don't have the time and motivation to geek out on my system like i did when i was using slackware.

Some stuff in ubuntu is superior to other distros, like the package manager. This distro looks promissing ( especially since it's only a year old ) , but I think I'll wait for a couple more release before I try it again. 

Thanks to all who posted fixes in this forum.

---

