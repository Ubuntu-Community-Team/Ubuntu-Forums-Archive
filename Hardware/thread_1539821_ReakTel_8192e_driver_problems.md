---
title: "ReakTel 8192e driver problems"
date: 2010-07-27
forum: Hardware
---

### Post by msh559 on 2010-07-27
Hey, just trying to get my wifi and wired connections going on ubuntu 10.04.  just installed it to dual boot with win 7 and im having some troubles with my driver for the network card.  I cant connect to my home network through wireless and cannot connect to the internet with my wired connection.  When plugged into wired my network says etho1 or autoeth1 or whatever but when i go to open mozilla it says no internet access.  How am i supposed to run ndiswrapper to install my driver if i have no way to download it wired in the first place?  

Try to keep it simple too, im kinda out of my element when it comes to linux,  used to windows bios talk haha.:)

---

### Post by P4man on 2010-07-27
a little bit more info would be useful. When you say "I cant connect to my home network through wireless and cannot connect to the internet with my wired connection." Does that mean you can connect to the local network using wired? 

If you plug out and in the ethernet cable, do you get a notification ? if so that means your wired networking driver at least is working and it could be an internet connectivity problem (ipv6 or dns related) for the wired. lets sort that out before trying to fix the wireless.

---

### Post by msh559 on 2010-07-27
ok so when i plug in my ethernet cord the networking icon in the top right corner starts moving and whatever, then a notification pops up and says wired connection you are now offline

My toshiba l500 is using a:
Realtek RTL8102E/RTL8103E Family PCI-E Fast Ethernet NIC (NDIS 6.20)
Realtek RTL8192E Wireless LAN 802.11n PCI-E NIC

My router is a d-link dir-615.

What i'm guessing is that there is a ip problem in ubuntu. This is how i had it set up

Wired Connection 1
MAC address 00:22:5f:9c:3e:a1
MTU automatic

IPv4 settings 
MEthod: automatic(DHCP)

IPv6 settings 
Method: ignore

---

### Post by msh559 on 2010-07-27
and when i plug in the ethernet cord and after it pops up the notification ill click on the network icon and Auto Ethernet is under available but when i try to connect it gives the same notification

---

### Post by P4man on 2010-07-28
Did you enter that MAC address? I always leave it blank and never had any issue. Possibly network manager entered it for you, but are you sure its correct (or just delete it)

Can you also open a terminal and provide the output of:
```

lspci 
```
(this will show the exact type of network cards)
```

ifconfig
```
(shows your network settings)
```

sudo ifconfig eth[COLOR="Red"]0[/COLOR] up
```

This will try and bring the network connection up and the output is what im interested in here. You may need to change the "0" with "1" or "2" depending what number your card got assigned in the output of ifconfig.

Last point; you may want to try and change the MTU size in the connection settings. Try setting it to 1500.

---

### Post by msh559 on 2010-07-29
ok ran all the commands, nothing came up after i put in 

sudo ifconfig eth0 up
 
so i dont know what that means
 
here they are


mitch@mitch-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
14:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)

mitch@mitch-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:5a:0c:6c:fb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0x6000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)


mitch@mitch-laptop:~$ sudo ifconfig eth0 up
mitch@mitch-laptop:~$

---

### Post by msh559 on 2010-07-29
also tried to connect to my router homepage by entering my gateway 192.168.0.1 and firefox did the usual offline spiel.  It must be a problem with some settings in ubuntu

---

### Post by P4man on 2010-07-30
The MAC address I see in the output of ifconfig doesn match the mac address you put in network manager. Try putting in the correct one.

---

### Post by msh559 on 2010-07-30
same outcome as last time.  Try to connect to Wired Connection 1 and brings up Wired Connection- You are now disconnected.  Does anyone know what the hell is going on? 
 
Back about 6 months ago i used the Ubuntu live cd to just run ubuntu without installing it and it was able to connect to the internet.  The only differences ive made to my network or setup is that i upgraded to windows 7 and i got a new router.  Neither of these should have anything to do with this problem though? This is extremely frustrating

---

### Post by msh559 on 2010-07-30
Just hooked up my laptop directly to the ethernet cord to the modem  to bypass the router to see if it was a router compatibility problem.  Couldnt connect to the internet straight out of the modem so it has to be some setting in ubuntu.
Is there a way to manually install a driver without using nsidwrapper?  i think that this is the problem because when i click on Hardware Drivers, not one driver displays and it says there are no proprietary drivers are in use on this system.

---

### Post by P4man on 2010-07-30
You're not getting an IP address. Can you post the output of

```
sudo dhclient
```

You could also try setting all up your IP, DNS, and gateway manually and see if that helps.

---

### Post by P4man on 2010-07-30
> **msh559 said:**
> Just hooked up my laptop directly to the ethernet cord to the modem  to bypass the router to see if it was a router compatibility problem.  Couldnt connect to the internet straight out of the modem so it has to be some setting in ubuntu.
Is there a way to manually install a driver without using nsidwrapper?  i think that this is the problem because when i click on Hardware Drivers, not one driver displays and it says there are no proprietary drivers are in use on this system.

AFAIK ndiswrapper is only for wireless (but I could be wrong). And you are not getting any proprietary drivers because for that; you need to be connected to the internet. Catch22. I think there are proprietary drivers for you card though but afaik you shouldnt need them. Ill google some more later.

---

### Post by msh559 on 2010-07-30
mitch@mitch-laptop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

SIOCSIFFLAGS: Operation not permitted
SIOCSIFFLAGS: Operation not permitted
Listening on LPF/wlan0/00:22:5f:9c:3e:a1
Sending on   LPF/wlan0/00:22:5f:9c:3e:a1
Listening on LPF/eth0/00:23:5a:0c:6c:fb
Sending on   LPF/eth0/00:23:5a:0c:6c:fb
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
mitch@mitch-laptop:~$


got nsidwrapper working by following the following wiki
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

was able to install the driver for my card but as soon as i get to the following part:

[COLOR="DarkRed"]3.6.3. Configuring Wireless Network Settings using command line
If the above methods did not produce a working Wireless Network connection, you can Edit the Network Interfaces file by hand and diagnose your network using the command line.

You can discover settings with iwconfig beyond those on offer with the Networking tool. Also, the order of the wireless settings can be very important. If you discover that issuing iwconfig commands in a certain order on the command line is necessary, make sure the file asserts the settings in the same order.
Test /etc/network/interfaces by activating and deactivating the wireless network interface from the Terminal, which shows some diagnostic messages:
  sudo ifdown wlan0
  sudo ifup wlan0
You may diagnose the network adapter status with commands:
  ifconfig
  iwconfig
  
  dmesg
  tail /etc/var/messages
Note: During startup, the system will activate the Network Admin settings kept in the file /etc/network/interfaces, where the Networking tool saves its settings.
For information on getting WPA to work, read the WPAHowto.[/COLOR]
[COLOR="Black"][/COLOR]
ill put in sudo ifdown wlan0

and it will say ifdown:interface wlan0 not configured

and when i put in sudo ifup wlan0
ignoring unkown interface waln0=wlan0.

---

### Post by msh559 on 2010-07-30
SOLVED!!!! 
Power trick i guess
remove battery
unplug ac
hold power button for 15 sec
reinstall battery
plug in ac and restart!!!1

---

