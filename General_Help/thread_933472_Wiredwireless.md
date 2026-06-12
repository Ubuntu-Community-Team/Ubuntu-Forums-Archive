---
title: "Wired/wireless"
date: 2008-09-29
forum: General Help
---

### Post by papabill on 2008-09-29
My machine has both wired and wireless networking. I have installed the wireless drivers and they work, but when I reboot, the wired network takes over. If I disable it, I have no networking at all.

How do I make my wireless load by default?

Thanks

---

### Post by ibuclaw on 2008-09-29
Are you **using** the wired network for anything?

The most sensible reply would be to disable the RJ45/RJ11 port in your BIOS.

But, there is another way.

```
sudo gedit /etc/network/interfaces
```
And either comment out "auto eth0" or replace it with "auto your-wireless-device-name-here0"

Regards
Iain

---

### Post by oldsoundguy on 2008-09-29
unplug the wired connection.  then go to system>administration>network
Turn off the wired connection there.

---

### Post by papabill on 2008-09-29
> **tinivole said:**
> Are you **using** the wired network for anything?

The most sensible reply would be to disable the RJ45/RJ11 port in your BIOS.

But, there is another way.

```
sudo gedit /etc/network/interfaces
```
And either comment out "auto eth0" or replace it with "auto your-wireless-device-name-here0"

Regards
Iain

All it says is:```

auto lo
iface lo inet loopback
```

---

### Post by papabill on 2008-09-29
> **oldsoundguy said:**
> unplug the wired connection.  then go to system>administration>network
Turn off the wired connection there.

And when I do that, I have no network at all unless I manually connect to the default wireless network (and I thought Fedora was a pain in the a**)

---

### Post by oldsoundguy on 2008-09-29
no expert on the vagaries of various wireless cards as I did my research and bought wireless cards that were shown to work out of the box with Ubuntu builds.

But it sounds to me like your wireless card is not actually working and your computer is using the wired connection.

in terminal: lshw

and see what wireless card is shown (make and MODEL if possible).  Maybe somebody can help you get the thing working correctly.  It may take several steps including installing a program called ndswrapper and then installing the WINDOWS driver in that wrapper.  Who knows?

---

