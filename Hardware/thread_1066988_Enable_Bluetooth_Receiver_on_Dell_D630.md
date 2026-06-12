---
title: "Enable Bluetooth Receiver on Dell D630"
date: 2009-02-11
forum: Hardware
---

### Post by dernsber on 2009-02-11
Any ideas?... 

i've tried the airport-utility, but can't get that figured out...
It is enabled in BIOS...
I have thought about trying bluez, but wanted to wait and see if anyone has other ideas...

Thanks!

---

### Post by dernsber on 2009-02-11
Bump.....

---

### Post by ajmctaggart on 2009-02-11
Any idea what Bluetooth is installed?

should be a ```
lsusb
``` command

Also, Im sure you've Googled, but did you see this site...Hardy Heron not Ibex...

[http://pjhile.com/bluetooth-on-dell-d630-ubuntu-804-hardy-heron]("http://pjhile.com/bluetooth-on-dell-d630-ubuntu-804-hardy-heron")

I don't have Bluetooth on my Dell, so I don't think I'm much help...

Others with D630's report Bluetooth worked OTB, so I'm not sure what the problem is for you

Good Luck!

---

### Post by dernsber on 2009-02-11
I think i found the problem... when i originally had the laptop i had Windows on it with no Bluetooth, so i turned off the receiver through that... thinking that i should be able to turn it back on no matter what OS i have....

I then installed Ubuntu.. and from what i've read, you need to turn it back on with a windows only utility... yeah, suxor.. once that's done it works perfectly.

but i still rand the command you said:
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 006 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


And looked at your link... HIDD isn't even popping up... i'll try to figure that out...

Right now got 2 things trying... some Dell hardware apps and a Windows VM... if neither of those work, i'll just install windows, turn it on, then reinstall Ubuntu... :-)

---

### Post by ajmctaggart on 2009-02-11
You had Windows on it w/o bluetooth, so you turned it off???

You've definitely got bluetooth...so I'm not sure if you mean you just didn't want to use it so you shut it off?

At any rate, if you already deleted Windows, I doubt the VM will work, but it's not like I'm a guru, so who knows...

---

### Post by dernsber on 2009-02-11
didn't want to use it, so i shut it off... and yeah.. trying to figure out the aircraft-manager thing now... it installed but won't load when i run the settings... seems like its hanging on something...

---

### Post by ajmctaggart on 2009-02-11
[http://w3.ualg.pt/~aanjos/misc.html]("http://w3.ualg.pt/~aanjos/misc.html")

Thats a great resource for you and your Dell if you ever run into other troubles, not Ubuntu specific, but at least shows you what's possible...

I guess you're right about the bluetooth, I didn't realize you shut anything off in Windows before hand...

 [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/277211]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/277211")

Let us know what works...

---

### Post by dernsber on 2009-02-12
So.. installed windows, installed the Dell drivers, it turned on, installing Ubuntu now and it seems to be working perfectly... such a pain the ***....

But fixed now, enjoy!!!

---

