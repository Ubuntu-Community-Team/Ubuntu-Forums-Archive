---
title: "Where to start with a TV remote"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by jc508 on 2007-08-25
:confused:Hi,
I would like some help please in setting up a remote control - slowly please as I cant tell a gpio from a lirc!.
The machine is running Fiesty and the TV is working - MythTv up and running

The remote came with a DViCO Fusion Dual Digital 4 HD Tuner and the DViCo site says the package has a "Fusion MCE Remote Control"

Armed with only this info I have been searching and getting confused with how many components lirc has etc.  Eg Licr has to be compiled vs No it just has to be configured;
It looks like there are some assumptions made about the hardware that I think I haven't got right yet.
Many posts say to run cat /proc/bus/input/devices and look for 'event n'  - when I do this I don't see anything like the device.
Conversely if I issue lsusb I get
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0fe9:db78 DVICO 
Bus 002 Device 002: ID 0fe9:db78 DVICO 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
My guess is that the remote is coming in on Usb Bus 002 Device 001 as that would put it on the same card as the tuner.

Do I have to do something to get it appear as an input device ?  Can lirc just 'see' the usb?

Then when you get tangled in lirc you get to choose mceusb2 or mceusb how on earth do you know which to use?  I have tried to look inside to see chips etc but the thing is glued together!

Thanks
JC

---

### Post by newlinux on 2007-08-25
is it this remote:

[http://www.overclockers.com.au/wiki/Image:Dvico_remote.jpg](http://www.overclockers.com.au/wiki/Image:Dvico_remote.jpg)

If so, I believe the versions of the of the LIRC in the ubuntu repos has support for this device without patching.

---

### Post by newlinux on 2007-08-25
You can get the lircd.conf from here:

[http://lirc.sourceforge.net/remotes/dvico/](http://lirc.sourceforge.net/remotes/dvico/)

According to the [http://www.lirc.org/html/table.html](http://www.lirc.org/html/table.html) it uses the dvico driver and doesn't need a kernel module.

---

### Post by jc508 on 2007-09-09
Thanks for the help (been diverted with work last two weeks!)
I am not outof the woods yet but will post afresh

---

