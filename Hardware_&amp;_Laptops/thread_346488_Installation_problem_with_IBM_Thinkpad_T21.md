---
title: "Installation problem with IBM Thinkpad T21"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by stevos on 2007-01-25
Has anyone managed to install Ubuntu on a Thinkpad T21?
I notice the T23 is included in the hardware compatability list but I can't get my T21 to start with 6.06 or 6.10.
When booting the following message appears -

       piix4_smbus 0000:00:07.3  IBM laptop detected. This module my corrupt your serial eeprom.
       Refusing to load module.

Win XP works fine on this machine.

800MHZ P3
256 MB
I have successfully installed both versions on a Compaq Armada M700.

---

### Post by exad on 2007-01-25
I recently installed kubuntu 6.10 on a T21(800mhz 512MB).  Boots successfully from both the CD and the hard drive.

Its a nice linux machine, the power management (suspend and hibernate) and the volume controls on the keyboard work without any hassle.

Dmesg shows that same message, the next line:
piix4_smbus: probe of 0000:00:07.3 failed with error -1

---

### Post by stevos on 2007-01-26
I have now tried 5.04 and it worked with no errors reported.
Of course I can't get any updates for this though!

Guess I'll have to keep trying.

---

### Post by PolarBear64 on 2007-11-19
I am currently installing 7.10 on a T21 I was given.

I am stuborn and just ignored the fact it gave me the eprom error deal.

it took about 6 tries rebooting when the install seemed to stop but now it is at the installing system screen.

will add more later when I have seen how its performing.

Edit - well the install failed then I retried using the OEM installer and it worked great. 


800mhz cpu, 256M ram, 15G HD.

---

### Post by PolarBear64 on 2007-11-28
Well been using 7.10 for a week now with no problems on the T21 except sometimes the video does not seem to initialize and I have to try booting about 4 or 5 times before the video will work after the initial ubuntu splash screen.

---

