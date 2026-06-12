---
title: "Turn off Dell trackpoint"
date: 2008-12-29
forum: Hardware
---

### Post by Cl0ud9 on 2008-12-29
I am having problems with the trackpoint on my Dell latitude causing the mouse to drift. I would like to turn it off without removing the keyboard and unplugging the wire. I have tried using synclient and setting GuestMouseOff = 1, but this does not work. Any helpful suggestions on how I can solve this trackpoint problem would be greatly appreciated.

---

### Post by New life on 2009-02-23
Hi Cl0ud9,

The reason I found it can never be solved by software is that the trackpoint and the touchpad share the same hardware. I managed to disable the trackpoint by changing the xorg.conf, but the drift came back soon. It was only when I unplugged (no need to cut) the 4-wire flatcable of the trackpoint that the problem was solved. It's really worth the effort. It takes only 10 minutes if you know how to handle the small connector that connects both the keyboard and the trackpoint. The screws to free the keyboard are marked with a (K). The plastic above the keyboard can be opened by pulling a little bit on the right side. Good luck !

---

### Post by ZeroFossilFuel on 2012-01-15
I'm resurrecting a Dell Latitude for my wife and ran into exactly this same problem. Removed the trim plate at the base of the LCD, 5 screws marked K from the bottom and the keyboard lifted right out. Pulled the ribbon cable connector from the mobo. The connector head has two clips (one at each end) that hold the ribbons in place. A small jewelers screwdriver is all that's needed to release the clips. The back slides off and the TrackPoint ribbon pulls out easily. Snapped it all back together and voi-la!

---

