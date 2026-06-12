---
title: "(Jaunty) Broadcom 4312 Wireless Not Working"
date: 2009-05-09
forum: Hardware
---

### Post by banduan on 2009-05-09
EDIT: 
Issue (mostly) resolved.
The problem was quite likely with the hard switch for wireless+bluetooth (Compaq combined both), which *does not work properly* after Ubuntu loads but *does* before.
If you have an issue with wireless, consider this one possibility. Try restarting then hitting the wireless switch and see if your wireless suddenly works.

-----------------
I recently upgraded from Intrepid to Jaunty on my Compaq CQ40
Wireless under 8.10 was working fine.

When I upgraded, wireless was working fine (though speakers weren't that's another issue).

Something happened though during this week, maybe an update or maybe the fact that I used Janitor to delete an outdated kernel. 
Now my wi-fi refuses to detect my wireless connection.


[LIST]
[*]Broadcom turns up under lshw as neither claimed, unclaimed, disabled or whatever. No tag is on it. i.e. it's probably working, just not detecting anything.
[*]Hardware drivers shows the STA driver as installed and working.
[*]Wired connection still works
[*]Wireless router itself still works, I have other laptops connecting to it.
[*]I always had two ATA softreset errors when booting Jaunty. Mind you wireless was working before even with these errors.
[*]the laptop has no wifi hard switch.
[/LIST]
I reinstalled (clean install) and used the opportunity to upgrade to Ubuntu 64. Wifi still not detected.

I replaced gnome network manager with WICD. Wifi still not detected.

At my wits end on this right now. Any help very much appreciated

---

### Post by benmoran on 2009-05-09
I have a Dell Inspiron 1501 with a Broadcom card. When I recently upgraded to the new kernel, my wireless stopped working as well. I have "proposed" and "unsupported" updates checked in the sources page, so I was assuming that was it. The new (unworking) kernel is .12, so for now I just hit escape at the grub menu and use the older .11 kernel. 

Give it a shot and see if it works for you.

---

### Post by banduan on 2009-05-09
I believe .11 is the only one I have on my laptop. Grub menu only gives me that kernel as an option anyway.

---

### Post by banduan on 2009-05-10
Further updates.

I installed (clean install) 8.10 64-bit- which was frustrating because the process was hit-and-miss.

Once installed, in I fiddled around with Hardware Drivers and managed to get Boradcomm STA working - and my wifi was detected.

But it refused to let me log on after I set the password for my wifi (on WEP).
I then had the incredible foresight to delete the connection, hoping once it detected the connection again maybe I could get it working.
It was never detected again.
:(

Using wired connection to update now, hoping it'd work. At least I got sound back thanks to going back to Intrepid.

---

### Post by fa2k on 2009-05-10
I have a Dell Inspiron 1501. I can't enable the wireless either in Windows Vista or in Ubuntu 9.04 (kernel 2.6.28-11-generic). The device is not found by any of the OS'es. The timing of this post leads me to believe that this is related. My problems started today. In my case, there is no mention of the Broadcom in lshw.

---

### Post by banduan on 2009-05-10
I don't think yours is 100% related. My wireless device is installed but it can't discover my wifi connection.

Check your hard switch.

---

### Post by banduan on 2009-05-11
some outputs:

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:e2:76:b8  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fee2:76b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1333 errors:0 dropped:79709253 overruns:0 frame:0
          TX packets:1053 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1006348 (1.0 MB)  TX bytes:171188 (171.1 KB)
          Interrupt:250 

eth1      Link encap:Ethernet  HWaddr 00:21:00:7e:21:15  
          inet6 addr: fe80::221:ff:fe7e:2115/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)
```lshw -c network
```
*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:7e:21:15
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:e2:76:b8
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.2 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:d3:49:51:3f:87
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```contents of etc/network/interface
```
auto lo
iface lo inet loopback

```

---

### Post by Peter09 on 2009-05-11
Did you say that you had removed network manager?

---

### Post by banduan on 2009-05-11
did so earlier on to replace with wicd to see if that would detect.

since then I've done a clean install of ubuntu 810 amd64

---

### Post by Peter09 on 2009-05-11
Can you see no wireless networks when you left click on the network icon.

What do you see when you right click on the network icon?

---

### Post by jtappin on 2009-05-11
This sounds like the same problem I had on my HP MiniNote:
[http://ubuntuforums.org/showthread.php?t=1148771]("http://ubuntuforums.org/showthread.php?t=1148771")

The problem there was that the restricted drivers detection failed to find the need for the b43-fwcutter package. Install that and I think you'll be in business.

---

### Post by banduan on 2009-05-11
Peter, if I'm not connected via wired, I see the network icon with an orange triangle with an exclamation mark on it. Clicking on it just shows wired heading with just the usual wired connection listed as disconnected and wireless networks heading without any connections listed. 

jtap, I tried isntalling the cutter program very early on, it did nothing. I must admit though I've reinstalled twice since then so it might be different this time round, maybe I'll give it another go. Bear in mind though that my broadcomm firmware driver (STA) installs fine under Hardware Drivers.

---

### Post by Peter09 on 2009-05-11
As an experiment in 

/etc/modules/blacklist

 put the line

wl0

and then reboot.

---

### Post by banduan on 2009-05-11
> **Peter09 said:**
> As an experiment in 

/etc/modules/blacklist

 put the line

wl0

and then reboot.

There isn't a modules folder. There is however modprobe.d. I'll try in there first.

Strangely enough theres a separate blacklist for bcm43, probably set by STA driver to just blacklist every other driver for broadcom.

---

### Post by banduan on 2009-05-11
Didn't work. I'll try removing a blacklisted item from the bcm43 blacklist though.

---

### Post by tremmert on 2009-05-11
I would like to also add that my hp mini 1000's wifi is not working either after the upgrade.  The wireless switch light is like amber, not the normal blue.  I can select the old kernel through grub and it works fine...

TOmmy

---

### Post by banduan on 2009-05-12
Your issue might not quite be the same.
Mine doesn't work even with old kernel.

However, might be worth noting that on my laptop what perhaps should be the wifi button is actually the bluetooth button. There's no hard wifi switch.

edit: i have the niggling suspicion this may be the cause. I'm gonna start abusing that button.

---

### Post by banduan on 2009-05-12
PROGRESS!
After hitting the wifi button repeatedly, at increasing seconds interval, wifi is now detected. I'm at work now though so I can't access those wifi connections (theyre somebody else's offices).

That button had all this while only worked for *bluetooth.* Even stranger, hitting the button again after wifi connections have been detected does not remove the wifi...... 8(

Now all that remains to be resolved is the login. Fingers crossed it'll work.

---

### Post by banduan on 2009-05-12
Checking the connection at home, the wifi is now detected.

The source of the problem may be the hard switch. It does not work for wifi when Ubuntu has loaded, but during startup I hit the button and presto. There's the wireless. Weird stuff.

---

### Post by p3car on 2009-06-23
I have a similar situation on Dell Vostro 1320 with Broadcom BCM 4312 (rev 1).
The driver seems to be in place, if I run a 
```
sudo iwlist eth1 scan
```I get a list of available networks. Network manager insists that "wireless is disabled"

I installed wicd (which will uninstall network manager) and it worked. I could connect to my wireless network. I reinstalled network manager and it still says "wireless is disabled".

I have a hardware switch on the side of the computer, if I turn it off the lights for bluetooth and network on the laptod will go off. 

I'd be happy to run wicd, but I also use an 3G USB modem, which network manager will detect and connect to, wicd doesn't seem to offer this functionality.

---

### Post by napzilla on 2009-07-22
**Update:** Commenting out everything but the "lo" interface in /etc/network/interfaces resolved the issue.

Okay, this is a bit odd. I'm using an Inspiron 6400 (aka 1501) with Intrepid, and I'm having exactly the opposite problem. I can connect to wireless networks with little or no trouble, but I cannot for the life of me convince Ubuntu to recognize a wired connection. Even now, I'm sitting right next to the bloody router with a network cable hanging out the back of my computer, but I have to use the wireless connection to get online. So maybe if we somehow merge our problems together, it'll work both ways...
:D

---

### Post by dckrinke on 2009-11-15
I was using ubuntu 8.04 successfully with my broadcom BC4312, Things were working so well I decided to upgrade to 9.10. When I booted to the liveCD, I could choose the B43-fwcutter proprietary driver and connect to my home wireless router. However, when I installed to my hard drive and rebooted, the BCM4312 no longer works. I tried Wireless Troubleshooting and get: 

5.2.2.&#8195;Check for device recognition

   1. Open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:61:2e:8e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.110 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:c000(size=256) memory:f8200000-f8200fff memory:c0000000-c001ffff(prefetchable)


My kerner is: 
Linux dennis-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

What should I try? Should I go back to 8.04? 

Thank you,
Dennis Krinke

---

