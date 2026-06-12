---
title: "ATI Rage mobility M3"
date: 2009-10-23
forum: Hardware
---

### Post by dburr96 on 2009-10-23
Have a Dell C600, installed Ubuntu 9.04, graphics are 800x600, should be much better. How 't assume do I fix this? I am not very savvy with PC's so please explain in plain terms. Don't assume I know what I'm doing, hahaha, thanks

---

### Post by dvlchd3 on 2009-10-23
Not completely familiar with that ATI card.  I know my ATI Radeon Xpress 200M does not require restricted drivers as of 9.04, however, check System -> Administrator -> Hardware Drivers and see if there is a restricted river available (should be fglrx) for your graphics card.

If enabled, or not listed, attempt the following:
System -> Preferences -> Display -> see if you can increase the resolution.

---

### Post by dburr96 on 2009-10-25
Hello, and thanks for the reply. I have tried both of those suggestions and there isn't any drivers listed at all for my machine, and I am not able to improve the resolution beyond 800x600, or 640x480

---

### Post by dvlchd3 on 2009-10-26
I couldn't seem to find your card listed, but try going to the site below and download the drivers directly from ATI.  ATI has been attempting to provide more linux support for their cards, however, be warned, when I attempted this process on my Desktop, it crashed X Windows, therefore leaving me with no GUI...

You may have better luck:

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

(Make sure you select Linux x86 for 32-bit or Linux x86_64 for 64-bit)

---

### Post by Yellow Pasque on 2009-10-26
DO NOT download drivers from ATI for this GPU. This chip is an old Rage128-based chip and isn't supported by fglrx/Catalyst. It is supported by the xserver-xorg-video-r128 driver. If it's not working right, look at /var/log/Xorg.0.log and figure out why. Since the r128 driver is pre-installed, it's probably an issue with X not detecting resolution correctly.

---

### Post by masud tarek on 2010-02-13
first try to edit xorg.conf file under /etc/X11
value of horizontalsync rate 31 -55 or more(75)....
colordepth 16 ...
edit resolution ranges under 'monitor' section
 
 
if the file is empty or no file, do the following things:
on the dell site, go to your laptop's driver section and select os type=linux
hopefully you will get a red hat linux ATI driver - .rpm
download it.
 
On ubuntu or xubunto, install Alien
with this package you can convert the .rpm file to .deb
 
install the .deb driver, now under /etc/X11 you will get XFconf......  file
 
Open it to edit,
change the defaultdepth 24 to 16 ....
hope, this will work for you ...atleast, for me it worked

---

### Post by waynefoutz on 2010-02-13
I had the laptop a few years ago, I had Gutsy (7.10) installed on it. I used the catalyst driver, But I doubt the latest Catalyst driver will support it, ATI dropped linux support on just about all their older cards.

---

### Post by 00b00nt00 on 2010-02-13
Strange... I had a Compaq Armada E500 with a Rage Mobility P/M card and it worked fine out of the box. No compiz, though, which was to be expected. Something is wrong in the Xorg...

---

