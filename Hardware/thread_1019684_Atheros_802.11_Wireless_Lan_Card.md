---
title: "Atheros 802.11 Wireless Lan Card"
date: 2008-12-23
forum: Hardware
---

### Post by Malvazar on 2008-12-23
Okay I got a weird problem that really needs to be fixed.
As you may have guessed I have a Atheros 802.11 Wireless Lan Card, I have it all set up and showing in the system, but I can't use it! 
It will search for wireless signals around my area, but nothing more than that. 
So I figured that I would go see if the drivers were enabled out of some weird flook that it wasn't. Well it wasn't so I tryed to enable it. It asked for a system restart, I did that. 
The system rebooted and I tryed to use the wireless again, no dice! So I go look at the drivers again and it still is not enabled nor will it enable regardless of how many time I tell it to enable. 
So what do you all think I need to do?
:confused::confused::confused::confused::confused::confused:

---

### Post by SuperSonic4 on 2008-12-23
What happens if you do ```
sudo modprobe ath5k
```

I used this guide: [http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html) and method 2

---

### Post by Malvazar on 2008-12-23
> **SuperSonic4 said:**
> What happens if you do ```
sudo modprobe ath5k
```I used this guide: [http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html) and method 2

I get this:
FATAL: Module ath5k not found.
Oh and it might help to tell you I am running on Ubuntu 8.04!

---

### Post by stchman on 2008-12-23
> **Malvazar said:**
> Okay I got a weird problem that really needs to be fixed.
As you may have guessed I have a Atheros 802.11 Wireless Lan Card, I have it all set up and showing in the system, but I can't use it! 
It will search for wireless signals around my area, but nothing more than that. 
So I figured that I would go see if the drivers were enabled out of some weird flook that it wasn't. Well it wasn't so I tryed to enable it. It asked for a system restart, I did that. 
The system rebooted and I tryed to use the wireless again, no dice! So I go look at the drivers again and it still is not enabled nor will it enable regardless of how many time I tell it to enable. 
So what do you all think I need to do?
:confused::confused::confused::confused::confused::confused:

Are you running Intrepid?  If so try this.

[https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One](https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One)

The new Intrepid backport modules have greater Atheros support.

If you are running Hardy you will need to install madwifi or use ndiswrapper, use the Aspire One 8.04 documentation.

---

### Post by Malvazar on 2008-12-23
> **stchman said:**
> Are you running Intrepid?  If so try this.

[https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One](https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Intrepid%20Ibex%208.10%20on%20the%20Acer%20Aspire%20One)

The new Intrepid backport modules have greater Atheros support.

If you are running Hardy you will need to install madwifi or use ndiswrapper, use the Aspire One 8.04 documentation.

nope still didn't work!
I already had ndiswrapper installed.
And I am running Ubuntu 8.04

---

