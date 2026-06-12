---
title: "Wacom serial tablet...what works?"
date: 2010-03-29
forum: Hardware
---

### Post by JAKEOTR on 2010-03-29
Hello everyone...I have a Wacom UD0608R Digitizer ll serial tablet. I have most things working but the stylus is still flaky (I'm using 9.10 64bit). I've tried everything and am aware of the filed bugs for this. I just need to get this working and it looks like 10.04 is not going to help. Can anyone tell me of other distros or older versions of Ubuntu (or anything for that matter) that work correctly with my tablet. I'll dual boot to another distro, use older versions of Gimp, whatever I have to do to get this operational. Please let me know of your successes, thanks

---

### Post by JAKEOTR on 2010-04-04
Anyone?... please

---

### Post by luminol on 2010-04-06
I'm using an old 12x12 Intuos serial tablet connected via a USB<->serial adapter (I highly recommend this). Works flawlessly in Jaunty (9.04).

The only way I've _ever _been able to get a serial Wacom tablet to work is by editing xorg.conf as described [here]("https://help.ubuntu.com/community/WacomTroubleshooting").

My USB dongle-with-wacom-attached shows up as a serial device on /dev/ttyUSB0, so I comment out (#) all the:

*Option        "Device"        "/dev/input/wacom" # USB ONLY?*

and

*Option        "USB"           "on"               # USB ONLY*

in xorg.conf.

I'm currently banging my head against Kubuntu Karmic with this very same problem. Hopefully it'll be better with Lucid, but I'm not holding my breath. If I make any headway, I'll post my results.

---

### Post by JAKEOTR on 2010-04-08
Thanks for the reply....I'll try putting 9.04 back on

---

### Post by luminol on 2010-04-10
Hope you haven't re-installed 9.04 yet. I finally thrashed something out here: [Installing a serial Wacom tablet in Karmic]("http://ubuntuforums.org/showthread.php?p=9102516#post9102516").

---

