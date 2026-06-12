---
title: "Medion Laptop - Keeps going back to login screen"
date: 2018-11-09
forum: Hardware
---

### Post by nalberto on 2018-11-09
I installed ubuntu to a cheap Aldi laptop Medion E4242

There is an issue with the built in intel graphics card.

If I boot in recovery mode 800x600 then all is good and it behave as it should. But if I boot normally it keeps going back to a black screen after 20 seconds. I then have to press the space bar and I get the login screen, login and then again 20s.

I only has ubuntu on it.
Not sure if it helps but here some info collected from boot-repair
[http://paste.ubuntu.com/p/rp5N7xBfNc/](http://paste.ubuntu.com/p/rp5N7xBfNc/)

It does not seem to recognise the intel graphics card from the settings screen.

Any idea?

---

### Post by ajgreeny on 2018-11-09
What hardware does that machine use; it is difficult to help with no information about that?

---

### Post by nalberto on 2018-11-21
I found the solution. For some reason ubuntu seems to get the signal that the screen is closed and therefore goes to sleep mode.
I installed gnome-tweak-tool which allowed me to switch off the function that tells the laptop to go to sleep when screen is close. That was bit of a trial and error to find this but it now works perfectly.

In recovery mode the laptop was working fine. That may help someone with a similar issue.

I also had to wipe all partitions on disk before installing ubuntu because the bootloader was corrupted.

---

