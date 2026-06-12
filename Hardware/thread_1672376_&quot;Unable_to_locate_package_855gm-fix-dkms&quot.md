---
title: "&quot;Unable to locate package 855gm-fix-dkms&quot;"
date: 2011-01-20
forum: Hardware
---

### Post by mvandemar on 2011-01-20
I just installed Ubuntu 10.10 on an IBM Thinkpad R51. I am having issues with getting something other then the (I think) fbev driver to function. I tried performing the instructions here:

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Testing%20upstream%20patch%20for%20i855](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Testing%20upstream%20patch%20for%20i855)

But I got this message at one point:

"Unable to locate package 855gm-fix-dkms"

I verified that the repository is in fact added, and I can see it listed under Software Sources -> Other Software. Afterwards on reboot I got a blank desktop and nothing else. At times various elements I knew where there would flash, like if I clicked on the Applications menu, but not long enough for me to interact with them. I rebooted into a console, and edited /etc/X11/xorg.conf to use the vesa driver instead, and then rebooted again, but could not get a graphical interface after that. I then renamed xorg.conf to xorg.conf-disabled, rebooted, and tried to implement [Brian Rogers]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511/comments/427") fix, as suggested here:

[http://ubuntuforums.org/showpost.php?p=10345085&postcount=5](http://ubuntuforums.org/showpost.php?p=10345085&postcount=5)

I added the ppa, but do not understand how to add the actual package. Also, something I wasn't expecting, it looks like at some point in these attempts I somehow wound up with Ubuntu 11.04 - Natty Narwhal? Not sure how that crept in.

I am not that worried about getting Compiz to work, although it might be nice. Older laptop though so would probably be just as well without it. I would really like to be able to change my screen resolution though. 

Any help appreciated.

-Michael

Edit: I renamed /etc/X11/xorg.conf back to it's proper name, and rebooted, and it appears to be working now, although glitchy (corners of the bottom panel were missing until I moused over them, some flickering). Unfortunately it looks as if the maximum resolution is only 1024x768 anyway, so what I initially wanted isn't going to happen regardless. I guess I will switch back to the default driver, since that is the resolution I started with, but without the flickering.

---

### Post by Don Scapp on 2011-02-19
I managed to find the package by manually adding these sources:

> deb [http://ppa.launchpad.net/glasen/855gm-fix/ubuntu](http://ppa.launchpad.net/glasen/855gm-fix/ubuntu) lucid main
deb-src [url]http://ppa.launchpad.net/glasen/855gm-fix/ubuntu lucid main    

But now it gives me this:   

> Building initial module for 2.6.37-graphics2+12-generic  
Error! Bad return status for module build on kernel: 2.6.37-graphics2+12-generic (i686) 
Consult the make.log in the build directory /var/lib/dkms/855gm-fix/0.7.7/build/ for more information. 
dpkg: error processing 855gm-fix-dkms (--configure):  subprocess installed post-installation script returned error exit status 10 
Errors were encountered while processing:  855gm-fix-dkms 
E: Sub-process /usr/bin/dpkg returned an error code (1)      

Any ideas?

---

