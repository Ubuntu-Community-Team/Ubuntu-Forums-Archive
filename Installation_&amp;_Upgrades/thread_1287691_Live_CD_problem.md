---
title: "Live CD problem"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by Trisztanhun on 2009-10-10
Hi!
When I insert the live CD of Ubuntu 8.10, everything goes right, and when i choose start or install ubuntu it loads up. After its loaded thought my screen goes black, and my monitors' led starts blinking orange and green. After, like 30 seconds I hear the login music of ubuntu, so I think its my graphic card whats not supported. My graphic card is a : ATI radeon HD 3850 (Gainward publisher). My ram is 1 gb, and my CPU is an AMD athlon 64 bit 3800+ (with ~2400 MHZ). 

The other thing is, that i downloaded the 9.04 version of ubuntu, and beacause of lacking blank CD's I decided to install it from a USB flash drive. I used LOADS of methods, but i couldnt get it to work. The main problem was, when I started the computer and plugged in the flash drive everything froze up, until I plugged it out. My motherboad is an : ASUS A8NE-FM.

Please help :D

Cheers.

Tristan

---

### Post by alexandermdevereux on 2009-10-10
try turning the computer off and putting the flash drive in. Then go into the bios boot menu and select usb. If usb isn't there then you can't boot from usb

---

### Post by raymondh on 2009-10-10
> **Trisztanhun said:**
> Hi!
When I insert the live CD of Ubuntu 8.10, everything goes right, and when i choose start or install ubuntu it loads up. After its loaded thought my screen goes black, and my monitors' led starts blinking orange and green. After, like 30 seconds I hear the login music of ubuntu, so I think its my graphic card whats not supported. My graphic card is a : ATI radeon HD 3850 (Gainward publisher). My ram is 1 gb, and my CPU is an AMD athlon 64 bit 3800+ (with ~2400 MHZ). 

The other thing is, that i downloaded the 9.04 version of ubuntu, and beacause of lacking blank CD's I decided to install it from a USB flash drive. I used LOADS of methods, but i couldnt get it to work. The main problem was, when I started the computer and plugged in the flash drive everything froze up, until I plugged it out. My motherboad is an : ASUS A8NE-FM.

Please help :D

Cheers.

Tristan

Hello Tristan and welcome.

This is assuming that the CD has been checked for defects (one of the options) and that the [MD5]("https://help.ubuntu.com/community/HowToMD5SUM") matches.

- You can try "safe graphics mode" (press F4 to get this option)
- You can try an [ALTERNATE ]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")install which is text-based instead of GUI
- You can even try 8.04 Long-Term-Support (LTS) hoping that in 8.04, your graphic card was still supported.

I am not familiar with the LOADS method, sorry.

Regards,

---

### Post by presence1960 on 2009-10-10
> **raymondhenson said:**
> hello tristan and welcome.

This is assuming that the cd has been checked for defects (one of the options) and that the [md5]("https://help.ubuntu.com/community/howtomd5sum") matches.

- you can try "safe graphics mode" (press f4 to get this option)
- you can try an [alternate ]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")install which is text-based instead of gui
- you can even try 8.04 long-term-support (lts) hoping that in 8.04, your graphic card was still supported.

I am not familiar with the loads method, sorry.

Regards,
+1

---

### Post by presence1960 on 2009-10-10
for safe graphics mode hit F4 when you get this screen

see [here]("https://help.ubuntu.com/community/BootOptions") for more detailed info on boot options for Live CD

---

### Post by presence1960 on 2009-10-10
> **alexandermdevereux said:**
> try turning the computer off and putting the flash drive in. Then go into the bios boot menu and select usb. If usb isn't there then you can't boot from usb

also look under hard disk boot order. Some flash drives show up there also. Then change the flash drive to boot first if it is in there. When you are finished with the flash drive and remove it your hard disk boot order will revert to the way it was initially.

---

