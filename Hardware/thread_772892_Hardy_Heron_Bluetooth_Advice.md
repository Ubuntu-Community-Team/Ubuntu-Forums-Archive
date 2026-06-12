---
title: "Hardy Heron Bluetooth Advice"
date: 2008-04-28
forum: Hardware
---

### Post by justtech on 2008-04-28
Anyone able to direct me in the right direction with setting up a solid bluetooth connection with my computer and mouse/keyboard.  I've followed all of the tutorials that I could find.  I have added them to my /etc/bluetooth/hcid.conf.  Tried to add it to my bluez-utils in Hardy... no go.  

My problem is not when my computer boots up.  I have more of a problem when I leave my computer alone anywhere from 5mins - overnight.  Sometimes both the keyboard and mouse are still working but 50% of the time, it is not.  I have tried to create a bash script that runs a terminal command (sudo hidd --connect 00:07:61:48:14:ca) I can just double click on with a wired mouse but that requires me to type in my sudo pass.  I am just trying to find a way to eliminate having to keep a wired keyboard and a wired mouse hooked up to the computer at all times.  Of coarse, the keyboard is the worst to have because it's bigger and in the way.

If anyone can come up with a solution or point me in the right direction, it would be HIGHLY appreciated.

---

### Post by justtech on 2008-04-29
Anyone?

---

### Post by olivero1 on 2008-05-28
This worked for me:

[http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html)

It took me an hour to get it all working - but it is all solid now:)

---

