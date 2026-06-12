---
title: "Problem with HP DV6, eSATA, WD Green 2TB"
date: 2011-05-18
forum: Hardware
---

### Post by comicus on 2011-05-18
Hey all, it's been a while since I've had the urge to install Ubuntu, but yesterday, after seeing release notes for 11.04, I couldn't help myself. Everything seems to be working fine EXCEPT my external drive on eSATA. I'm dual-booting, and I can't boot into Ubuntu with the device connected via eSATA. It's a eSATA/USB docking station, and when it's connected via USB everything works, but eSATA is literally a non-starter. eSATA works fine in windows7, so I know its no a connectivity issue. If I try to plug in the device via eSATA after boot ubuntu doesn't seem to do anything... Nothing in the disk manager, nothing in scsitools, nothing in gparted... I've been browsing and browsing all night to try to find a solution, but nothing will get the device recognized. I should note that I used the Wubi install, could that make a difference? I'm willing to make some space and give Ubuntu its own partition but I was hoping to have all my problems resolved before I did that.

Any suggestions?

---

### Post by comicus on 2011-05-18
Also, I tried connecting with both the USB AND the eSATA cables plugged in. It won't recognize the drive until the eSATA cable is unplugged, and then it detects it almost instantly!

---

### Post by comicus on 2011-05-24
well I got it working, somehow...

Made a 100gb partition, did a fresh install. Booted up great with the device unplugged. Plugged in the dock, turned on the dock, put in the drive. Showed up in disk manager and mounted it from there!

---

### Post by ILoveYorkies on 2011-05-26
[SIZE=3]Congrats on solving your problem and thanks for explaining how you did it. I'm it will help other too.:)[/SIZE]

---

