---
title: "Bumblebee in Ubuntu 15.04"
date: 2015-10-04
forum: Hardware
---

### Post by rasmus91 on 2015-10-04
Hey All

(Ubuntu 64bit)

I'm trying to get bumblebee up and running on my Asus UX32VD. It's an nVidia GeForce 620m card in it other than the intel one.

I've had bumblebee working fine on other installations, but this time, i just can't get it to work. I've followed this guide: [http://rajat-osgyan.blogspot.dk/2015/03/how-to-install-bumblebee-on-ubuntu.html]("http://rajat-osgyan.blogspot.dk/2015/03/how-to-install-bumblebee-on-ubuntu.html")

But when i get to step number 6.:
>  6) One more reboot

Once rebooted if you run the command
primusrun glxinfo | grep OpenGL

You would see the OpenGL String points to
OpenGL vendor string: nouveau

This confirms that bumblebee is working fine and able to load the nouveau driver fine.

NOTE no need to edit the /etc/bumblebee/bumblebee.conf file as of yet as it is already configured for using nouveau drivers.

And run:
```
primusrun glxinfo | grep OpenGL
```
The result is:
```
primus: fatal: Bumblebee daemon reported: error: Could not load GPU driver
```

I can't do glxgears or anything with optirun, it just isn't working.

Can someone help me?

Thanks :)

---

### Post by efflandt on 2015-10-04
Why are you trying to use bumblebee and which nvidia package do you have installed? Nvidia packages in Ubuntu 14.04 and newer have nvidia-prime making the bumblebee kludge unnecessary. I could get optirun to work in 13.10, but not primusrun at all. Since 14.04 all you should have to do for hybrid Intel/Nvidia graphics is install an nvidia driver package (although, I am not sure which versions are in 15.04 repositories), but you would probably also need to undo all the bumblebee related stuff.

Then to switch graphics you would use **NVIDIA X Server Settings**. After switching from Nvidia to Intel you have to log out of X and back in for it to take effect. After switching Intel to Nvidia I have to reboot. Then you do NOT have to use optirun or primusrun or any additional related parameters sometimes required for those.

---

### Post by rasmus91 on 2015-10-05
Honestly i was unaware until i read the guide mentioned in the original post. however, bumblebee is still desirable for a few reasons:

1) With primusrun, i don't have to logout to switch back to the intel graphics.

2) according to several people unity seems to have a bit of tearing in the desktop with nvidia prime.



If i was to revert to nvidia, how would i do that?

some apt-get purge nvidia* and bumblebee, and then with the official nvidia respository install an nvidia driver, along with nvidia-prime?

---

