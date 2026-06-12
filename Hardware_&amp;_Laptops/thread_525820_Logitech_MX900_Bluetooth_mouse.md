---
title: "Logitech MX900 Bluetooth mouse"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by pbalir on 2007-08-14
I'm a week into using Ubuntu, and have most things working. Except this mouse!!

I have a Logitech wireless keyboard that works out of the box. But the mouse is on a second receiver, and only works if I unplug/replug it after booting. Of course, by that time, pressing the Connect button etc is a waste of time!

lsusb shows that it exists...but pcitool scan reveals nothing. I've worked thru the forums trying to get it together.

The main changes I made are in /etc/bluetooth and /etc/default/ but still no joy. From what I can read, this is a rather unusual situation.

Regards

Paul

---

### Post by pbalir on 2007-08-23
Well, I decided that the later version, 7.10, currently in beta, might have solved the problem of Blutooth mice. So I downloaded it and set it up.

Sad to report, it did no better than 7.04 - the mouse simply was not recognized.

Please, someone, tackle this deficiency....

Paul

---

### Post by wieman01 on 2007-08-24
There is a Logitech bluetooth thread somethere in the forums. Have you check that out yet?

---

### Post by pbalir on 2007-08-24
Yes, I've tried all the solutions offered. The mouse remains unconnected.

I've also looked at the bug reports, and it seems that I'm standing in a long queue of people with the same or nearly identical problem. SuSE can find the mouse, but not Ubuntu :(

Paul

---

### Post by romeyde on 2007-11-12
Did you ever find a fix for this?   I started using Gutsy last week and all in all, love it.  But...   While I was very impressed at how well it did at detecting and setting up my hardware,  this flipping mouse is driving me crazy.

I have the exact same issue.   My Logitech MX900 mouse just won't work on boot up.   I end up having to unplug it, plug it back in, then resync the bluetooth to get it to start responding.  Also, I noticed that if I just leave it as is, plug a cheap usb mouse in that I have laying around (which works right away) and then unplug the usb mouse, my MX900 starts working.   Real pain.

Searched the forums and tried several "fixes" but nothing seems to help.

This and the suspend issue are the only ones I'm dealing with.  Which, granted, compared to linux in the early 90's when I first started messing with it, is amazing.

---

### Post by steveneddy on 2007-11-12
I've found that trying a different USB port seems to work well for me.

---

### Post by pbalir on 2007-11-12
Yep, I found a fix. Not what I expected, but it works in 7.04 and 7.10

Open a terminal window, get root access and type "apt-get remove bluez-utils"

How easy was that!

Regards

Paul

---

### Post by romeyde on 2007-11-12
Woohoo...   Only tried one full reboot after removing the package but it appears to have worked.
Thanks much.

---

### Post by pbalir on 2007-11-12
Yay!

I guess you no longer have a Bluetooth mouse, just a working one :)

Paul

---

### Post by romeyde on 2007-11-12
Now if I could just get my buttons all working right.  :)   For some reason, the top one on the left side is detected as a right mouse click instead of a unique button.   In windows, these two buttons allowed me to go back and forth in history in Firefox.  Not a huge hassle really and something I certainly can learn to live with.

---

