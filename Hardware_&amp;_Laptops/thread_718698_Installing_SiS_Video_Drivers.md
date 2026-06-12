---
title: "Installing SiS Video Drivers"
date: 2008-03-08
forum: Hardware &amp; Laptops
---

### Post by s2welee on 2008-03-08
I have a Intel little valley D201GLY2 that I am having trouble with the video.  Anytime I hook it up to a monitor, I get horizontal lines and just a nasty display.  I think it is a driver issue.  

I have downloaded the drivers from Intel, but I am not sure what to do with them.  I have a .la file and a .so file that came in the download.  If anyone can tell me where these files need to go I would really appreciate it.  I cannot find anywhere to just add a driver or update the driver.  Thanks for the help.

Ubuntu 7.10 Gnome

---

### Post by ssj3strife on 2008-03-08
Try running

sudo dpkg-reconfigure xserver-xorg

and selecting different options from that menu. Try the vesa driver first, then look for any other that might work, such as intel or sis.

As far as the files you downloaded, .so looks like a kernel module, that you could try running modprobe or insmod... but then you'll need to reconfigure X manually to use it. That's a little beyond my expertise, but hopefully that first command will solve your troubles.

---

