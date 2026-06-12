---
title: "Wireless troubles first, more to come..."
date: 2008-10-29
forum: General Help
---

### Post by 34917426 on 2008-10-29
There's more to come on this, I wanted to deal with the wireless first so I can upload screenshots of another problem. 

The daemon.log indicates that the device can be detected, but the "link is not ready" and it has an an error setting the ESSID to '' making it an invalid arguement, thus deactivating the device. 

...computers... 

The driver is detected fully in Terminal and has no problems. nm-applet cannot detect any networks. manually entering our router in solves nothing. 

I can give more daemon log messages as neccessary. 

cliff notes: Driver loaded and working fine (so I think) but no networks can be detected. And I live in a network-infested area.

EDIT: forgot. Ubuntu 7.10 gutsy gibbon, compaq e500 w/319mb ram. WL541C cheapo wireless card. It was working fine a couple of months ago, then suddenly quit. No hardware or software upgrades in the mean time.

---

### Post by ryanhaigh on 2008-10-29
Have you tried using the commandline tools to establish the connection?

You can use iwlist  to scan for wireless networks.

```
iwlist wlan0 scan
```

You can then use iwconfig to connect to the access point:

```
iwconfig wlan0 essid "yournetworid" mode managed commit
dhclient wlan0
```

If the network you are using employs encryption you will also need to provide the key. See the man page for iwconfig for more info on using this command.

You say that the driver is detected but what driver is in use? Are you using ndiswrapper? What chipset is used by your card?

EDIT: note that wlan0 was for one of my old cards your device may using something different.

---

### Post by 34917426 on 2008-10-29
```
 username@username-tokenring:~$ **iwlist wlan0 scan**
wlan0       No scan results
username@username-tokenring:~$ **iwconfig wlan0 essid XXXXXXXXXXXXXXXXX mode managed commit dhclient wlan0**
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
username@username-tokenring:~$ ** iwconfig**
lo      no wireless extensions.

wlan0   IEEE 802.11g  ESSID:off/any
        Mode:Managed  Frequency: 2.437GHz Access Point: Not-Associated
        Bit Rate: 54 Mb/s  Tx-Power: 10dBm  Sensitivity=0/3
        RTS thr: off  Fragment thr:off
        Power Management:off
        Link Quality:0 Signal level:0 Noise level:0
        Rx invalid nwid:0 Rx invalid crypt: 0 Rx invalid frag:0
        Tx excessive retries:0 Invalid misc:0 Missed beacon:0

username@username-tokenring:~$ ** sudo lshw -C network**
[sudo] password for username:
  *-network
      description: Wireless interface
      product: ACX 111 54Mbps Wireless Interface
      vendor: Texas Instruments
      physical id: 3
      bus info: pci@0000:02:00.0
      logical name: wlan0
      version: 00
      serial: 00:50:18:42:d6:fe
      width: 32bits
      clock: 33MHz
      capabilities: pm bus_master cap_list ethernet physical wireless
      configuration: broadcast=yes driver=ndiswrapper+gplus driverversion=1.45+D-Link,04/09/2004,6.0.0.18 latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

"username" has been subsituted for my actual username...

[edit]what you see in bold is my actual typing. [/edit]
[edit2]XXXXXXXXXXXXX is the network name but hidden for...reasons :)[/edit2]

---

### Post by ryanhaigh on 2008-10-29
ok well as you can see you didn't have permission to set the wireless network using your standard user credentials, the command needs to be run as root/sudo:
```
sudo iwconfig wlan0 essid XXXXXXXX mode managed commit
```
The dhclient part is actually a second command and should not be on the same line:
```
sudo dhclient wlan0
```

The fact that the scan isn't showing anything doesn't look promising for you, I also see that you are indeed using ndiswrapper. You might be able to find newer or better drivers which may allow the card to work. Check the ndiswrapper home page there is a listing of cards/chipsets and the best/working drivers. Also you should look into whether that card is supported by a native linux driver, it my require compilation but could be as easy as using module-assistant.

---

### Post by 34917426 on 2008-10-30
```

username@username-tokenring:~$ **sudo iwlist wlan0 scan**
[sudo] password for username:
wlan0    No scan results
username@username-tokenring:~$ **sudo iwconfig wlan0 essid XXXXXXXX **mode managed commit
username@username-tokenring:~$ **sudo dhclient wlan0**
There is already a pid file /var/run/dhclient.pid with pid 6039
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:50:18:42:d6:fe
Sending on   LPF/wlan0/00:50:18:42:d6:fe
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS recieved. 
No working leases in persistent database - sleeping. 
```

Here is a System Log daemon.log readout. 

```

username-tokenring Network Manager: <info> wlan0: Device is fully-supported using driver 'ndiswrapper'.
username-tokenring Network Manager: <info> nm_device_init(): waiting for device's worker thread to start
username-tokenring Network Manager: <info> nm_device_init(): device's worker thread started, continuing. 
username-tokenring Network Manager: <info> Now managing wireless (802.11) device 'wlan0'.
username-tokenring Network Manager: <info> Deactivating device wlan0. 
username-tokenring Network Manager: <WARN> nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument
```

kern.log says this:

```

username-tokenring kernel: [   74.176000] lo: Disabled Privacy Extensions
username-tokenring kernel: [   74.176000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
username-tokenring kernel: [   74.256000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
username-tokenring kernel: [   74.176000] apm: overridden by ACPI.
username-tokenring kernel: [   74.176000] Failure registering capabilities with primary security module. 

<and in the messages column, it says this:>

username-tokenring kernel: [   62.468000] ndiswrapper version 1.45 loaded (smp=yes)
username-tokenring kernel: [   62.604000] ndiswrapper: driver gplus (D-Link,04/09/2004,6.0.0.18) loaded
username-tokenring kernel: [   62.604000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
username-tokenring kernel: [   62.604000] ACPI: PCI Interrupt 0000:02:000.0[A] -> Link [C142] -> GSI 11 (level, low) -> IRQ 11
username-tokenring kernel: [   62.204000] ndiswrapper: using IRQ 11
username-tokenring kernel: [   63.452000] wlan0: ethernet device 00:50:18:42:d6:fe using NDIS driver: gplus, version: 0x5000200, NDIS version: 0x501, vendor: 'TNET1130', 104c:9066.5.conf
username-tokenring kernel: [   63.452000] wlan0: encryption modes supported: WEP; TKIP with WPA
username-tokenring kernel: [   63.460000] usbcore: registered new interface driver ndiswrapper
```


error_log says it is unable to find IP address for server name "username-tokenring"!



Tough stuff. "All this computer hacking is making me thirsty. I'll order a tab." -Homer Simpson

---

### Post by ryanhaigh on 2008-10-30
Once you try to connect using the iwconfig wlan0 essid... command can you just run ```
iwconfig wlan0
``` to check that the card has actually established a connection to the router. Check it a couple of times and wait a few seconds to allow time for the association.

Have you looked into using the native driver or trying an alternate driver for ndiswrapper?

---

### Post by 34917426 on 2008-10-30
> **ryanhaigh said:**
> Once you try to connect using the iwconfig wlan0 essid... command can you just run ```
iwconfig wlan0
``` to check that the card has actually established a connection to the router. Check it a couple of times and wait a few seconds to allow time for the association.

Have you looked into using the native driver or trying an alternate driver for ndiswrapper?

No I have not looked into another driver - nothing has changed since awhile back when it was working perfectly fine. It'd auto-connect to the home network when in range, no biggie. 

I don't know how to use the native driver, but I did try 'ndiswrapper -l' and it was fine. or so it said. Isn't there something wrong with the ESSID being set to '' as in, nothing?

---

### Post by ryanhaigh on 2008-10-30
Yes the ESSID should update, that is why I asked you to run the iwconfig command again. So step by step do this:

1.Try and connect to the router:
```
sudo iwconfig wlan0 essid XXXXXXXX mode managed commit
```
2.Wait a few seconds to allow it time to associate
3.Check if the connection has been established:
```
sudo iwconfig wlan0
```
4.If it connected the ESSID should be set to the right name and you should see that you are associated with an access point. If not repeat the above steps a couple of times and if it doesn't work its not going to.
5.If you are now connected try and get an ip address:
```
sudo dhclient wlan0
```

The fact that the device and driver were working and now are not would seem to indicate that something has changed. Perhaps you updated to a new kernel? If so the old one should be in your grub list, you can try booting with the old kernel entry and see if the device works again. 

When you initially set the system up did you compile ndiswrapper yourself? If so the module will need to be recompiled after kernel upgrades.

Unfortunately sometime new software has regressions which may be responsible for your problems. At least you know there is a native linux driver to fall back on. Also you should try searching launchpad for bug reports related to ndiswrapper and your card.

---

### Post by 34917426 on 2008-12-07
Well geez, all of a sudden, on its on accord, it decides to work...if only for a short time!

Here's the iwconfig readout:

> XXXXXXXXXXXXXXXXX@XXXXXXXXXXXXXX-tokenring:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"XXXXXXXXXXX"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:40:10:10:00:03   
          Bit Rate=24 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


X's have replaced obvious traits...

Moving on to the other problem with ubuntu 7.10 I have: with or without an internet connection, without warning, some process (of which I have yet to discover) will "cap" the memory far below the allocated amount and levy a heavy drag on all system processes. The load reading can climb into the 10's, usually stopping at around 14. System monitor will show nothing going on unusual. Here are pictures:

[[IMG]http://i26.photobucket.com/albums/c113/Starofire/Random/th_Screenshot.png[/IMG]](http://s26.photobucket.com/albums/c113/Starofire/Random/?action=view&current=Screenshot.png)[[IMG]http://i26.photobucket.com/albums/c113/Starofire/Random/th_Screenshot-5.png[/IMG]](http://s26.photobucket.com/albums/c113/Starofire/Random/?action=view&current=Screenshot-5.png)[[IMG]http://i26.photobucket.com/albums/c113/Starofire/Random/th_Screenshot-3.png[/IMG]](http://s26.photobucket.com/albums/c113/Starofire/Random/?action=view&current=Screenshot-3.png)[[IMG]http://i26.photobucket.com/albums/c113/Starofire/Random/th_Screenshot-2.png[/IMG]](http://s26.photobucket.com/albums/c113/Starofire/Random/?action=view&current=Screenshot-2.png)[[IMG]http://i26.photobucket.com/albums/c113/Starofire/Random/th_Screenshot-1.png[/IMG]](http://s26.photobucket.com/albums/c113/Starofire/Random/?action=view&current=Screenshot-1.png)

Ideas?

Also: why is there no contrast/brightness control in Linux? (Some people have been able to adjust it in one of the configuration apps under the System menu, but I have looked where they have said it was and it wasn't there) Is there some paranoia towards users adjusting brightness/contrast? It doesn't turn out to a be an issue when it's full light inside, but when all the lights are off at night you'd have to wear sunglasses to read the screen...(and I did numerous times).

---

### Post by 34917426 on 2008-12-12
Nobody?

---

