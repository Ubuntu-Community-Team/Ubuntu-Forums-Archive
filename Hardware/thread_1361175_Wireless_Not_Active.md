---
title: "Wireless Not Active"
date: 2009-12-21
forum: Hardware
---

### Post by khris91 on 2009-12-21
Ok, So i know this topic has come up quite a few times throughout this forum and yet i have been able to find a solution to this problem so i am hoping for some help...

I just recently installed Ubuntu 9.10 (first time i've ever used linux, did it so i could test it out before telling someone if it was good or not) and the install went great, not a single problem the entire time.. well after it gets loaded up and i log in i went to go try to connect to the internet but when i clicked on the network thing and it popped up it showed the connect to wireless network spot that you have to enter the SSID and everything.. Well i entered the SSID (linksys with no password) and it says it was disconnected.. So i thought maybe i might of done something wrong so i got on another computer and found out about WICD and so i thought "Well if i could get it attached via ethernet cable then maybe i can just download it straight to the computer" So i tried it and it came up as connected, so i tried to get onto firefox and got nothing... 

So i got back on and did more research, got a package with WICD in it.. tried to add it to the synaptic and i don't quite believe i got it installed (any help in this area as well would be greatly appreciated...). So i did some more research and found a command that listed my network devices (sudo lshw) and it said *-network DISABLED Description: Wireless interface. 

Any help that anyone can give will be truelly amazing so thank you!

-Khris

---

### Post by iceback on 2009-12-21
I not exactly new to ubuntu (since 7.x) but I'm having the same problem.  I've had wireless working all along until just a few days ago.  Lost it altogether mid-usage.  Took that as an opportunity to load 9.10 (upgrade from 8.4).  So here I sit wired in but cannot enable wireless.

Tried building compat-wireless-2009-12-11 and the build failed:

/compat-wireless-2009-12-11/drivers/net/wireless/rtl818x/rtl8187_leds.c: In function ‘rtl8187_unregister_led’:
/home/rob/Desktop/wireless/compat-wireless-2009-12-11/drivers/net/wireless/rtl818x/rtl8187_leds.c:170: error: implicit declaration of function ‘flush_delayed_work’
make[4]: *** [/home/rob/Desktop/wireless/compat-wireless-2009-12-11/drivers/net/wireless/rtl818x/rtl8187_leds.o] Error 1
make[3]: *** [/home/rob/Desktop/wireless/compat-wireless-2009-12-11/drivers/net/wireless/rtl818x] Error 2
make[2]: *** [/home/rob/Desktop/wireless/compat-wireless-2009-12-11/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/rob/Desktop/wireless/compat-wireless-2009-12-11] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [modules] Error 2


which was disappointing to say the least.  

Also installed wifi-radar, but that hasn't helped either.

What gives?

---

### Post by iceback on 2009-12-21
As to wifi-radar, it find my local wireless repeater, the connect button is active but pressing it does nothing.

Right-clicking on the network-manage icon shows  "Enable networking checked" but "Enabel wireless" is grey

---

### Post by iceback on 2009-12-21
Well, this could be embarrassing.  My old laptop is sitting beside me, merrily chatting over the airwaves, but this new HP 8530w is recently comatose, wirelessly speaking.  The each have an identical configuration for my access point (which used to work on this box too). Both machines have the same (sparce) /etc/network/interfaces file
[INDENT]auto lo
iface lo init loopback
[/INDENT]

I wonder if the internal card is dead?  How do I tell?

lspci tells me I have a Intel Corporation Wireless WiFi Link 5300, but does that mean it's working?  And should that show up as wlan0 or eth1

Running out of things to check.

---

### Post by iceback on 2009-12-21
Press the little antenna button goof.  Sheesh!

---

### Post by khris91 on 2009-12-22
Ok so i have done a ton of research the past few hours and i keep seeing people saying they install bcmwl-kernel-source but when i try to i have to install BKMS as well and when i finally get both up my Wireless drivers seem to magically disappear completely... But when i get rid of BKMS (which ends up purging bcmwl-kernel-source as well) the drivers reappear...

---

### Post by iceback on 2009-12-22
Better lay out the gory details of whic box you have.  (If I had, some other hp 8530w owner might have figured it out for me :) )

Also some of the output from the ifconfig, iwconfig, lspci might help.

---

### Post by khris91 on 2009-12-22
Im running a Dell Inspiron 1300 with a Intel Celeron M Processor
The network card is a Broadcom BCM4311 (AirForce 54g) 802.11a/b/g PCI Express Tranceiver

The ifconfig output is:

eth0
Link encap:Ethernet  HWaddr  00:14:22:94:42:76
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)


lo
Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:240 (240.0 B)   TX bytes: 240  (240.0 B)


iwconfig:


lo
no wireless extensions.

eth0
no wireless extensions.

wmaster0
no wireless extensions.

wlan0
IEEE 802.11bg   ESSID: " "
Mode:Managed  Frequency:2.412 GHz  Access Point:  Not-Associated
tx-Power=0 dbm
Retry  long limit:7   RTS thr:off   Fragment  thr:off
Power Management:off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0  Missed beacon:0


lspci:


This has been cut down...

2:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
2.03.0 Network controller: Broadcom Corporation BCM4311 {AirForce 54g}  802.11a/b/g PCI Express Transceiver (rev 02)


That is all of it basically.. I have tried to install bcmwl-kernel-source and dkms but when i do my drivers disappear for some unknown reason... Any help well be GREATLY appreciated...

---

### Post by tb-noobie on 2009-12-23
Hi I have (I suspect) a similar problem - so hope this is the best place to post it.
 
I'm a complete novice when it comes to linux - so if any of this doesn't make sense or I need to post more info please let me know.
 
I had a problem with my sound ("No volume control gstreamer plugins and/or devices found" ) which I managed to solve with the help of guidance on these forums and elsewhere, but in doing so I seem to have knocked out my wireless capability.
 
When I go to Admin/Network (using the GUI) I can no only see "Wired Connection" & "Point-to-point connection" - previously I could also see wireless connection.
 
I presume therefore my "driver" is no longer installed or registered?
 
Not quite sure what the report does but if I run "lspci -v" from terminal the Output includes :
 
02:00.0 Ethernet Controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
            Subsytem: Aksey Computer Corp. Unknown device 7128
            Flags: bus master, fast devsel, latency 0, IRQ 7
            Memory at 32100000 (64-bit, non-prefetchable) [Size=64K]
            Capabilities .......
 
Which I presume means my wifi card is at least physically recognised.
 
Grateful for any pointers as to what to do next.
 
Regards,
 
 
Tony

---

### Post by khris91 on 2009-12-23
Tony,
Have you downloaded any packages labelled dkms? If so I "suspect" that might of been the problem but I can't guarentee it, the only reason I say that is because my wireless cards continue to disappear after installing dkms.. But if you did not install it when trying to get your sound to work then don't mess with it cause it might be working with your card better then mine is...

---

### Post by khris91 on 2009-12-23
Bump

---

### Post by ken_do_san on 2009-12-23
I had the same problem with wireless not working in my Compac, it appears you have the same set as my laptop.  I found this link in a previous forum post (thanks go to snowpine) and tried out the drivers Broadcom have.  Click the link (or copy and paste into your browser) and it'll take you the page, just choose the appropriate driver, untar it and follow the directions.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Hope it works for you and anyone else curious enough to try it out, it doesn't however activate the wireless antenna switch (on my system it still stays orange but I definitely have wireless connectivity).

Merry Christmas to all ho ho ho

---

### Post by gcvisel on 2010-01-26
I found "the definitive answer" over at 
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)
for my Emachines E520 new install of Ubuntu 9.10.  It involved searching Synaptic for ""b43-fwcutter" to download and run.  It came right up after a reboot.

Spook.

---

### Post by uaebuntu on 2010-01-26
The network card is a Broadcom BCM4311 (AirForce 54g) 802.11a/b/g PCI Express Tranceiver

I have had loads of problems with the open and proprietry drivers for Broadcomm wireless on my Dell Latitude. It sort of worked occasionally with the propriety drivers and we tried to blacklist the open drivers to stop them loading altogether but to no avail. (even taking it to the linux Guru at work)

Eventual solution was to use Intel hardware

---

