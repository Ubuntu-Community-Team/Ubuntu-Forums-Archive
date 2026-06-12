---
title: "Wired eth0 missing, dissapeared from lspci (netbook)"
date: 2010-08-31
forum: Hardware
---

### Post by sdaau on 2010-08-31
Hi all, 

Well, it seems that I got my MSI Wind U135 screwed up big time :( Unless there is some way to probe into hardware that doesn't have loaded drivers in Linux... 

The thing is - the wireless works well; however _the wired connection disappeared somewhere in the last month or so_! I haven't noticed it, since I didn't need to use the wired connection until now... But now that I need to use it, I can see that eth0 has completely disappeared, even from lspci!! 

By the way, I have an MSI Wind U135, with Lucid as first and only OS. Wired ethernet connection has worked great up until about a month ago, when I used the wired connection for the last time succesfully. 

The last thing I remember about the wired connection, is that I was at some place trying to connect to the wireless there, and when I failed, I disabled wireless from Network Manager; but then that Network Manager icon kept flashing again, indicating that it was trying to connect to the wired connection - even though there was no LAN cable going into the connector! That was kind of pissing me off, so I simply deleted the 'Auto eth0' entry from Network Manager, and that made the icon stop flashing. 

Fast forward to today, when again I need to use the cable. After plugging the LAN cable, I notice Network Manager doesn't react; I try then the following:
```

$ sudo ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1900 (1.9 KB)  TX bytes:1900 (1.9 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 40:61:86:43:0f:1a  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fe43:f1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7807392 (7.8 MB)  TX bytes:696206 (696.2 KB)
          Interrupt:16 


$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device

$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

```

Now, there are a ton of entries in the forums under "eth0: ERROR while getting interface flags: No such device", and they all recommend using lspci / lshw; also at this point, I again created a new wired connection in network manager. Then, I tried lspci / lshw:
```

$ sudo lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 40:61:86:43:0f:1a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 ip=192.168.1.11 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:16 memory:fe900000-fe90ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

Ouch... eth0 doesn't show, even as disabled !! :(

This would make me think that the network card maybe has hardware problems (but given this is a netbook, I suspected the ethernet card is integrated on the motherboard, in which case there cannot be loose connections). The only thing that, sort of, gives me hope, is that I remember I read somewhere that 'lspci' lists those devices "that have a driver loaded" (unfortunately, cannot remember where I read that). In which case I'd hope this is some driver initialization issue, maybe caused by some corrupt startup file - and the hardware is, hopefully, otherwise healthy. 

At this point I, thankfully, found a lspci output from a healthy machine of exact same kind in [Forum Ubuntu-fr.org / Problème de lecteur de cartes sur MSI wind U135 Lucid Lynx](http://forum.ubuntu-fr.org/viewtopic.php?id=409082):

[quote=http://forum.ubuntu-fr.org/viewtopic.php?id=409082]
...
01:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe 
**02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)**
[/quote]

where I can see that the hardware that should be present, but isn't, is Realtek RTL8101E/RTL8102E. As per "[Decoding PCI data and lspci output on Linux hosts](http://prefetch.net/articles/linuxpci.html)", the above line says that the device should be present on '[FONT="Courier New"]Field 1 : 02:00.0 : bus number (02), device number (00) and function (0)[/FONT]' (*more about these codes on [http://pci-ids.ucw.cz/](http://pci-ids.ucw.cz/)*) - and the linux driver that is responsible for driving this hardware is, apparently, **r8169**. There is a page listing devices handled by this driver here:

[http://hardware4linux.info/module/r8169/](http://hardware4linux.info/module/r8169/)

however, although there are devices called "Realtek RTL8101E" on that list, the exact same "RTL8101E/RTL8102E" cannot be found there. 

Still, I tried to load the r8169 driver:
```

$ sudo modprobe r8169

$ lsmod | grep r8169
r8169                  34076  0 
mii                     4381  1 r8169

$ sudo lshw -businfo | grep '\(01:00.0\|02:00.0\)'
pci@0000:01:00.0  wlan0      network     RT3090 Wireless 802.11n 1T/1R PCIe

```

Nope, still nothing on bus number 2 :( 

```

$ grep eth0 /var/log/messages	# shows nothing

$ dmesg | grep eth0				# shows nothing

$ grep -A 4 -B 2 eth0 /var/log/syslog
...
-- [snip] -- 
Aug 31 17:17:05 mypcname NetworkManager:    SCPlugin-Ifupdown: init!
Aug 31 17:17:05 mypcname NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Aug 31 17:17:05 mypcname NetworkManager:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Aug 31 17:17:05 mypcname kernel: [   21.947317] type=1505 audit(1283267825.651:5):  operation="profile_load" pid=823 name="/usr/share/gdm/guest-session/Xsession"
Aug 31 17:17:05 mypcname kernel: [   21.976770] type=1505 audit(1283267825.679:6):  operation="profile_replace" pid=824 name="/sbin/dhclient3"
Aug 31 17:17:05 mypcname kernel: [   21.980479] type=1505 audit(1283267825.683:7):  operation="profile_replace" pid=824 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug 31 17:17:05 mypcname kernel: [   21.980921] type=1505 audit(1283267825.683:8):  operation="profile_replace" pid=824 name="/usr/lib/connman/scripts/dhclient-script"
--
Aug 31 17:17:05 mypcname kernel: [   22.039708] type=1505 audit(1283267825.743:10):  operation="profile_load" pid=825 name="/usr/bin/evince-previewer"
Aug 31 17:17:05 mypcname kernel: [   22.065581] type=1505 audit(1283267825.771:11):  operation="profile_load" pid=825 name="/usr/bin/evince-thumbnailer"
Aug 31 17:17:05 mypcname NetworkManager:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Aug 31 17:17:05 mypcname NetworkManager:    SCPlugin-Ifupdown: autoconnect
Aug 31 17:17:05 mypcname NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Aug 31 17:17:05 mypcname NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Aug 31 17:17:05 mypcname NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.

```

Well, it seems that upon every reboot, Network Manager starts something called SCPlugin-Ifupdown which does try to deal with eth0, but nothing happens afterwards; at first glance, it seems that the reaction to eth0 is always the same each time, even though a couple of times today I tried rebooting with a LAN cable connected (the rest of the reboots were without). 


So, I guess this problem boils down to lspci not being able to see device on bus nr. 2, which should otherwise be there. Assuming this is a problem with a driver - is there any other way to inspect/probe for devices on pci bus nr.2 in linux, that possibly does not depend on drivers? In other words, are there other tools that I could use in order to verify that the ethernet network adapter is alive or dead hardware-wise? 


Thanks in advance for any comments,

Cheers!

---

### Post by sdaau on 2010-09-12
:BUMP: [BUMP]

And more bad news - just tried to boot a Live USB of Lucid, and still eth0 is not detected... so it looks like this is not a problem of software setup; does this mean the hardware is burned ? :(

Well, hope someone has an idea to troubleshoot this..

Cheers!

EDIT: Well, seems I can confirm a hardware error now.. 

First, I tried removing the power cable and the laptop battery for a while, and then tried to restore default BIOS settings. The BIOS is kinda simple too, no options to for example turn on and off wireless etc.. In any case, this made no difference. Maybe I'll try with the latest [manufacturer BIOS]("http://www.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1973") (the latest version seems to be [3.0X (n014_30x.zip)]("http://www.msi.com/index.php?func=downloadfile&dno=10953&type=bios")). 

But in any case, I finally checked with the LED lights on my router; on my other PC, even when it is turned off, it seems it powers the Ethernet connector anyways - so even when that PC is turned off, when I plug an Ethernet cable into it, the corresponding LED shines on the router. Needless to say, the LED doesn't shine when I plug the Ethernet cable in the MSI Wind :( 

([I]I tried even looking at signals at oscilloscope, but it seems something would be observable only with an established connection - not with an open ended cable, connected only on one end..

EDIT2: Found this: [Ethernet Receiver]("http://www.holmea.demon.co.uk/Ethernet/EthernetRx.htm"), very good DIY project working with Ethernet, there are oscilloscope captures as well... Seems the Ethernet cable is terminated with transformers - if this means Ethernet is current instead of voltage based, probably not much can be seen on an open ended cable anyways - maybe if each differential pair was terminated with a resistor?[/I]).

EDIT3: Flashed the latest BIOS (*using grub4dos to load a 2MB win98 boot floppy image; in fact it is difficult to even see it has been updated - the front page numbers dont change in the BIOS screen, one has to look further in 'System Information' menu or something*) -- unfortunately, as expected, nothing new happens: eth0 is still dead...

EDIT4: Just noticed that there is a LED for, apparently, wired network, never seen it before - second from right to left, with the two vertical parallel arrows, one up, one down (image from [here]("http://lowphd.blogspot.com/2010/08/msi-wind-u135-wimax-inside-netbook.html")): 

[URL="http://3.bp.blogspot.com/_Qabtj3Ik__o/TGVfZl2poYI/AAAAAAAAAek/zOq28Y9EwLM/s1600/IMG_3863.JPG"]
[IMG]http://3.bp.blogspot.com/_Qabtj3Ik__o/TGVfZl2poYI/AAAAAAAAAek/zOq28Y9EwLM/s320/IMG_3863.JPG[/IMG][/URL]

Well, cannot remember if it shined earlier, but now definitely it doesn't, even with an Ethernet cable connected... :(

I also tried with re-pressing all function (Fn) keys, in hope something maybe triggers the BIOS to activate Ethernet hardware (*by looking at /var/log/messages, I can see that pressing Fn+F2, which is for changing displays if you have an extern monitor which I don't, will generate "ACPI: BIOS _OSI(Linux) query ignored" - so I guess those keys trigger something in BIOS*) - but, again, eth0 is still dead :(

---

### Post by executorvs on 2010-09-21
The module which runs the realtek r816* ethernet cards is buggy. I suggest you file a bug on launchpad. to get your card up again shutdown, unplug your computer, and pull the battery. Give it about 3 minutes and when you boot up, it should have returned... at least until the cycle repeats itself.

let me know if it doesn't work.

---

### Post by sdaau on 2010-09-23
Hi executorvs,

Thanks so much for responding !

> **executorvs said:**
> The module which runs the realtek r816* ethernet cards is buggy. I suggest you file a bug on launchpad. to get your card up again shutdown, unplug your computer, and pull the battery. Give it about 3 minutes and when you boot up, it should have returned... at least until the cycle repeats itself.

let me know if it doesn't work.

Well, I just unplugged, removed the battery and waited for some 5 minutes, but unfortunately, the situation is same as before - the wired network adapter is not reported in lspci at all... So, as this still looks like a hardware problem, I haven't filed any bugs yet.

I was talking to the supplier, and asked them to look at this thread - they also seem to think its hardware, and they are OK with me using the warranty to get a replacement machine ... However, if this is something fixable, I'd rather fix it myself than going through all that with the customer support replacement procedure.. 

So if you have any more ideas on how to troubleshoot this problem further (*up to, and including, oscilloscope measurement, but not any opening of the machine that would void warranty ;) *), I'd love to hear them ! :) 

Cheers!


(*PS: By the way, I have had a different hardware problem - cannot remember what it was - with a different netbook; and there, the solution indeed was to: unplug, remove the battery, and wait some 10 minutes... I always wandered what this was due to - some capacitors not discharging properly? In any case, that seems not to be the solution here... *)

---

### Post by alexsmith on 2010-12-01
I've got EXACTLY the same problem yesterday. :o

Have you found any solutions, cause I got none yet! :(

I remember I had a similar problem some time ago and I solved it booting my notebook in Window$ and then going back to Linux. Probably because Window$ driver is better than Linux one, since unfortunatelly it is proprietary, i.e., manufacturers are supposed to know better their hardware.

But, unfortunatelly again, it didn't solve the problem this time.

I'll keep in touch if I find out something...

---

### Post by alexsmith on 2010-12-01
Reading a little further, I saw many comments mentioning turning off the machine, removing the battery and waiting for a couple minutes before turning it back on again.

I tried that here and it looks like eth0 is back working. I said "looks like" because I'm not able to test it right now, but ifconfig now shows eth0 again, which makes me happy... ;-)

---

### Post by sdaau on 2011-01-11
Hi alexsmith, thanks for responding!

> **alexsmith said:**
> Reading a little further, I saw many comments mentioning turning off the machine, removing the battery and waiting for a couple minutes before turning it back on again.

I tried that here and it looks like eth0 is back working. I said "looks like" because I'm not able to test it right now, but ifconfig now shows eth0 again, which makes me happy... ;-)

Just saw your post, and thought I'd try it again - so I removed the battery for the entire night this time; but still no dice.. (and still haven't had time to go to the shop for repairs).. 

Cheers!

---

