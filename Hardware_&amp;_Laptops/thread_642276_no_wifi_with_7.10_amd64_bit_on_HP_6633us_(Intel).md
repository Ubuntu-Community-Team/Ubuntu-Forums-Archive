---
title: "no wifi with 7.10 amd64 bit on HP 6633us (Intel)"
date: 2007-12-16
forum: Hardware &amp; Laptops
---

### Post by gfd_2 on 2007-12-16
here we go... I downloaded the 64bit ISO, burned an image and installed... with the usual issues of no sound and no wifi.

NOTE: This link is no longer valid.. Not sure why. 

Working on the wifi issue... whoooeee there's a LOT of suggestions out there and one has me seeing my network... the essid is right there! BUT - i can't connect.    wifi-radar sees the network but wont' get an IP, NetworkManager sees the network but times out after ~ 40 seconds.    My network is wide open... no security


Here's some info....

:~$ cat /etc/network/interfaces:
auto lo
iface lo inet loopback
iface eth1 inet dhcp
wireless-essid <MY ID HERE>
auto eth1

:~$ sudo ifup eth1 
"SET failed on device eth1 ; no such device" There is already a pid file /var/run/dhclient.eth1.pid with pid 1
Internet Systems Consortium DHCP Client V3.0.5
All rights reserved blah blah blah.

sudo ifup wlan0
Ignoring uknown interface wlan0=wlan0

sudo ifdown wlan0
wlan0 not configured

dhclient
Listening on LPF/wlan0/00:1a:73:d7:d6:fe
Sending on LPF/wlan0/00:1a:73:d7:d6:fe
Sending on Socket/ fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS recieved
No working leases in persistant database - sleeping


Can someone offer any suggestions?

---

### Post by gfd_2 on 2007-12-16
here is how I got to where I am:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-dfa35a08da26002d337e79d528efb0c4ed5a127f](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-dfa35a08da26002d337e79d528efb0c4ed5a127f)

every time the system sees my network but will not attach.

---

### Post by gfd_2 on 2007-12-16
After running some commands found on the previous site here's what 
cat /etc/network/interfaces looks like:

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid 04Z411305563

auto wlan0

IFUP: 

dcb@dcb-laptop:~$ sudo ifup wlan0
[sudo] password for dcb:
ifup: interface wlan0 already configured

DHCLIENT:
Listening on LPF/wlan0/00:1a:73:d7:d6:fe
Sending on   LPF/wlan0/00:1a:73:d7:d6:fe
Listening on LPF/eth0/00:1b:24:e5:4f:dc
Sending on   LPF/eth0/00:1b:24:e5:4f:dc
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.47 -- renewal in 40201 seconds.


Any suggestions on how to get Wifi-Radar or Network Manager to attach to my network?  It would appear that I'm able to see the network and communicate with it... but when I unplug my wire... no good.

---

### Post by Z_o-s-o on 2007-12-16
Is the wireless a broadcom or Atheros chipset

---

### Post by gfd_2 on 2007-12-16
lspci -nn | grep Network shows: 
02:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 02)

and

driver=ndiswrapper+bcmwl5 
driver=r8169

This is driving me buggy... my network is visible, the lights are blue but no connection. 

Thanks -

---

### Post by gfd_2 on 2007-12-17
bump

---

### Post by Z_o-s-o on 2007-12-17
This page got my Broadcom working on my DV6215.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by gfd_2 on 2007-12-17
i'm going to do a wipe, reinstall then run through the guide. Thanks.

---

### Post by gfd_2 on 2007-12-17
where to go from here?    I have gone through 4 different processes...

1.) run the installer prescribed by darknoob... no good.
2.) ran through the Broadcom Wireless tutor in the Ubuntu 7.10 (Gutsy) wiki ... no good.
3.) Enabled repositories, installed the restricted driver, blue light came on for the wifi card!  but N-M did not recognize a wireless network... rebooted... and nothing.
IWCONFIG - lo = no wireless extensions, eth0 = no wireless extensions.
IWLIST - lo and eth0  both do no support scanning

3.) ran through the tutorial for fwcutter and the bcm4311 file... no good.
4.) ran through the wiki doc on Broadcom BCM3411 rev 01 (ndiswrapper) ... no good.

Any suggestions?  

Before I try anthing else I'm going to do another wipe and reinstall so I know I'm working with a clean system...

Any and all suggestions are MORE then welcome.

---

### Post by Z_o-s-o on 2007-12-17
Thats some bad luck....

I've got the Bcm4311 and at first I was using the restricted driver, but it had no range for me.

So I followed that walk through I posted and I'm typing this reply on it as we speak.  I don't know where you should go from here though.

---

### Post by gfd_2 on 2007-12-18
> **Z_o-s-o said:**
> This page got my Broadcom working on my DV6215.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I think I see the problem... you have an AMD process while I have an Intel processor... another poster explained that these steps wouldn't work on an Intel system.... just my luck.

Thanks anyway.

---

### Post by gfd_2 on 2007-12-18
bump - reinstalled 7.10

Any suggestions?

---

### Post by Z_o-s-o on 2007-12-18
Maybe you can get support from Canonical?

At very least you should be getting something using the restricted driver manager.

On a side note, there were problems with wifi cards failing in theres laptops, and I did have to send mine back to HP for a new motherboared.  Not sure if that was Intel too, but I believe so.

---

### Post by gfd_2 on 2007-12-18
according to the Conical website it will cost me 293 US dollars for  9am to 5 pm support....

---

### Post by Z_o-s-o on 2007-12-18
Thats becaue its selling it to you in 1 year quantities.

Are you 100% percent sure this wireless card is working correctly. As previously stated, theres know problems with motherborads on the dv6000's.

If it is working correctly, then I'm outta ideas. In 7.10, the bmc4311 is detected out of the box, and can be installed by using the restricted driver manager. I had problems with range, but it connected to WEP, WPA, WPA2 and all of that.

On that guide I gave you, at the bottom, various people reported sucess on Intel processors.

---

