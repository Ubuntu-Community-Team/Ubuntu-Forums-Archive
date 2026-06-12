---
title: "Killed My Mouse (Touchpad)"
date: 2008-09-04
forum: General Help
---

### Post by EoRaptor013 on 2008-09-04
What have I done?!?

Hardy on a Dell E1705 laptop. On a whim, I enabled the Linux-Restricted-Modules and Waitfornfs.sh system services and rebooted. The system hung, so I rebooted in recovery mode, and disabled those same two services. Now, no matter whether I boot in regular or recovery mode, my touchpad is dead. The mouse pointer appears in the log-in and desktop but does not respond to any input, either mouse movements or button clicks. Something is still connected to the mouse, however, because I get the pool of circles when I tap the ctrl key (You know, locate mouse with ctrl key option.). I also tried an external USB mouse, without success. 

I don't even know how to diagnose the problem, let alone fix it. Any and all help appreciated. 

Randy

---

### Post by Peter09 on 2008-09-04
You could try installing the touch pad drive again

```
sudo apt-get install xserver-xorg-input-synaptics
```

Not sure whether this will work, but its an option.

---

### Post by EoRaptor013 on 2008-09-04
Good thought! Unfortunately, I tried it and it didn't work. On the other hand, I don't know what possesed me, but I tried sudo /etc/init.d/udev start and all kinds of devices are loading. I'll let you know the outcome.

Randy

---

### Post by SlalomMan on 2008-09-04
If the TouchPad is a usb device, try running "lsusb" to make sure that Ubuntu is seeing the mouse at the hardware level. Then try looking for drivers and such.

---

### Post by EoRaptor013 on 2008-09-04
Most interesting. As mentioned above, for some reason I decided to do sudo /etc/init.d/udev start from tty1. The result was a bunch of messages indicating that various devices were loading. When I switched back to the graphical console, everything was running: mouse, nvidia, wireless, etc. 

So, now the question is why didn't udev run during boot up? 

I know it's got something to do with upstart or init or some such, but not sure what... and I **really** don't want to screw it up again!

Any help appreciated.

Randy

---

### Post by EoRaptor013 on 2008-09-04
OK, I don't know how it happened, but the symlink from  /etc/init.d/udev to rcS.d was missing. I recreated the symlink and all is well! 

Thanks to Peter09 and SlalomMan for your input. They got me poking around and that's what it took. 

Randy

---

