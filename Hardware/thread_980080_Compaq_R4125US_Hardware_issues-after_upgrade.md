---
title: "Compaq R4125US Hardware issues-after upgrade"
date: 2008-11-12
forum: Hardware
---

### Post by rwap on 2008-11-12
Hi,

I have a compaq R4125US laptop that I have been running ubuntu on since version 7.04 (I think)  I upgraded to the new versions every time they came out, reluctantly, because of all the bad PR that upgrades get, also it took me weeks to get the wireless adaptor working.

anyways,

I upgraded to 8.10 last night and it all seemed to go well with the exception of the estimated time clock...whoever programed it needs to be shot. (lol) ie. it says 15 min left, you come back hour later and it still says 10 min! buts that's not the issue.

I booted 8.10 up this morning and it worked :) BUT, my wireless didn't and also my volume controls are messed up too..

For the wireless, I noticed the restricted driver was enabled, so I disabled it, because I remember when I first got the wireless working I installed some kind of wrapper thing- I forgot what it was called.. ldwrapper?  And it was still there apparently, if I go to system->admin->windows wireless drivers is listed.

anyway, I disabled the restricted driver and it still didn't work, I kept using ubuntu to see what else was broken and for some reason most keys on the keyboard stoped working.. the caps lock, enter key, F-#'s and a few others worked but I couldnt type anything. Also, I couldn't use the mouse to click most of the gnome panel, I could only click the icons and the calendar. So I ctrl+backspaced gnome and when it came back up I still couldn't click the panel BUT, the wireless was working, it asked for the password and connected, so I checked my email etc... and it worked great, UNTIL I REBOOTED. After I rebooted I can use the keyboard and mouse normally, but now the wireless is totally broke. (go figure) So I re-enabled the restricted driver and when I tried to type the root password the keyboard and mouse broke again! I rebooted and tried again and it worked, the driver enabled, but wireless didnt work. The icon is up in the corner and if I right click it it shows Wireless greyed out but it wont let me do anything. I check the network configuration thing under the system->preferences menu and it shows my routers config there but thats all I know how to do..

As for the sound.

When I press the volume buttons (up down and mute) it repeats the action continuously, IE. if I press the down button once it turns all the way down and if I go to manually adjust it I drag the slider up it turns it back down, if I press the UP button it does the same thing, the mute button appears to work...

If I press mute then go to manually adjust the volume it works fine I can drag the sliders and they stay.

I found this for the sound, but it doesn't work right..

[http://ubuntuforums.org/showthread.php?t=975464&highlight=volume+control+buttons](http://ubuntuforums.org/showthread.php?t=975464&highlight=volume+control+buttons)

If I turn off the repeat, the volume buttons stop working, if I slow down either one of them it has no effect.


On the keyboard and mouse issue, I found this.. 

[https://bugs.launchpad.net/ubuntu/intrepid/+source/acpid/+bug/285323](https://bugs.launchpad.net/ubuntu/intrepid/+source/acpid/+bug/285323)

Except I CAN adjust my brightness without this happening, Im not really sure what makes it stop working it just randomly stops..


BTW. While the wireless was working, I updated ubuntu and it dl'ed 19 updates- don't remember what they all were..

also, the wireless card is a broadcom, but I don't remember what model and don't know how to find out.

Wow.. This was a long post.
Thanks look forward to some help.
Rwap

---

### Post by rwap on 2008-11-12
I found out how to find the model wifi card I have,

I ran   lspci | grep Broadcom\ Corporation

and got

Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Maybe this will help?

---

### Post by rwap on 2008-11-13
Ok, I got the wireless to work- sort of 

I removed the proprietary driver from the blacklist file-/etc/modprobe.d/blacklist

rebooted and it kinda worked.. The light on my wifi button works and it sees my network It connected 1 time again... I used it, Rebooted to make sure it was really fixed and Now it wont work again. I tries to connect but it just sits there and after a few minutes says disconnected.

Weird..

Even Weird-er... I found a link on the volume controls and keyboard + mouse.. If I press any of the volume buttons it causes the keyboard to stop working and I cant click anything on the gnome panel- except icons and the calendar. As I said earlier. 

Ideas?

---

### Post by rwap on 2008-11-13
ok, I found something on the wireless....

It is having a issue with DHCP... I found this in the syslog...

> Nov 13 03:22:31 russell-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Nov 13 03:22:31 russell-laptop NetworkManager: <info>  dhclient started with pid 6331 
Nov 13 03:22:31 russell-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov 13 03:22:31 russell-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Nov 13 03:22:31 russell-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov 13 03:22:31 russell-laptop dhclient: All rights reserved.
Nov 13 03:22:31 russell-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov 13 03:22:31 russell-laptop dhclient: 
Nov 13 03:22:32 russell-laptop NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit 
Nov 13 03:22:32 russell-laptop dhclient: Listening on LPF/eth1/00:90:4b:ee:91:1d
Nov 13 03:22:32 russell-laptop dhclient: Sending on   LPF/eth1/00:90:4b:ee:91:1d
Nov 13 03:22:32 russell-laptop dhclient: Sending on   Socket/fallback
Nov 13 03:22:35 russell-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Nov 13 03:22:35 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 4 
Nov 13 03:22:35 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Nov 13 03:22:36 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Nov 13 03:22:36 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Nov 13 03:22:38 russell-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Nov 13 03:22:40 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 4 
Nov 13 03:22:40 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Nov 13 03:22:40 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Nov 13 03:22:40 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Nov 13 03:22:42 russell-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Nov 13 03:22:44 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 4 
Nov 13 03:22:44 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Nov 13 03:22:44 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Nov 13 03:22:44 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Nov 13 03:22:47 russell-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Nov 13 03:22:48 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 4 
Nov 13 03:22:48 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Nov 13 03:22:48 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Nov 13 03:22:48 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Nov 13 03:22:52 russell-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Nov 13 03:22:53 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 4 
Nov 13 03:22:53 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Nov 13 03:22:53 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Nov 13 03:22:53 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Nov 13 03:22:57 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 4 
Nov 13 03:22:57 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Nov 13 03:22:57 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Nov 13 03:22:57 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Nov 13 03:23:01 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 4 
Nov 13 03:23:01 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Nov 13 03:23:01 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Nov 13 03:23:01 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Nov 13 03:23:06 russell-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Nov 13 03:23:06 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 4 
Nov 13 03:23:06 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Nov 13 03:23:06 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Nov 13 03:23:06 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Nov 13 03:23:10 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 4 
Nov 13 03:23:10 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Nov 13 03:23:10 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Nov 13 03:23:10 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Nov 13 03:23:14 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 4 
Nov 13 03:23:14 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Nov 13 03:23:14 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Nov 13 03:23:14 russell-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Nov 13 03:23:16 russell-laptop NetworkManager: <info>  Device 'eth1' DHCP transaction took too long (>45s), stopping it. 
Nov 13 03:23:16 russell-laptop NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 6331 
Nov 13 03:23:16 russell-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Nov 13 03:23:16 russell-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Nov 13 03:23:16 russell-laptop NetworkManager: <info>  (eth1): device state change: 7 -> 9 
Nov 13 03:23:16 russell-laptop NetworkManager: <info>  Activation (eth1) failed for access point (wireless) 
Nov 13 03:23:16 russell-laptop NetworkManager: <info>  Marking connection 'Auto wireless' invalid. 
Nov 13 03:23:16 russell-laptop NetworkManager: <info>  Activation (eth1) failed. 
Nov 13 03:23:16 russell-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Nov 13 03:23:16 russell-laptop NetworkManager: <info>  (eth1): device state change: 9 -> 3 
Nov 13 03:23:16 russell-laptop NetworkManager: <info>  (eth1): deactivating device (reason: 0). 

Also I am using clarkconnect for my DHCP server, I found the assignment and expiration- I can connect to the network- ONLY WHEN THE DHCP IS EXPIRED. I watched it As soon as the time was up ubuntu joined.. 

Just a sec I will post the syslog after connecting- It might be useful.

EDIT: Ok here's the syslog from the laptop after joining the network..

> Nov 13 03:31:57 russell-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Nov 13 03:31:57 russell-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Nov 13 03:31:57 russell-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov 13 03:31:57 russell-laptop dhclient: All rights reserved.
Nov 13 03:31:57 russell-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov 13 03:31:57 russell-laptop dhclient: 
Nov 13 03:31:57 russell-laptop NetworkManager: <info>  dhclient started with pid 6274 
Nov 13 03:31:57 russell-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov 13 03:31:57 russell-laptop NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit 
Nov 13 03:31:57 russell-laptop dhclient: Listening on LPF/eth1/00:90:4b:ee:91:1d
Nov 13 03:31:57 russell-laptop dhclient: Sending on   LPF/eth1/00:90:4b:ee:91:1d
Nov 13 03:31:57 russell-laptop dhclient: Sending on   Socket/fallback
Nov 13 03:32:00 russell-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Nov 13 03:32:00 russell-laptop dhclient: DHCPOFFER of 192.168.3.128 from 192.168.3.1
Nov 13 03:32:00 russell-laptop dhclient: DHCPREQUEST of 192.168.3.128 on eth1 to 255.255.255.255 port 67
Nov 13 03:32:00 russell-laptop dhclient: DHCPACK of 192.168.3.128 from 192.168.3.1
Nov 13 03:32:00 russell-laptop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
Nov 13 03:32:00 russell-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 13 03:32:00 russell-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Nov 13 03:32:00 russell-laptop NetworkManager: <info>    address 192.168.3.128 
Nov 13 03:32:00 russell-laptop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Nov 13 03:32:00 russell-laptop NetworkManager: <info>    gateway 192.168.3.1 
Nov 13 03:32:00 russell-laptop NetworkManager: <info>    hostname 'russell-laptop' 
Nov 13 03:32:00 russell-laptop NetworkManager: <info>    nameserver '192.168.3.1' 
Nov 13 03:32:00 russell-laptop NetworkManager: <info>    domain name 'system.lan' 
Nov 13 03:32:00 russell-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 13 03:32:00 russell-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Nov 13 03:32:00 russell-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Nov 13 03:32:00 russell-laptop avahi-daemon[4846]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.3.128.
Nov 13 03:32:00 russell-laptop avahi-daemon[4846]: New relevant interface eth1.IPv4 for mDNS.
Nov 13 03:32:00 russell-laptop avahi-daemon[4846]: Registering new address record for 192.168.3.128 on eth1.IPv4.
Nov 13 03:32:00 russell-laptop dhclient: bound to 192.168.3.128 -- renewal in 19051 seconds.
Nov 13 03:32:01 russell-laptop NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Nov 13 03:32:01 russell-laptop NetworkManager: <info>  Policy set 'Auto wireless' (eth1) as default for routing and DNS. 
Nov 13 03:32:01 russell-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Nov 13 03:32:01 russell-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 13 03:32:02 russell-laptop ntpdate[6347]: adjust time server 91.189.94.4 offset 0.196848 sec

So... Is the dhcp thing ubuntu's fault or clarkconnect?

---

