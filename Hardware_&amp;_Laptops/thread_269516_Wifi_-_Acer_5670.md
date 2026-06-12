---
title: "Wifi - Acer 5670"
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by Migrator on 2006-10-01
Hi!  I've just started the long haul towards linux.  I've been testing it on a desktop for quite a while then I decided to convert my Windows laptop to a dual-boot with Kubuntu 6.6.

Everything was ok so far wifi, bluetooth etc.  Although I never got around to test the sound.  However, after I updated the entire system using Synaptic, my Wifi stopped working altogether.  It doesn't seem to start properly when I turn on the laptop and once it is turned on, I can't use the switch in front to turn on the hardware.  When I switch back to my Windows partition the wifi still works though, so I know the hardware is still working.

Any ideas?

Oh yeah and my sound system isn't working either, but I gathered from the previous posts that its a known problem so I'll just update myself from there..

---

### Post by dyous87 on 2006-10-02
Hmm that's odd, I have the same laptop running Ubuntu 6.06 and the sound and wireless both work fine and have been so for a couple of months now. Open up a terminal and type in:
```
ifconfig
```

post your output here for me to see it.

--DAVE

---

### Post by kelvin_team on 2006-11-06
Hi there my acer 5670 also work fine with the ubuntu 6.06, wifi is work very well. Maybe u have to turn on the wifi using the front panel wifi button, since my system also some times not automatically run the wifi. Hope can help.

Kelvin.

---

### Post by scifan2 on 2007-01-24
For the wireless - since your running kubuntu, you'll want to install knetworkmanager just because it makes things easier to work with - especially if your using WPA.

For your sound, I'd check the kmixer window to ensure things are turned up... also, you'll want to right click on your kmixer icon and select your master channel and change it to the "Front channel" so that your key's will run the correct audio channel set... :)

---

### Post by lbelmond on 2008-02-16
=^.^=

---

