---
title: "Re-enable wireless after suspend/resume"
date: 2006-07-16
forum: Hardware &amp; Laptops
---

### Post by ltmon on 2006-07-16
Hi all,

To my immense please my Kubuntu 6.06 installation on a new laptop suspends to RAM straight out of the box with practically no problem whatsoever.

This is especially pleasing given I thought that with the ATI graphics card I had no hope of getting this to work.

The only thing I need to do when resuming is to re-enable wireless by clicking on the network I am connected to in KNetworkManager.  It already looks enabled, but I need to force it to refresh itself to get any kind of wireless connectivity back.

Does anyone know of a way to do this automatically or via the command line.  I'm sure I could work out how to add an extra command to the suspend/resume scripts if only I knew how to do this.

Thanks in advance,

L.

---

### Post by shortbus on 2006-07-16
> **ltmon said:**
> 
The only thing I need to do when resuming is to re-enable wireless by clicking on the network I am connected to in KNetworkManager.  It already looks enabled, but I need to force it to refresh itself to get any kind of wireless connectivity back.


You might want to give this a shot:
[network services]("http://blogs.cyberciti.biz/hm/index.php/2005/10/03/how-do-i-restart-linux-network-service/")

---

### Post by awaldram on 2006-07-16
I use wifi-radar with the following in resume.d beauty of this is I can suspend move location restart and still have network access.

/etc/acpi/resume.d/45-wifistart.sh

#!/bin/bash

if [ -x /usr/sbin/wifi-radar ]; then
        /etc/init.d/wifi-radar restart;
        ifconfig eth1 up
        /usr/sbin/wifi-radar  -d

fi

---

### Post by ltmon on 2006-07-16
> **awaldram said:**
> I use wifi-radar with the following in resume.d beauty of this is I can suspend move location restart and still have network access.

/etc/acpi/resume.d/45-wifistart.sh

#!/bin/bash

if [ -x /usr/sbin/wifi-radar ]; then
        /etc/init.d/wifi-radar restart;
        ifconfig eth1 up
        /usr/sbin/wifi-radar  -d

fi

Does this work with NetworkManager, or is it a completely different system?  I'm really happy with it otherwise, and I don't particularly want to go through setting up a brand new tool for network management just because of this small problem.

Cheers,

L.

---

### Post by edrex on 2006-07-19
I have the same issue: on resume, KNetworkManager still shows connectivity to the pre-suspend network. This is sorted out after ~30 seconds though (probably by my card?) if the same network is still available, so it hasn't bothered me too much (better than the old days eh?).

A related issue, and the one that has me googling around for a solution, is that KNetworkManager doesn't refresh the list of networks for upwards of *60 (90?) seconds* following a resume. I usually give up waiting and  manually type the ESSID and WEP key into the "Connect to other wireless network..." dialog.

I don't know anything about this new dbus thing, but it seems like somebody (networkmanagerd, knetworkmanager) isn't getting the "we just woke up!" message. 

Maybe I just didn't notice it before, but it seems like it may have broken post-release... err... or maybe it's because I'm running KDE 3.5.3. How about you, ltmon, are you running the new KDE?

---

### Post by ltmon on 2006-07-19
Yep I'm running 3.5.3, and like you I found that if I just wait long enough it will just automatically reconnect to whatever network is available.

I use kwallet to store WEP/WPA keys for my trusted networks, so I don't even have to do this step - just force it to wake up by clicking on a network.

L.

---

