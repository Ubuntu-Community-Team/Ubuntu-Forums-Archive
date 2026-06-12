---
title: "Laptop touchpad..."
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by ryantmer on 2007-07-01
I am using Feisty on an old Twinhead Slimnot VX, and I have a rather obnoxious problem with the touchpad, ie it doesn't work. I've searched all around the forums and Google, but nobody seems to have to same problem. I have added a section to my xorg.conf to enable synaptics touchpads, but it still doesn't work. Even more bizarre, when I do
```
cat /proc/bus/input/devices
```

I don't get anything about a synaptics touchpad. I do, however, get something about "Macintosh mouse button emulation", which does not seem to be very common... This has led me to the conclusion that my touchpad may not actually be synaptics.

Are there any other options to get this thing to work? Also, it should be noted that USB mice work, but I have not been able to get PS/2 one working yet.

---

