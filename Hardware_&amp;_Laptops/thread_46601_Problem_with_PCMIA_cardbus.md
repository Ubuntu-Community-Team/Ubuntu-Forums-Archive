---
title: "Problem with PCMIA cardbus?"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by Magitek on 2005-07-05
Hi,
Sorry for the newbie question. I decided I have had enough of Windows so I've moved to Kubuntu linux. Most the hardware seems to have installed fine although i'm not sure about the PCMIA cardbus. I'm trying to connect to my wireless router but my wireless card is not recognised atall. KWifiManger shows there is no wireless card even though I have one plugged in. I'm not sure whether the not recognising if my WLAN PCMIA card is due to the cardbus not working or the WLAN card itself. But surely the power LED should come on the card even if the device is not recognised, this isn't happening.  Thanks in advance, your advice would help me out allot. Cheers, Joe.

---

### Post by Ken.Lank on 2005-07-05
OK, I'm still a newbie, but I'll start out with this.  I'm sure someone can jump in and help once you post your results.

run "lspci" ... does your adapter show up in the results?  If yes, then run "iwconfig", does the port show up and does it see it as  wireless card?

If you could post the results of these steps as well as information about the type of card, I'm sure one of the more experienced users can take over in helping you out.

---

### Post by Magitek on 2005-07-05
Thanks Ken,
My Cardbus driver seems to be installed. I have the ENE CB1410 Cardbus controller driver so it seems to have installed the correct driver. When doing iwconfig i got:

lo                  no wireless extensions.

eth0              no wireless extensions.

sit0                no wireless extensions.

The company I bought the wireless adapter off said it was supported by linux [http://www.shop4usb.co.uk/oscommerce-2.2ms2/catalog/product_info.php?cPath=29&products_id=42](http://www.shop4usb.co.uk/oscommerce-2.2ms2/catalog/product_info.php?cPath=29&products_id=42). I'm not sure on the chipset it uses. Any ideas what to do next?

---

### Post by Magitek on 2005-07-06
OK, I tried using my other PCMCIA WLAN adapter which is Microsoft MN-720. I installed ndiswrapper using the instructions from here: [https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)
The lights on my card haven't come on, but Kwifimanger achnowledges when the card is plugged in and says it has good signal .etc. To activate my card it is required for me to type  "modprobe ndiswrapper". I can't connect to a network however in KwifiManager, it says no network found, when clearly there is a wireless connection around me. I need a hand editing the /etc/network/interfaces file, I can't edit it from KDE it won't seem to let me it just crashes. My last file said there where two few parameters when running "ifup wlan0".


Now I have changed it to, as in the how-tut([https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29))

[INDENT]# This file describes the network interfaces available on your system 
   # and how to activate them. For more information, see interfaces(5).

   # The loopback network interface
     auto lo
     iface lo inet loopback

   # The primary network interface
     #auto eth0
     #iface eth0 inet static
     # address 192.168.2.3
     # netmask 255.255.255.0
     # network 192.168.2.0
     # broadcast 192.168.2.255
     # gateway 192.168.2.1
     # # dns-* options are implemented by the resolvconf package, if installed
     # dns-nameservers XXX

   # The wireless network interface   
     auto wlan0
     iface wlan0 inet dhcp
 netmask 255.255.255.0
 network 192.168.2.0
 broadcast 192.168.2.255
 gateway 192.168.2.1
 # dns-* options are implemented by the resolvconf package, if installed
 dns-nameservers XXX
 wireless_keymode XXX
 wireless_key XXX
 wireless_essid XXX[/INDENT]

Please help me fill in these parameters:

[INDENT]dns-nameservers 
wireless_keymode 
wireless_key 
wireless_essid
broadcast
network[/INDENT]

The only information I know is:

[INDENT]IP Adress: 192.168.1.3
Netmask: 255.255.255.0
Defualt gateway: 192.168.1.1
DNS Server: 192.168.1.1[/INDENT]

How can I find them out?

Please help,  I would really appreciate it. Cheers, Joe.

---

### Post by az on 2005-07-06
Please send the output from:

find /sys/class/pcmcia_socket
lspci


Is this bug relevant?
[https://bugzilla.ubuntu.com/show_bug.cgi?id=8575](https://bugzilla.ubuntu.com/show_bug.cgi?id=8575)

---

### Post by Magitek on 2005-07-07
Hi, here si what I got:

Input:

```
root@ubuntu:~# find /sys/class/pcmcia_socket
```

Output:

```
/sys/class/pcmcia_socket
/sys/class/pcmcia_socket/pcmcia_socket0
/sys/class/pcmcia_socket/pcmcia_socket0/driver
/sys/class/pcmcia_socket/pcmcia_socket0/device
/sys/class/pcmcia_socket/pcmcia_socket0/card_eject
/sys/class/pcmcia_socket/pcmcia_socket0/card_insert
/sys/class/pcmcia_socket/pcmcia_socket0/card_vcc
/sys/class/pcmcia_socket/pcmcia_socket0/card_vpp
/sys/class/pcmcia_socket/pcmcia_socket0/card_voltage
/sys/class/pcmcia_socket/pcmcia_socket0/card_type
```

Input:

```
root@ubuntu:~# lspci
```

Output:

```
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 14)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Radeon Mobility 9000 M9] (rev 01)
0000:02:00.0 Network controller: Broadcom Corporation: Unknown device 4325 (rev 02)
```

As I said before KWifiManager shows there is a card. It says it has full signal strength "ULTIMATE Signal strength 100", but I cannot  find a network when choosing "Scan for Networks...". I don't know if my card is really working or not, or whether kWifimanager just thinks it is because the drivers present. NDISWRAPPER identifies the hardwares there .etc.

I'm using the Microsoft MN-720 driver I found at: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
I chose option one from there.

Cheers, Joe.

---

### Post by Magitek on 2005-07-07
Also let me get this right fior wireless lan to work wired lan must be disabled right? I am not connected to a wired lan though, but the network port can't work if the wlan is on and visa versa right?

Anyway when I try:

```
ifup wlan0
```

it says:

```
Ignoring unknown interface wlan0=wlan0.
```

I can mount/unmount my normal lan (eth0) fine.

Is it a problem with my /etc/network/interfaces file?

I did a fresh install because I didn't want to wreck that file anymore so now my file says:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet static
	address 192.168.1.3
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1
```

KDE Control module gets ugly whenever I try to change network settings infact it won't let me in the gui. Is there a guide to writing to the interfaces file?

---

### Post by Magitek on 2005-07-07
I think I might bite the bullet and buy a Netgear WG511T WiFi card, according to this:
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards/](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards/) 
(wish I found this earlier) it works out of the box, also it supports 11g and I have an 11g router so thats a bonus. I only hope it works...

Also my MN-720 broke(!?) and doesn't seem to work after I've tried installing it on linux. That's Microsoft for ya ;). Thanks anyway guys.

---

