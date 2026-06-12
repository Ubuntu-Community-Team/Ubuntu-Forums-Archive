---
title: "wireless randomly fails, requires reboot"
date: 2008-07-18
forum: Hardware
---

### Post by Minilek on 2008-07-18
I use a Lenovo T61, and lspci says the following about my wireless card: "03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)".

Occasionally (maybe a couple of times a day) internet via my wireless card just stops working: I seem to not be able to send/receive packets.  If I try to restart my wireless either by ifdown eth1 then ifup eth1, or by /etc/init.d/networking restart, I get the following error:
```

send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Resource temporarily unavailable.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; Resource temporarily unavailable.

```
I then have to reboot for my wireless to work.  If I don't reboot immediately once receiving this error, i.e. I continue to just use my laptop offline, then my laptop eventually (within a minute or two) freezes and I can no longer execute new programs or kill old ones.  I then have to do a cold reboot to restore normal use of my laptop.

Does the above happen to anyone else, or has anyone heard of such an issue?  I'm using Gutsy Gibbon, Ubuntu 7.10.

Here's my /etc/network/interfaces
```

auto lo
iface lo inet loopback


iface eth1 inet dhcp
wireless-mode managed
wireless-essid someessidhere

iface eth0 inet dhcp

auto eth0

auto eth1

```

---

### Post by kerry_s on 2008-07-18
your not alone i had that problem to, i couldn't figure it out, i didn't have time to figure it out and just moved to win2k. i was using a ibm t20, blitz usb wireless, ndiswrapper.
the wireless when it did work it was not dependable enough for me to let mom use it.
sorry, i know it's not much help, just hang in there.

---

### Post by brion@cbkidder.com on 2009-10-25
I am having similar intermittent wireless failure problems on my Lenovo T61 with Intel PRO/Wireless 3945ABG in Jaunty.

I can connect to a wireless network but after maybe 10-15 minutes of usage it just abruptly stops. I have to reconnect to the wireless network to continue what I was doing. Strangely, I only see it happen while I'm watching streaming video tv shows like on hulu.com.

Also in my household using the same wireless is a Windows XP and a Mac laptop, and neither have the same issues as I am. 

Power management is set to never/do nothing so I think the problem is in how Jaunty works with the 3945ABG.

Any suggestions would be much appreciated.

---

