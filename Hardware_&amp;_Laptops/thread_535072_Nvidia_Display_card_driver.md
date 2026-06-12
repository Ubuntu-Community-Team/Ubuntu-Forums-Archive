---
title: "Nvidia Display card driver"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by josephwahba on 2007-08-26
Hi,
After a few trials i managed to install Ubuntu 7.0.4 on my new HP dv2000 laptop,
the problem is I had to change the the display configuration to VESA using 
	sudo dpkg-reconfigure xserver.xorg
to be able to run it
and after the installation every thing is working fine except that the display only available in 1024x768
I downloaded the latest Nvidia driver which support my card and installed it.
every thing went find and the GUI started using startx command.
but after rebooting the machine i got the message "Failed to Start the X server".
and when i use Nvidia nvidia-xconfigure to configure the xorg.config and then use startx it works fine untill the next reboot

Any ideas??

---

### Post by logos34 on 2007-08-26
you're probably using the wrong nvidia kernel. (the x server error screen will give you details).

You might consider uninstalling it and using the nvidia-glx-new driver in the repos.  

Try this guide:

[http://albertomilone.com/latest_nvidia_udsf_feisty.html](http://albertomilone.com/latest_nvidia_udsf_feisty.html)

---

