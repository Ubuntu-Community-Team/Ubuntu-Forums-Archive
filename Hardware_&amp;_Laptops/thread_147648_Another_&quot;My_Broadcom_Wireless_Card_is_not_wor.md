---
title: "Another &quot;My Broadcom Wireless Card is not working&quot; post"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by Tiede on 2006-03-20
I have an Acer 3003 WLMi that used to work great on Breezy before.
Ever since I upgraded a week ago from kernel 2.6.12-9-386 to 2.6.12-10-386 it stopped working altogether (Light not coming on at all, no connectivity, the whole nine yards...) I remember  having the exact same problem on Dapper before I downgraded to Breezy a little over a month ago: Everything says I should be connected perfectly, but nothing really works... Look at these outputs for example.
ifconfig:
```
wlan0     Lien encap:Ethernet  HWaddr 00:14:A4:4A:F2:F3  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interruption:17 Mémoire:e2000000-e2002000 

```

iwconfig:
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

lshal: (the relevant part of course :D)
```
udi = '/org/freedesktop/Hal/devices/net_00_14_a4_4a_f2_f3'
  info.udi = '/org/freedesktop/Hal/devices/net_00_14_a4_4a_f2_f3'  (string)
  linux.subsystem = 'net'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  net.80211.mac_address = 88655721203  (0x14a44af2f3)  (uint64)
  info.product = 'Networking Interface'  (string)
  net.interface_up = false  (bool)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.linux.ifindex = 3  (0x3)  (int)
  net.address = '00:14:a4:4a:f2:f3'  (string)
  net.interface = 'wlan0'  (string)
  net.physical_device = '/org/freedesktop/Hal/devices/pci_14e4_4318'  (string)
  info.capabilities = {'net', 'net.80211'} (string list)
  info.category = 'net.80211'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_14e4_4318'  (string)
  linux.sysfs_path = '/sys/class/net/wlan0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_14e4_4318'
  info.udi = '/org/freedesktop/Hal/devices/pci_14e4_4318'  (string)
  linux.subsystem = 'pci'  (string)
  linux.hotplug_type = 1  (0x1)  (int)
  pci.subsys_product = 'Unknown (0x0312)'  (string)
  pci.subsys_vendor = 'AMBIT Microsystem Corp.'  (string)
  info.product = 'Unknown (0x4318)'  (string)
  pci.product = 'Unknown (0x4318)'  (string)
  info.vendor = 'Broadcom Corporation'  (string)
  pci.vendor = 'Broadcom Corporation'  (string)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.device_class = 2  (0x2)  (int)
  pci.subsys_vendor_id = 5224  (0x1468)  (int)
  pci.subsys_product_id = 786  (0x312)  (int)
  pci.vendor_id = 5348  (0x14e4)  (int)
  pci.product_id = 17176  (0x4318)  (int)
  info.linux.driver = 'ndiswrapper'  (string)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.bus = 'pci'  (string)
  linux.sysfs_path_device = '/sys/devices/pci0000:00/0000:00:0b.0'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0b.0'  (string)

```

lshw
```
tuxed
        *-network:1
             description: Wireless interface
             product: Broadcom Corporation
             vendor: Broadcom Corporation
             physical id: b
             bus info: pci@00:0b.0
             logical name: wlan0
             version: 02
             serial: 00:14:a4:4a:f2:f3
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical wireless
             configuration: broadcast=yes driver=ndiswrapper multicast=yes wireless=IEEE 802.11g
             resources: iomemory:e2000000-e2001fff irq:17

```

lspci:
```
0000:00:0b.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)

```

What is the difference between linux-image-2.6.12-9-386 and linux-image 2.6.12-10-386 pertaining to wireless cards in general and Broadcom chipsets in particular. I searched the modules for the bcm43xx.ko faulty driver that is in Dapper, but it is not present. The only module in the list that is for Broacom is bcm203.ko, which I don't believe has any effect on my card. I wanna stress that my wireless card worked in 2.6.12-9-386... (I was having [another problem related to wireless connectivity](http://ubuntuforums.org/showpost.php?p=801953&postcount=39) in it also, but at least the card was properly activated.)

EDIT: The light on my laptop came on once today when I plugged a USB printer to my computer while it was booting. I thought it was fixed and shut it down, but it won't come back on again. I am thus suspectig there might be a conflict or other reason why it is not working. Is there a way I can check that out. Any help/comment welcome.

---

### Post by Tiede on 2006-03-23
Just a quick question. Does anyone know if the issue with Broadcom Cards has been fixed or a workaround. Wireless connectivity was the only reason why I am still on breezy, and now that it stopped working here to... (I've heard of regression already, but in the same version of an OS... :-?)

I used dapper before and I ***know*** everything else will work for me, so if anyone has any idea about how to fix that wireless problem, I'll be all set! :)

---

### Post by Tiede on 2006-03-24
how many times does one have to "bump" a thread of such importance?

---

### Post by SqRt7744 on 2006-03-24
[COLOR="Red"]EDIT[/COLOR]: if below doensn't work for you look at this thread: 
[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom)

I installed breezy on a friend's laptop and she is also having some trouble with her wireless card.  The way I dealt with it is as follows (this may not be the best way, but it seemed to work for me).  
Find out the correct wireless chipset by typing 
lspci 
in a terminal.
Then go to 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
and get the correct drivers (it may be in the form of an exe in which case you must use wine to unpack them, or unpack on windows machine and put on usb stick), then under system->admin->windows wireless drivers, add driver.  This is just a frontend for ndiswrapper so make sure you have the latest version installed from the repos.
In a terminal type
sudo ifdown /dev/wlan0
sudo modprobe -r ndiswrapper
sudo modprobe -i ndiswrapper
sudo ifup /dev/wlan0
this just takes down the wireless connection, reloads the ndiswrapper, and starts the connection again.  This fixed it for me!  You may have to go into network settings and reactivate the wireless connection if it didn't come up.
in a terminal type
ifconfig
and make sure that wlan0 has been assigned a ip.  try dhclient if not (this shouldn't be necessary though).

Good luck.

---

### Post by Tiede on 2006-03-25
happy to know someone out there is reading my posts! :D

I tried the steps you mentionned many times already, and they have proven themselves very unhelpful (at least for me). It may be because the wlan interface is correctly ifupped (or at least ubuntu think it is) but it isn't really... I don't know.
The only time I got it working was that one time I was poking around my pc with my usb printer, I plugged it while the PC was starting up, it locked, I rebooted, and then the wireless card came one during the next boot process and seemed to be working flawlessly. Haven't been able to reproduce the situation though...
I am also already subscribed to the thread you mentioned, and am actively participating in it. But it hasn't been able to help me for some reason. It's like when the kernel passed the 2.6.12-10 line, it decided to blow ndiswrapper+bcm away :(
I am happy though that you answered. If I hadn't tried that step, it might have helped. Try it again for old times sake though, but it didn't work (as I feared it wouldn't).
I guess I am going to have to switch to windows every time I need wireless access for a while. :-? Don't want to, but I must.

---

### Post by SqRt7744 on 2006-03-25
I sorry it didn't help!  The fact that it worked *once* means that it must be able to. I doubt it has anything to do with the kernel upgrade, something just isn't set right.  When Dapper is officially released I'd do a clean upgrade (back up all your files, and let it set itself up without baggage from current install).  I've heard they've done a lot of work in the broadcom wireless department.

---

### Post by Tiede on 2006-03-27
although I always make sure to retrace my steps when I'm fiddling with things on my laptop, I do like the idea of a clean install and will surely try it again!
Thing is, I already did that w/ Dapper flight 4, and the bcm43xx (The new broadcom driver) wasn't able to up my card then... a dist-upgrade to flight 5 equivalent did not resolve it either, so I am a little sceptic. But, as you said, there is so much roaring in the Linux Broacom department that it can only be a good thing.
For now, I can only cross my fingers and hope I'll have wireless access again in my ubunubox in June. :-?
In the mean time, I am stuck using windows, which, for some reason, is more and more awkward-looking everyday...

---

