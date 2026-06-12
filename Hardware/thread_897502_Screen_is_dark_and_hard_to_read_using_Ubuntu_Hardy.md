---
title: "Screen is dark and hard to read using Ubuntu Hardy Heron on Dell Inspiron 1300"
date: 2008-08-22
forum: Hardware
---

### Post by tetristic on 2008-08-22
Hi-

I'm a newcomer to Linux, so please excuse any obvious idiocies on my part.

I'm using a Dell Inspiron 1300 laptop, which according to a google search uses a WXGA display. I've just installed Ubuntu Hardy after trying a few other distributions and failing to get them to work. 

The problem I'm having is this: under windows, the laptop used a power-saving technique whereby when it was running on battery the screen would be darkened slightly to reduce power consumption - when the power cable was plugged back in the screen would brighten up again.

After I installed Ubuntu the screen started switching seemingly at random between the two states. For a while it got lighter when the power cable was removed - the reverse of what it's supposed to do - but now it seems to have settled on a darkened display whether the power cable is in or not.

I've had a look through the forum but can't find any topics which cover it, and I've got absolutely no idea where to start! Any help would be greatly appreciated.

Thanks,

Russell

---

### Post by timcredible on 2008-08-22
not sure, but try system->administration->power management and see if any settings in there can fix the problem, maybe turn off power management.

---

### Post by tetristic on 2008-08-22
No luck I'm afraid, I tried playing around with the option to 'reduce backlight when idle' but to no effect at all. I can't see a way to completely disable power management though.

---

### Post by meijer.o on 2008-08-23
Dear user,

try adding the module video to /etc/modprobe.d/blacklist

command: sudo gedit /etc/modprobe.d/blacklist

add to the file:

blacklist video

Make sure that you have a empty line at the bottum of the file "blacklist"

restart your computer.


I hope for you that it works,

Kind regard,

A linux user

---

### Post by tetristic on 2008-08-23
Fixed! Thank you meijer.o!

---

