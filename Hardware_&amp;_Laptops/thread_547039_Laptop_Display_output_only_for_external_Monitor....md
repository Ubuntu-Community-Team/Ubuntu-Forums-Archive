---
title: "Laptop Display output only for external Monitor..."
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by matthews_406 on 2007-09-09
I have a Dell Inspiron 1520 (Graphics = NVidia 8600 GT)

Ubuntu Installed perfectly except for 1 thing.

I do not have a GUI on my own screen, I only get it when I use an external monitor...
How do I change it.

In Windows there is a Display Preference where you can pick screen 1 or 2.
Or by hiting F5 you can also switch,,,

Does Ubuntu have somthing simular??

I have found out that hiting ctr-alt-f1 gives me a textual display on my own screen, but the Graphical display is only availiable on the external monitor. (alt-crt-f7)


Any Idea's??

---

### Post by frith on 2007-09-09
Hmmm laptop monitor support... prepare for the pain.

Does it work on your internal display when you don't have the external monitor plugged in?

To test this, you have to restart X (or maybe even Ubuntu) with the external monitor unplugged.

If you can get the display to work without the external monitor, and you now want to get both of them working, the road I went down is using the binary nVidia drivers and TwinView. It pretty much kinda worked mostly... But its a start.

And as far as I know there is no shortcut for switching displays, the support for monitors and external displays (which is a special case of dual displays, which don't really work yet).

There is hope though:

[http://www.linux.org.au/conf/2007/talk/95.html](http://www.linux.org.au/conf/2007/talk/95.html)

[http://ozlabs.org/~jk/docs/mergefb/](http://ozlabs.org/~jk/docs/mergefb/)

frith

---

### Post by matthews_406 on 2007-09-10
Ok, I don't think I was clear enough.

I turn on the laptop. It shows Dell and Bios.
I am sent to Grub Loader and Select Ubuntu.
The orange bar comes and loads fully.

Now, the Screen turns black, I hear the jungle like sound for the login.

(At this point, the external Monitor is not attached....)

ALT+CTR+F1 Gives me a text display.
ALT+CRT +F7 gives me a black screen.

I am using 7.04 on a DELL Inpiron 1520.
I have downloaded and installed all the updates.

HOW do I tell X-Server to send the Signal to the screen attached to my laptop...instead of acting like desktop computer??

---

### Post by h2osho on 2007-09-10
I'm having a similar problem. I have a Dell Insiron 8600 and I can get the Dell and XP flash screen to come up then the scren goes black. I'm currently plugged into my HDTV and is a big PAIN.

I replaced the INVERTER and it worked for a few days then went blank again. So now I'm thiniking it's a software/driver conflict? I think I downloaded a latest and greatest vidoe driver from NDIVIA and installed it, but I THINK it's messed up my OEM installed driver for the display.

I DO NOT know how to reset all the drivers back to original installation.

So you're problem MAY be hardware and not software. 

If anyone knows how to have me remove the NDIVIA driver and use the Dell driver which came with my laptop I would be very happy.

Thanks

---

### Post by frith on 2007-09-10
Okay.. This is not something I have experienced, but I'll give a couple of suggestions:

Are you using the binary nVidia drivers? If so, there is a utility called nvidia-settings (sudo nvidia-settings) that will detect your displays and set up your configuration. I should warn you that it plays around with your xorg.conf file, so anything you have added may get removed.

Alternatively, it would also be helpful to have a look at your xorg.conf file (/etc/X11/xorg.conf - need to be superuser to edit it) This file is in charge of your display - regarding what goes where and what devices to use. You may be able to diagnose your problem just by looking at it, or alternatively post it here for the experts :)

Frith.

---

### Post by frith on 2007-09-10
P.S. h2osho:

sudo dpkg-reconfigure -phigh xserver-xorg

will reset your xorg.conf - this will use the default ubuntu drivers, I believe they are 'nv'. As for actually removing the drivers, this is a new and interesting challenge which I have attempted, but didn't find a good solution - I did sudo apt-get remove nvidia-glx which removes the package and dpkg -l | grep nvidia to find the installed packages relating to nvidia. Then dpkg -P <the list of nvidia related packages> should remove them. modprobe -r <modulename> will also remove modules from the kernel, but this shouldn't be necessary. 

Hope that helped.

---

### Post by matthews_406 on 2007-09-11
> **frith said:**
> Okay.. This is not something I have experienced, but I'll give a couple of suggestions:

Are you using the binary nVidia drivers? If so, there is a utility called nvidia-settings (sudo nvidia-settings) that will detect your displays and set up your configuration. I should warn you that it plays around with your xorg.conf file, so anything you have added may get removed.

Alternatively, it would also be helpful to have a look at your xorg.conf file (/etc/X11/xorg.conf - need to be superuser to edit it) This file is in charge of your display - regarding what goes where and what devices to use. You may be able to diagnose your problem just by looking at it, or alternatively post it here for the experts :)

Frith.

Thanks a  lot... I am not sure if my random changing things did it, (I just hoped for the best and guessed when I didn't know what it was asking me..

Anyways, my problems is solved. I booted it without being plugged in, and just let it go. 
**Strange thing, I only have display when I run off battery!! as soon as I plug it in, I need to use an external monitor....**

Please fix this for 7.10


Thanks a lot.

I

---

