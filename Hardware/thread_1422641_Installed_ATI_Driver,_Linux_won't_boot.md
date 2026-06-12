---
title: "Installed ATI Driver, Linux won't boot"
date: 2010-03-05
forum: Hardware
---

### Post by P2000camaro on 2010-03-05
I just installed Ubuntu again after about a year of not using it. Afterward I installed the restricted ATI driver (I have an ATI Mobility card.. I think it's the 3460). Now after GRUB I just get a black screen. I just booted from the CD, but I cannot figure out how to uninstall the driver from here as it's not actually booted to my desktop, just the LIVE CD. Is there any way to get back into Linux without fully reinstalling?

---

### Post by Barriehie on 2010-03-05
> **P2000camaro said:**
> I just installed Ubuntu again after about a year of not using it. Afterward I installed the restricted ATI driver (I have an ATI Mobility card.. I think it's the 3460). Now after GRUB I just get a black screen. I just booted from the CD, but I cannot figure out how to uninstall the driver from here as it's not actually booted to my desktop, just the LIVE CD. Is there any way to get back into Linux without fully reinstalling?

Do you get to the grub menu screen where it says 'recovery console' or something to that effect???

---

### Post by n8ek on 2010-03-06
I am having exactly the same problem, i get grub menu screen where it says 'recovery console' but dont know what to do when i go into recovery console, i tried startx and got the black screen.

Thanks

---

### Post by n8ek on 2010-03-06
I managed to get back into Ubuntu by doing this in the recovery console sudo apt-get remove --purge xorg-driver-fglrx

hope it helps P2000camaro

---

### Post by agnes on 2010-03-06
n8ek is right. Also, you have a backup of your xorg.conf file in /etc/X11. So you can always bring the situation back to normal, by replacing the current Xorg settings in xorg.conf by the right backup in xorg.conf*. 

However, I had several issues like these with a Mobility Radeon HD once and I remember this (both options) working:

**option 1)** Type, after having installed the driver
```
aticonfig --initial -f

```
in console.
If it then still doesn't work after reboot, type ```
aticonfig --acpi-services=off
```  OR edit the boot settings in /boot/grub/menu.lst and boot with the options "noacpi" and "acpi=off" 
Then the graphics will work, but acpi is then off, so you don't have extended power management, e.g. suspend/hibernate won't work.

**option 2)** I don't know if you installed the Catalyst driver from Ati's website or just the driver from the repos. Anyway, after removing the  driver, try the different version. The one in the Karmic repos is derived from Catalyst 9.10 while version 9.12 is on the ATI site, so it does matter. (edit: older ones are also available, but too old will not work on your system, so read the Release Notes first).
Now, I once (at an older kernel) could only have a successful install of the one from ATI's site *after* having installed the one from the repos (don't ask me why...). So that may also be a last solution if aforementioned things don't work.

---

### Post by n8ek on 2010-03-07
1 problem i have encountered since getting my GUI back is Emerald and Compiz no longer work even after completely removing the ATI driver's (i think)

Thanks

---

### Post by n8ek on 2010-03-07
I found this to be a great help if needed? 

[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)

I now have eye candy back

---

