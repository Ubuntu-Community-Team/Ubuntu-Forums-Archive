---
title: "2 Graphics cards, fglrx + fail"
date: 2010-02-17
forum: Hardware
---

### Post by jon.mithe on 2010-02-17
Hi,

I'm having trouble setting up 2 graphics cards with fglrx for 3 monitors 

The two cards are:

ATI Technologies Inc Mobility Radeon HD 3600 (PCIe x16) 
ATI Technologies Inc FireMV 2250 (PCIe x1)

I intend 2 monitors on the Radeon, and a 3rd on the Fire

They both "work", the bootup happens on Fire and then with the login screen it changes to the Radeaon (had troubles on the first run, so did an aticonfig --initial and it basically does the radeon).

lspci shows:

```

02:00.0 VGA compatible controller: ATI Technologies Inc FireMV 2250
02:00.1 Display controller: ATI Technologies Inc FireMV 2250 (Secondary)
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
05:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3600 Series

```

The catalyst control center (amdcccle) however does not recognise the Fire card.  So I have two screens off the radeon I can configure and the Fire card monitor is blank.  

In the "Information" section of catalyst, there is only mention of the Radeon.

running aticonfig --lsa (list all adapters) it only shows the Radeon.

I have tried various aticonfig commands to set up the xorg, but have failed, primairly "--initial" and "--adapter=all --initial=dual-head" in the hope that catalyst control center would pick up the other card I can work from there -- but no luck.

I then tried my own xorg.conf which had 3 monitor, 3 device and 3 screen settings, with xinemara on, it was based off of a triple head xorg someone posted, but I have lost the link. Booting up I only got the Radeon in cloned mode.

I am fast running out ideas now and wandering if anyone can help?

I can post up any details.

I'm running an dell i7 with 64bit 9.10, very standard install / nothing special.

Please help! :), thanks,

Jon

---

### Post by jon.mithe on 2010-02-18
Yeah, for anyone else having this trouble, it seems the FireMV is no longer supported by catalyst.

---

### Post by jon.mithe on 2010-03-03
the solution was simple in the end, buy 2 nvidia cards...

[http://ubuntuforums.org/showthread.php?p=8870801#post8870801](http://ubuntuforums.org/showthread.php?p=8870801#post8870801)

---

