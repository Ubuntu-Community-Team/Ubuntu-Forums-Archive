---
title: "USB Stops Working Randomly."
date: 2008-11-08
forum: General Help
---

### Post by Roasted on 2008-11-08
My buddy called me tonight. I got him hooked on Ubuntu Intrepid last night. Now he's bummed because his USB ports stop working randomly, when he's not even doing anything. This is especially annoying to him because he uses a wireless USB adapter... so when USB stops, his connection is fried...

Here's a hardcore computer guy who fell in love with Ubuntu overnight who suddenly can't do a damn thing due to this bug, or whatever it is.

The weird thing is, his usb mouse works fine through it all. Yet flash drives, wireless devices, etc, all don't work.

Is there a fix for this?

---

### Post by Roasted on 2008-11-09
I talked to him more. He's been experiencing this problem in completely random times. Sometimes they'll stop working in 15 minutes after a boot, and the other day it was 12 hours that they stopped responding.

Flash drives don't respond, his 3Com wireless USB device (completely supported under Ubuntu, I have the same one) doesn't respond... yet his USB mouse works perfectly.

And I doubt that it's a lack of power problem, due to the fact his devices light up as normal. Nothing just comes about of them. He put his Kingston 2gb USB Flash Drive in, gparted showed nothing, fdisk -l showed nothing, he just doesn't have anything responding when the system starts acting like this.

Yet he can be logged into XP for days on end and there's no issues whatsoever.

---

### Post by PmDematagoda on 2008-11-09
Just after a USB device stops working properly, can you get the output of:-
```
dmesg | tail -25
```

---

