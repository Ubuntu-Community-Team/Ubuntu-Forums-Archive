---
title: "Gutsy killed my network connections"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by drinkingbird on 2007-10-19
I've just upgraded to Gutsy on a Toshiba Portege M200, and both my wired and unwired network interfaces have disappeared.

They can be seen in the device manager, but the gnome network manager doesn't seem to know anything about them.

The wireless device is just the basic Intel 2200BG interface, and I assume the wired controller is just something generic pressed by the million.

I also can't get the bluetooth device to pop up. It's as if Gutsy doesn't want to know anything about communication with the outside world.

Is this just something stupid in a random config file?

Edit: I just checked things out, booting the laptop into Windows, and all 3 network devices are fine there.

Second Edit: I can get the wired connection to work, but both wifi and bluetooth are still cactus.

---

### Post by drinkingbird on 2007-10-20
Well, I found a solution to this.

For some reason, the 386 version of the newly upgraded kernel didn't provide support for my wifi and bluetooth cards.

The generic kernel did though (although it gave me a bunch of X config grief, which took a bit of sorting out).

Weird.

---

