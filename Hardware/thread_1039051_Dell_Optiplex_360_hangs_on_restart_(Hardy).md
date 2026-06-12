---
title: "Dell Optiplex 360 hangs on restart (Hardy)"
date: 2009-01-14
forum: Hardware
---

### Post by larseko on 2009-01-14
Hi, I posted this in the wrong section previously (DE). Sorry for that. 

I just got a new Dell Optiplex 360, and have installed 8.04.1 on it. Everything works fine, including suspend and shutdown, but when I try to restart the computer it hangs, just when the shutdown progress bar is "empty". I have to do a hard shutdown to start over.

I have done some searches, and tried following:

[LIST]
[*]Modify the alsa-utils init script to take down the network interface eth0.
[*]Set the kernel option reboot=b in /boot/grub/menu.lst
[/LIST]

None of these suggestions helped me any further. Here's an excerpt from my syslog when I tried to reboot:

```
Jan 14 10:26:07 LO-E11 kernel: [   22.805092] eth0: no IPv6 routers present
Jan 14 10:26:24 LO-E11 init: tty4 main process (4360) killed by TERM signal
Jan 14 10:26:24 LO-E11 init: tty5 main process (4361) killed by TERM signal
Jan 14 10:26:24 LO-E11 init: tty2 main process (4363) killed by TERM signal
Jan 14 10:26:24 LO-E11 init: tty6 main process (4367) killed by TERM signal
Jan 14 10:26:24 LO-E11 init: tty1 main process (5315) killed by TERM signal
Jan 14 10:26:24 LO-E11 init: tty3 main process (4365) killed by TERM signal
Jan 14 10:26:26 LO-E11 gdm[5151]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jan 14 10:26:26 LO-E11 gdm[5151]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Jan 14 10:26:26 LO-E11 avahi-daemon[4807]: Got SIGTERM, quitting.
Jan 14 10:26:26 LO-E11 avahi-daemon[4807]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.251.
Jan 14 10:26:27 LO-E11 kernel: [   42.510024] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jan 14 10:26:27 LO-E11 NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Jan 14 10:26:27 LO-E11 NetworkManager: <info>  Deactivating device eth0. 
Jan 14 10:26:27 LO-E11 dhclient: receive_packet failed on eth0: Network is down
Jan 14 10:26:27 LO-E11 NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Jan 14 10:26:27 LO-E11 NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Jan 14 10:26:28 LO-E11 exiting on signal 15

```

Please help, it would be nice to have restart working, as I have several machines like this to use in a school, and it confuses the users when things don't work like expected. 

Thanks in advance.

---

### Post by tjpoe on 2009-02-24
same thing happens here. is this a problem with 8.04? will try 8.10

---

### Post by tjpoe on 2009-02-24
problem persists in 8.10 (Intrepid). Any ideas?

---

### Post by johnhammonds on 2009-03-08
I have a Dell Optiplex 745 with a Q6600 (Quad 2 Core) and my girlfriend has the same pc with a Core 2 Duo CPU. We have the same problem on theses pc's with 8.04 32bit. I don't have that issue with the amd64bit version, but I don't want to run the 64bit version. If anyone has any idea's, that would be awesome! Hope Jaunty 32bit solves this issue!!! (fingers crossed).

---

### Post by tjpoe on 2009-07-01
64 bit version of Jaunty works fine, but 32 bit version hangs on reboot. anyone have any fixes?

---

### Post by razius on 2009-07-27
bump? :(

---

