---
title: "Wireless Used To Connect - Help"
date: 2010-02-15
forum: Hardware
---

### Post by vaemor on 2010-02-15
My sisters laptop (HP G60) was infected so I put her in the safer area of Ubuntu (9.10 w/updates)

Well everything was fine, she came back after a week and her wireless is gone. (Network Disconnected - you are now offline) It had wireless working fine when I gave it to her; I looked around and nothing in settings is able to turn it back on. Not even the Fn key thing.

Since wireless internet was working before (so it couldn't be the usual problems) why is it unable to detect any wireless connection at all now? I've run into a wall.

---

### Post by RedSingularity on 2010-02-15
Post the output of 

ifconfig

---

### Post by vaemor on 2010-02-15
eth0      Link encap:Ethernet  HWaddr 00:1f:16:7d:ac:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:5e:28:f0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2C-5E-28-F0-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by RedSingularity on 2010-02-15
Check in

System>Admin>Hardware Drivers

See if you can activate it there.

---

### Post by vaemor on 2010-02-15
> **RedSingularity said:**
> Check in

System>Admin>Hardware Drivers

See if you can activate it there.
Unfortunately nothing shows up in that box. ("No proprietary drivers are in use on this system")

---

### Post by RedSingularity on 2010-02-15
Well it looks like your adapter is not even powered on.  I am looking at you ifconfig output.  Post the output of 

lspci

That will give us a chipset.

---

### Post by vaemor on 2010-02-15
> **RedSingularity said:**
> Well it looks like your adapter is not even powered on.  I am looking at you ifconfig output.  Post the output of 

lspci

That will give us a chipset.
Ah, turning it on might work, but I've been trying to do that with no luck. Here is the lspci:


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

---

### Post by RedSingularity on 2010-02-15
Yes so it looks like the system see's the hardware.  Are you sure you cant turn it on somehow?

---

### Post by vaemor on 2010-02-15
> **RedSingularity said:**
> Yes so it looks like the system see's the hardware.  Are you sure you cant turn it on somehow?
I've tried all the Fn keys to turn it on, nothing, and there isn't any physical switch on the laptop itself for wireless either; the network settings panel doesn't help, and right-clicking on the zero wireless bars shows network and wifi are checked and on. Still I can't seem to turn this on.

I might have to just reinstall Ubuntu and see if that helps.

---

### Post by RedSingularity on 2010-02-15
Can you right click the little Wireless icon and see of "Wireless" is checked on?

---

### Post by vaemor on 2010-02-15
> **RedSingularity said:**
> Can you right click the little Wireless icon and see of "Wireless" is checked on?
X Enable Network
X Enable Wireless

Are both checked on, but still nothing shows up on wireless.

And it says:

Wireless Networks
Disconnected

When I left click on the bars to see if I can get a wireless connection.

---

### Post by RedSingularity on 2010-02-15
Thats the same problem i have when i turn off the wireless adapter.  Thats why i am assuming yours is switched off.

---

### Post by vaemor on 2010-02-15
> **RedSingularity said:**
> Thats the same problem i have when i turn off the wireless adapter.  Thats why i am assuming yours is switched off.
That's most likely the problem, but I can't turn it on.

---

### Post by pi/roman on 2010-02-15
Here is a similar problem where the switch was only operable during login:

[[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1359723[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1359723")

---

### Post by vaemor on 2010-02-15
> **pi/roman said:**
> Here is a similar problem where the switch was only operable during login:

[[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1359723[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1359723")
Thanks so much, it works now!, freakin A!

---

