---
title: "Asus EeePC 1000H + Holux GPSlim240 : Host is down"
date: 2008-12-13
forum: Hardware
---

### Post by jbatista on 2008-12-13
Dear all,

I'm managing to get (mostly) everything in my EeePC 1000H with Intrepid (8.10). One of the things I'm attempting is using a GPS receiver (Holux GPSlim240) running in Linux.
* The netbook can see the GPS receiver with hcitool scan.
* I couldn't register the GPS with bluetooth-wizard, because the default pincode is "0000" and not "1234". I downloaded the bluez-gnome source and changed wizard/main.c funcion "pincode_callback" to accept "0000" as default pin code, ran it in place (didn't install the Deb package) and customized bluetooth-wizard accepted the device. The default bluetooth-wizard also sees it.

But it still seems I can't connect to it. I edited the /etc/bluetooth/rfcomm.conf to add the new device, and /dev/rfcomm0 does come up. However, doing a simple cat /dev/rfcomm0 gives the message:
cat: /dev/rfcomm0: Host is down
With another nearby system (different hardware, Debian-derivate) I'm still able to get the regular NMEA output expected with the command above.

I've set the pincode, and I see the device in /dev. Everything should be working now, but I either forgot something or did something wrong. 

I appretiate any help you might spare!

Cheers,

---

### Post by jbatista on 2008-12-16
Anyone? :confused:

---

### Post by jbatista on 2008-12-17
Following the steps described here:
[http://blogs.srijan.in/2008/01/19/bluetooth-gps-devices-with-linux](http://blogs.srijan.in/2008/01/19/bluetooth-gps-devices-with-linux)
I managed to get NMEA sentences from the GPS unit. :) It turns out I had to unbind the /dev/rfcomm0, run this command as normal user (or as root):
```

sdptool add --channel=1 SP

```
to add a Serial Port link to channel 1, and then bind the rfcomm0 device to the GPS MAC.

I was expecting that the "sdptool" instruction was unnecessary. I have a Debian backport installation in another computer and it works "out of the box". 

Would anyone more knowledgeable about Bluetooth in Linux care to explain why sdptool isn't supposed(??...) to be ran automatically, or at least point me to some relevant literature on the subject?

Thanks in advance. :wave:

---

### Post by firemann816 on 2009-01-03
Hey thanks for the good write up -
my pincode on my globalsat is 0000
and it wont pair successfully -

I cant help with your issue, a forum search for 'gps' returns your posts and it is helpful.
Intrepid didnt have sbsd included.

also
I dl'd package btscanner via synaptic and it helped me ensure I was okay on the bt dongle and rf side of things.

Cheers & Thanks, :popcorn:
-a

---

