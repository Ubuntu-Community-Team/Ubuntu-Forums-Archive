---
title: "HP ZE4300 suspend/resume troubles"
date: 2006-05-04
forum: Hardware &amp; Laptops
---

### Post by jiggahertz on 2006-05-04
I'm trying to sleep/resume on a hp ze4300 using vesafb for an ati radeon card.  Using the default sleep.sh script in the /etc/acpi directory - laptop goes to sleep fine.  But on resume the screen doesn't turn on, keyboard is frozen (caps lock blinking), no power to usb mouse.  I also added the DPMS option in xorg.conf and VBREstore 1.  I've tried various suspend scripts, sleep levels, etc, and seeing the same behavior. 

Thanks,
JH

---

### Post by nixmega on 2006-05-05
[QUOTE=jiggahertz]I'm trying to sleep/resume on a hp ze4300 using vesafb for an ati radeon card.  Using the default sleep.sh script in the /etc/acpi directory - laptop goes to sleep fine.  But on resume the screen doesn't turn on, keyboard is frozen (caps lock blinking), no power to usb mouse.  I also added the DPMS option in xorg.conf and VBREstore 1.  I've tried various suspend scripts, sleep levels, etc, and seeing the same behavior. 

Thanks,
JH[/QUOTE]

I'm on a ZE4220 and over two years, I've never had luck with suspend. Oh yeah, try the Mobile U1 graphics driver :).. the IGP 320M in these notebooks works well under it. It'll run a little hot though, because of the annoying shared memory issues. (I think the ZE4300 series has IGP chipset as well, may want to check on that.) Sorry I couldn't be much help.

---

### Post by snipe122 on 2006-05-06
if you have incompatible notebooks, you should try different kernel options...

you only have troubles with standby or with hibernate as well? I just made my notebook hibernating a few days ago, so maybe I can help you a bit with that...


greetz

snipe

---

### Post by nixmega on 2006-05-10
Me Again... reconfiged my kernel. I now have hibernate and suspend support. I can help you if you're still around.

---

