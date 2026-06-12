---
title: "X server fails to open on my ATI Radeon X1200 graphics card."
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by missingno on 2007-08-30
I just got a Toshiba Satellite A215-S4697 laptop, and I'm trying to set up a dual boot system. When the X server tries to launch, it fails with the message 'No screens found'. I've tried editing the settings via [FONT="Courier New"]sudo dpkg-reconfigure xserver-xorg[/FONT], and haven't been able to find the right configuration to startx successfully. I either get the same error message, or 'Caught signal 11'. Does anyone know what the right settings are for my graphics card, ATI Radeon X1200?

---

### Post by missingno on 2007-09-01
I found what appears to be a solution [in this sticky]("http://ubuntuforums.org/showthread.php?t=414194"), but unfortunately I can't connect to Ubuntu's servers to get the update since the driver for my wifi isn't working either. What now?

---

### Post by kjg1981 on 2007-09-01
The internet should work fine if you can physically plug it in to your router.  Worked for me.

---

### Post by missingno on 2007-09-01
I tried an ethernet cable, and that didn't seem to work either. I'm stumped as to what to do.


Is it possible to simply download the driver fixes onto a USB stick/burn to a CD/etc and open them up locally, or will I need to get the bash shell to connect directly to the update servers online?

---

### Post by GraFfiX420 on 2007-09-16
Did you try to :
  sudo ifconfig eth0 up
  sudo dhclient eth0

?

---

