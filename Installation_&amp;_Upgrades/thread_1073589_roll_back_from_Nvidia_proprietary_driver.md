---
title: "roll back from Nvidia proprietary driver"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by v1nsai on 2009-02-18
I had a really bad experience last time I tried to upgrade from the Ubuntu open source nvidia driver to nvidia's driver that they have on their website, I ended up reformatting my whole partition.  Anyway, I have an earlier version of the driver and I want to try again, video performance is pretty wanting with just the open source nvidia driver.  In case it hits the fan again, how can I roll back to the open source driver again?

---

### Post by whoop on 2009-02-18
What ubuntu version are you using? Why not consider using the recommended hardware drivers? System-->Administration-->hardware drivers

---

### Post by v1nsai on 2009-02-18
Yea that's what I meant by open source drivers, that's what I'm using right now.  I can barely watch video in full screen, and this machine has more than enough power to push it and does so just fine in windows, so I figured it was the driver.

Just worried about another disaster, last time I did it my 22" LCD would only display in 640x480 o_0 .  I heard on the Nvidia forums that the driver I downloaded was pretty unstable and that the previous version was a lot better, but I still would like to know how to undo any changes I make.

---

### Post by whoop on 2009-02-18
Then consider using envy(ng): [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by v1nsai on 2009-02-18
Seems pretty foolproof, I'll give it a shot thanks :)

Just for reference though, is a specially written program the only way to roll back a driver?

---

### Post by pgatrick on 2009-02-18
If your monitor was only in 640x480 you probably just needed to add the proper resolution to your xorg.conf. Also, if the nvidia driver doesn't work right, just switch 'Driver    "nvidia"' back to 'Driver    "nv"' or vesa or whatever in your xorg.conf.

---

### Post by v1nsai on 2009-02-23
If I made a backup of xorg I could just roll back to that couldn't I?  I remember playing around with xorg a little bit but I wasn't having any luck, it was pretty ugly so I ended up nuking the partition.

---

