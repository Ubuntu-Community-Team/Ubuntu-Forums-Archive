---
title: "Disable wacom stuff"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by strabes on 2007-05-09
I have a dell inspiron E1705 which is not a tablet PC.  I have disabled the bootsplash in menu.lst. When my computer is booting, I notice that it sometimes says something about wacom drivers. I would like to disable this since my computer is not a tablet PC. Here's the output of "locate wacom"

> alex@alex-laptop:~$ locate wacom
/var/lib/dpkg/info/xserver-xorg-input-wacom.conffiles
/var/lib/dpkg/info/xserver-xorg-input-wacom.postrm
/var/lib/dpkg/info/xserver-xorg-input-wacom.prerm
/var/lib/dpkg/info/xserver-xorg-input-wacom.md5sums
/var/lib/dpkg/info/xserver-xorg-input-wacom.list
/var/lib/dpkg/info/xserver-xorg-input-wacom.postinst
/etc/init.d/xserver-xorg-input-wacom
/etc/rc4.d/S10xserver-xorg-input-wacom
/etc/rc3.d/S10xserver-xorg-input-wacom
/etc/rc5.d/S10xserver-xorg-input-wacom
/etc/rc2.d/S10xserver-xorg-input-wacom
/etc/udev/rules.d/50-xserver-xorg-input-wacom.rules
/lib/modules/2.6.20-15-generic/kernel/drivers/usb/input/wacom.ko
/usr/share/doc/xserver-xorg-input-wacom
/usr/share/doc/xserver-xorg-input-wacom/changelog.Debian.gz
/usr/share/doc/xserver-xorg-input-wacom/copyright
/usr/share/lintian/overrides/xserver-xorg-input-wacom
/usr/src/linux-headers-2.6.20-15-generic/include/config/usb/wacom.h
/usr/lib/xorg/modules/input/wacom_drv.so

---

### Post by jpeddicord on 2007-05-10
Don't worry about it loading the Wacom drivers. They are there to provide support for drawing tablets and tablet PCs if available/plugged in. Having them in the kernel will do nothing bad to your system. Unless they are causing problems, I highly recommend you keep them installed.


Jacob
UAResolved

---

### Post by strabes on 2007-05-10
I know what they do. I just think it's wasteful to load them on bootup since I don't have wacom devices anyway. Would it speed up my boot time if I were to get rid of them or just remove them from the boot process? How would I go about doing this?

---

### Post by jpeddicord on 2007-05-10
It probably wouldn't give you any significant performance increase. The Loading Wacom Drivers (or was it Tools?) stage of the boot process lasts not long enough to have an effect on the boot. Try booting in recovery mode and look for the Wacom step (if it is still in there) to see how fast it is.

Plus, if you remove the Wacom drivers, you will end up removing ubuntu-desktop, which can cause dependency problems when you upgrade in the future. They take up no more space (or boot time) than any of the other X drivers, such as SiS, ATI, and such, which are all loaded into the X server.

Jacob

---

### Post by strabes on 2007-05-10
ok, sounds good.

---

### Post by louistan3 on 2007-05-10
im not sure if this removes the wacom tools.. but i removed all the wacom entries on my xorg.conf file... and actually decreased my boot by about 2 secs... pretty good improvement for me coz i like fast bootups... lol

i think my laptop does not load the wacom stuff at bootup anymore thats why its faster.. 

hope this helps.. :)

---

### Post by strabes on 2007-05-10
Yep, I've had that stuff out of my xorg.conf for months now. Doing that also gets rid of errors when running apps. You can see the errors when you run apps from terminal. I didn't know it would speed up my boot significantly though. I use a verbose boot so it still says that it's loading them but it's not really causing me much distress. I just wanted to know if anyone knew a simple way to disable them.

---

### Post by liquidarts on 2007-07-24
Not sure where you are with this now, but I also see them in my /etc/rc5.d folder, which means they are loading on bootup.  You may want to check if they are there.

---

### Post by pikul on 2007-07-26
> **louistan3 said:**
> im not sure if this removes the wacom tools.. but i removed all the wacom entries on my xorg.conf file... and actually decreased my boot by about 2 secs... pretty good improvement for me coz i like fast bootups... lol

i think my laptop does not load the wacom stuff at bootup anymore thats why its faster.. 

hope this helps.. :)

I removed the wacom stuff from my xorg and X stop loading :lolflag: i had to restore my xorg.conf.bk to let it all the same, did you do anything else to make it work ?

---

