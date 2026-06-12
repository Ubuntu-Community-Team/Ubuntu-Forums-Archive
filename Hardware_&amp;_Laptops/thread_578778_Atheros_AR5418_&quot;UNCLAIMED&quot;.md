---
title: "Atheros AR5418 &quot;UNCLAIMED&quot;"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by klaasvanschelven on 2007-10-17
Hi,

I replied to an old message earlier tonight ([http://ubuntuforums.org/showthread.php?t=565514](http://ubuntuforums.org/showthread.php?t=565514)) but just realized that probably isn't "the way". Sorry for doubleposting 

I've installed both
linux-restricted-modules for my kernel and
madwifi-tools "tools for the Multiband Atheros Driver for WiFi"

I have Ubuntu 7.10 (yes I know I'm a day early, but it's the only thing that I got to work to some degree).

This is what lshw has to say:

klaas@thinkpad:~$ sudo lshw -C network
[sudo] password for klaas:
*-network
description: Ethernet interface
product: 82573L Gigabit Ethernet Controller
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 00
serial: 00:1a:6b:67:85:ca
size: 100MB/s
capacity: 1GB/s
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.2.102 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
*-network UNCLAIMED
description: Network controller
product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
vendor: Atheros Communications, Inc.
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list
configuration: latency=0

Help would be very much appreciated - I've been working an evening on getting the graphics to work and still have no sound. 

Klaas

---

### Post by blenderfish on 2007-10-20
I am having the exact same issue.  I am using a Thinkpad z61m with the AR5418 Atheros wireless card.  I have gotten this working previously using ndiswrapper in Feisty, and in Dapper.  I have installed ndiswrapper, which shows that the driver is installed and the device is present, but when I run lshw, the device is unclaimed.  I do not see a wireless interface available in network settings.  What is my next step?  Here are my outputs:

sudo lshw -C network
```
:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5752M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:16:36:cf:a1:c4
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5752m-v3.22 ip=192.168.0.198 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=1GB/s
  *-network UNCLAIMED
       description: Network controller
       product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

```

iwconfig
```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

```

lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752M Gigabit Ethernet PCI Express (rev 02)
03:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
15:00.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
15:00.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
15:00.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
15:00.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

---

### Post by mlilien on 2007-10-23
I'm having the same problem on my Levovo t60p.  I had it working with madwifi in feisty, but can't get that to work in Gutsy.  The lenovo site says that it's supposed to have an ipw3945 card and I was pretty sure that that's what I had.  Is that the case?  Does Gutsy just not recognize it as ipw3945?
I know that ipw3945 is supposed to be supported in the restricted drivers manager, but it doesn't show up  there.

Thanks in advance for any help.

---

### Post by AFPilot on 2007-10-23
Not sure if this should be in this forum or networking - wireless?? Six days and no helpful response definitely has me worried. I have the X60 and get the same results with lshw -C network. Not sure what to do, have been scouring the forums and Google with no luck.

---

### Post by Room 34 on 2007-10-24
I am having the same problem with an Atheros AR5006EG in my MacBook. What's really weird though is that it WAS working, just fine, when I first did my Gutsy install.  It wasn't until last night, shortly after I installed a bunch of Ubuntu Studio packages using Synaptic Package Manager (which may or may not have anything to do with it), and then rebooted, that suddenly my wireless network disappeared and some troubleshooting led me (still fruitlessly) to this same diagnosis.

Very little information is out there about "network UNCLAIMED" and what to do about it.

FWIW I started another thread in the Apple Intel Users subforum: [http://ubuntuforums.org/showthread.php?t=589684](http://ubuntuforums.org/showthread.php?t=589684)

---

### Post by AFPilot on 2007-10-24
Ok, well since I don't want to go back to Windows and I have to have wireless I've managed to get the device recognized and working using ndiswrapper. It was quite easy and is explained in detail at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

Additionally, I was able to get the driver from this site [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/") 

Which includes this information as item 63:
Card: Atheros AR5418
      Chipset: AR5418
      pciid: 168c:0024
      Driver: 7iwc21ww.exe (use cabextract to extract files) from [http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-66449](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-66449)
      Other: Tested with ndiswrapper 1.42 (svn revision 2315) and kernel 2.6.21-smp. Just tested IEEE 802.11bg, not a or n and just WEP. Also tested ndiswrapper 1.43 on kernel 2.6.20. On vanilla kernels, it&#8217;s necessary to disable CONFIG_4KSTACKS by enabling &#8216;Kernel Hacking&#8217; and making sure the option to use 4K stacks is disabled.

I used the ndisgtk and it took two seconds but installed net5416 ???, however it seems to work just fine. It immediately started working and I could scan for networks. I've not connected to anything requiring WPA yet but running the following showed that it was supported:

sudo depmod -a
sudo modprobe ndiswrapper

tail /var/log/messages


I know it'll probably leave a bad taste in some folks mouth having to use these drivers but until it's resolved at least it means I can continue to use Ubuntu.

Cheers


UPDATE - I've successfully used WPA and am logged.

---

### Post by mlilien on 2007-10-24
In a thread on the networking/wireless forum, rustybronco pointed me to this thread
[http://ubuntuforums.org/showthread.p...t=AR5418+GUTSY](http://ubuntuforums.org/showthread.p...t=AR5418+GUTSY)
which solved it with madwifi.  

Worked perfectly.

---

### Post by AFPilot on 2007-10-24
Full link here: 
[http://ubuntuforums.org/showthread.php?t=572971&highlight=AR5418+GUTSY]("http://ubuntuforums.org/showthread.php?t=572971&highlight=AR5418+GUTSY")

---

### Post by charles_316 on 2007-11-15
i used ntdisgk and installed the driver from the WinXp/2k folder and it says the hardware is present but i still cant connect?

any ideas?

---

### Post by klaasvanschelven on 2008-05-06
Half a year later, I'm trying again (I'm not sure if the etiquette is to reopen the post but it's nr.2 in Google and still has no working answer at the bottom).

I've tried the madwifi approach as detailed here:
[http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008](http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008) (via [http://ubuntuforums.org/showthread.php?t=572971&highlight=AR5418+GUTSY](http://ubuntuforums.org/showthread.php?t=572971&highlight=AR5418+GUTSY))

now, lshw seems to indicate something's working, but with iwconfig I can't set to the correct access point:

```
tali@thinkpad:~$ sudo lshw -C network
[sudo] password for tali: 
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:1a:6b:67:85:ca
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.2.102 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR5418 802.11abgn Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7e:91:17:75
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
tali@thinkpad:~$ sudo ifconfig <interface> down
bash: interface: No such file or directory
tali@thinkpad:~$ sudo ifconfig wifi0 down
tali@thinkpad:~$ sudo dhclient -r wifi0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
tali@thinkpad:~$ sudo ifconfig wifi0 up
tali@thinkpad:~$ sudo iwconfig wifi0 essid "tali"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wifi0 ; Operation not supported.
tali@thinkpad:~$ 

```

further details:
Ubuntu 8.04 Hardy Heron
Lenovo Thinkpad T60


Any ideas on this one?... Thanks!

---

### Post by klaasvanschelven on 2008-05-06
Ahh... answering myself above here (#10): I got it to work by taking out the wire and typing

```
sudo networking restart
```

as explained here in post #11:
[http://ubuntuforums.org/showthread.php?p=4892467#post4892467](http://ubuntuforums.org/showthread.php?p=4892467#post4892467)

---

### Post by cbernaut on 2008-06-05
I cannot get my Atheros card running either after having followed all steps outlined in this thread and [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") as well.

I have an Asus FK3 series notebook (AMD x64) running Ubuntu 8.04.

Here is the relevant output:  

lshw -C network
>   *-network UNCLAIMED
       description: Network controller
       product: AR5418 802.11abgn Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

lspci
> ...
07:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
...

ndiswrapper -l
> net5416 : driver installed
	device (168C:0024) present

I ran the following two commands without any errors in /var/log/messages
> sudo depmod -a
sudo modprobe ndiswrapper

And alas, my /etc/modprobe.d/blacklist:
> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist b43
blacklist b43legacy
blacklist ssb
blacklist ath_pci 
blacklist ath_hal


Any pointers would be greatly apreciated!!  Thanks.

---

