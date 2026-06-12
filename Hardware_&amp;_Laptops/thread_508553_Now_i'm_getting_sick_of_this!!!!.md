---
title: "Now i'm getting sick of this!!!!"
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by Leipe_Po on 2007-07-24
ok this is the situation:

1.) i tried the ubuntu 7.04 live on my laptop to confirm everything was working...
2.) everything worked, so i did a hd install...
3.) after first reboot, my wlan didnt worked...
4.) after the second one, still no go....
5.) after the 3th one, nope....
6.) after the 4th one... still no go!!!!!

now i must be loosing my balls here, the claim that stuff worked on the live cd, will work when installed is just a bunch of crap then, cause i did nothing at all on the config!@

i'm just seconds away of going crazy!

its a intel wireless card on a compaq presario v4000....

thanks for any suggestion....

---

### Post by Circuit99 on 2007-07-24
I have one suggestion, while fiesty was installing were you connected to the internet and did the Ubuntu recognize your internet connection?


This my help

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_configure_network_connections](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_configure_network_connections)

and here

[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)


Good Luck   :popcorn:

---

### Post by ugm6hr on 2007-07-24
> **Leipe_Po said:**
> its a intel wireless card on a compaq presario v4000....


As far as I know, most intel cards work well.  That laptop came with Intel Wireless 2200BG (802.11 b/g) or Broadcom 802.11/b/g WiFi card, and the 2200BG is definitely well supported within Linux.  Although I think it can be confused between 2100 and 2200 chipsets sometimes.  If so, then perhaps a simple command will blacklist the IPW2100 driver to ensure it doesn't interfere.

The output from *lshw* should tell you what driver is being used, and *lspci* will confirm the chipset.
```
lshw
lspci
```

---

### Post by Ademi on 2007-07-24
Since your talking about disabling devices, does anyone know how to disable a device in ubuntu 7.04?

---

