---
title: "How can I install network drivers?"
date: 2008-05-31
forum: Hardware
---

### Post by tico305 on 2008-05-31
I have a HP Compaq nc6400 and for whatever reason the only way I can connect to the internet is with an ethernet cable and not wireless. I'm pretty sure I only have to install the drivers or w/e but when I go to the hp website to download the drivers, they're all in .exe format. How can I get these bastards to work?

B.t.w, the wireless connection option doesn't even appear in the network monitor.

Is there a file extension I can convert the .exe files to?

Thanks in advance,
Albert

---

### Post by unutbu on 2008-05-31
Please post

```
sudo lshw -C network
lspci
lsusb
ifconfig
cat /etc/network/interfaces
route -n

```

---

### Post by tico305 on 2008-06-01
Okay, well I pasted that into the terminal and it asked for a password like everything else...I entered my password and pasted it again and quite a few lines scrolled down for a bit. It mentioned my network stuff but...as far as I know, nothing has changed 	#-o

---

### Post by unutbu on 2008-06-01
Yes, so we can better help you, we need more information about the state of your system. Those commands help us learn just that.

---

### Post by tico305 on 2008-06-01
This what it said...I think I did it right and thanks.

```
tico@tico-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5753M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 21
       serial: 00:16:d4:c3:d4:0c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5753m-v3.56 ip=192.168.1.103 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945
tico@tico-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
02:06.4 Communication controller: Texas Instruments PCIxx12 GemCore based SmartCard controller
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express (rev 21)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
tico@tico-laptop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 08ff:2580 AuthenTec, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
tico@tico-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:c3:d4:0c  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fec3:d40c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79947 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73883 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106237618 (101.3 MB)  TX bytes:6761064 (6.4 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73300 (71.5 KB)  TX bytes:73300 (71.5 KB)

tico@tico-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

tico@tico-laptop:~$ route -n



```

---

### Post by unutbu on 2008-06-01
tico305, 
You can only use one network interface per network. In other words, if you have a wired connection to your router, you can not also have a wireless connection to the same router.

So if you want to connect to the internet using wireless, unplug the eth0 wire for now.

According to [http://bb.cactii.net/archives/2006_08.php](http://bb.cactii.net/archives/2006_08.php), wireless should work "out-of-the-box" -- at least with Dapper. One might presume after all these years, it should also work with Gutsy or Hardy.

According to [http://intellinuxwireless.org/](http://intellinuxwireless.org/), you should use the iwlwifi driver. I think the iwl3945 which you are currently using is the iwlwifi driver. 
So, are you sure you need to use some Windows .exe driver? There is a way to do that, but in your case, I don't think it is a good idea. A native linux driver is usually (maybe always?) a better choice than using ndiswrapper + windows driver.

Your lshw output shows the iwl3945 driver has been loaded. 
```
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: **driver=iwl3945** latency=0 module=iwl3945
```

But on the other hand, ifconfig fails to show a wlan0 network interface.

Are you seeing any lights turned on you wireless card? If not, please run the following command and post the result:
```
grep 3945 /var/log/messages

```

---

### Post by tico305 on 2008-06-02
It's not a pc card. It's an integrated one and okay this is weird. Usually the option for wireless internet isn't even available but now it is??? Must've been something I put in the terminal maybe? Odd thing is...it's picking up my neighbors' routers but not mine which is only a couple rooms away and the signal is typically strong throughout the house....its weird, any ideas? Anyways, I typed in the last code you gave me in the terminal and this is what I got.



```
tico@tico-laptop:~$ grep 3945 /var/log/messages
May 31 16:43:56 tico-laptop kernel: [   27.726890] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
May 31 16:43:56 tico-laptop kernel: [   27.726894] iwl3945: Copyright(c) 2003-2007 Intel Corporation
May 31 16:43:56 tico-laptop kernel: [   27.842750] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
May 31 16:43:56 tico-laptop kernel: [   29.756116] iwl3945: Radio Frequency Kill Switch is On:
May 31 16:43:56 tico-laptop kernel: [   29.761293] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 16:43:56 tico-laptop kernel: [   29.771353] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 16:43:56 tico-laptop kernel: [   29.791339] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 16:43:56 tico-laptop kernel: [   29.818828] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 16:43:56 tico-laptop kernel: [   29.838788] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
May 31 18:53:07 tico-laptop kernel: [   40.555069] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
May 31 18:53:07 tico-laptop kernel: [   40.555073] iwl3945: Copyright(c) 2003-2007 Intel Corporation
May 31 18:53:07 tico-laptop kernel: [   40.555246] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
May 31 18:53:07 tico-laptop kernel: [   42.058024] iwl3945: Radio Frequency Kill Switch is On:
May 31 18:53:07 tico-laptop kernel: [   42.063246] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 18:53:07 tico-laptop kernel: [   42.073302] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 18:53:07 tico-laptop kernel: [   42.093285] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 18:53:07 tico-laptop kernel: [   42.120781] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 18:53:07 tico-laptop kernel: [   42.140741] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
May 31 20:52:45 tico-laptop kernel: [   32.562120] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
May 31 20:52:45 tico-laptop kernel: [   32.562124] iwl3945: Copyright(c) 2003-2007 Intel Corporation
May 31 20:52:45 tico-laptop kernel: [   32.562303] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
May 31 20:52:45 tico-laptop kernel: [   33.438785] iwl3945: Radio Frequency Kill Switch is On:
May 31 20:52:45 tico-laptop kernel: [   33.443406] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 20:52:45 tico-laptop kernel: [   33.453463] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 20:52:45 tico-laptop kernel: [   33.473445] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 20:52:45 tico-laptop kernel: [   33.500984] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 20:52:45 tico-laptop kernel: [   33.520941] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
May 31 20:58:29 tico-laptop kernel: [  100.491678] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
May 31 20:58:29 tico-laptop kernel: [  100.491682] iwl3945: Copyright(c) 2003-2007 Intel Corporation
May 31 20:58:29 tico-laptop kernel: [  100.558730] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
May 31 20:58:29 tico-laptop kernel: [  101.987950] iwl3945: Radio Frequency Kill Switch is On:
May 31 20:58:29 tico-laptop kernel: [  101.993105] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 20:58:29 tico-laptop kernel: [  102.003161] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 20:58:29 tico-laptop kernel: [  102.023143] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 20:58:29 tico-laptop kernel: [  102.050670] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 20:58:29 tico-laptop kernel: [  102.070630] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
May 31 20:58:36 tico-laptop kernel: [  111.723945] iwl3945: Radio Frequency Kill Switch is On:
May 31 21:40:14 tico-laptop kernel: [ 2607.309878] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 21:40:14 tico-laptop kernel: [ 2607.359880] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 21:40:14 tico-laptop kernel: [ 2607.419872] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 21:40:14 tico-laptop kernel: [ 2607.589924] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 21:42:29 tico-laptop kernel: [   21.153945] assign_interrupt_mode Found MSI capability
May 31 21:42:29 tico-laptop kernel: [   22.843945] ACPI: Thermal Zone [TZ2] (52 C)
May 31 21:42:29 tico-laptop kernel: [   38.935847] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
May 31 21:42:29 tico-laptop kernel: [   38.935850] iwl3945: Copyright(c) 2003-2007 Intel Corporation
May 31 21:42:29 tico-laptop kernel: [   38.936027] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
May 31 21:42:29 tico-laptop kernel: [   40.661210] iwl3945: Radio Frequency Kill Switch is On:
May 31 21:42:29 tico-laptop kernel: [   40.666328] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 21:42:29 tico-laptop kernel: [   40.676384] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 21:42:29 tico-laptop kernel: [   40.696366] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 21:42:29 tico-laptop kernel: [   40.723827] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
May 31 21:42:29 tico-laptop kernel: [   40.743905] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Jun  1 03:24:06 tico-laptop kernel: [   38.401123] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun  1 03:24:06 tico-laptop kernel: [   38.401126] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Jun  1 03:24:06 tico-laptop kernel: [   38.401289] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Jun  1 03:24:06 tico-laptop kernel: [   39.866295] iwl3945: Radio Frequency Kill Switch is On:
Jun  1 03:24:06 tico-laptop kernel: [   39.871472] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun  1 03:24:06 tico-laptop kernel: [   39.881528] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun  1 03:24:06 tico-laptop kernel: [   39.901510] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun  1 03:24:06 tico-laptop kernel: [   39.929027] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun  1 03:24:06 tico-laptop kernel: [   39.948987] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Jun  2 00:20:09 tico-laptop kernel: [   38.099677] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun  2 00:20:09 tico-laptop kernel: [   38.099681] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Jun  2 00:20:09 tico-laptop kernel: [   38.099856] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Jun  2 00:20:09 tico-laptop kernel: [   39.602408] iwl3945: Radio Frequency Kill Switch is On:
Jun  2 00:20:09 tico-laptop kernel: [   39.607598] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun  2 00:20:09 tico-laptop kernel: [   39.617663] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun  2 00:20:09 tico-laptop kernel: [   39.637646] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun  2 00:20:09 tico-laptop kernel: [   39.665164] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun  2 00:20:09 tico-laptop kernel: [   39.685135] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Jun  2 00:20:16 tico-laptop kernel: [   50.420856] iwl3945: Radio Frequency Kill Switch is On:
tico@tico-laptop:~$ 


```

P.s. Thank you so much for help thus far! You're really helping out.

---

### Post by unutbu on 2008-06-02
If you are detecting a neighbor's router, your wlan0 interface must be up. Please post the output to

```
ifconfig      # Again, just to see wlan0 is there
iwconfig      # more info about wlan0
iwlist scan   # to see what routers your card detects
```

If your router has encryption turned on, you might want to turn it off temporarily just to make it easier to establish a connection. After you get a working connection we can work on encryption.

Have you tried Network Manager (System>Administration>Network) to configure the wireless interface?

---

### Post by Astro6312 on 2008-06-02
I have a questions related to this topic... I installed 8.04 on a dell quad core, everything went ok.  I take the HD and put it on another dell, same model, bought at the same time, but network is not detected.

Must be a different chip set?

Is there something in ubuntu that discover and install new hardware?  I remember seeing that in Fedora a long time ago.

Thanks,

Simon

---

### Post by unutbu on 2008-06-02
Yes, it is possible that two Dells bought at the same time may have different network cards. Sometimes the cards can have the same name, but have different revision numbers, and sometimes this means different chipsets.

If you run
```

sudo lshw > lshw-1.out
```
on the first machine, and run
```
sudo lshw > lshw-2.out
```
on the second machine, you can then compare the lshw-1.out to lshw-2.out to see if there are any differences in the hardware.

> Is there something in ubuntu that discover and install new hardware? I remember seeing that in Fedora a long time ago.
Besides lshw, there is also System>Preferences>Hardware Information. These tools just report detected hardware, however. 
The linux kernel in most cases detects all the hardware and loads the right driver modules at boot time. Hotpluggable USB devices are detected on the fly too, most of the time. Everything works, usually. The forums, however, are a gathering place for the exceptions, when something goes wrong.

---

### Post by stchman on 2008-06-02
> **tico305 said:**
> I have a HP Compaq nc6400 and for whatever reason the only way I can connect to the internet is with an ethernet cable and not wireless. I'm pretty sure I only have to install the drivers or w/e but when I go to the hp website to download the drivers, they're all in .exe format. How can I get these bastards to work?

B.t.w, the wireless connection option doesn't even appear in the network monitor.

Is there a file extension I can convert the .exe files to?

Thanks in advance,
Albert

The 3945ABG card work with Hardy but not too great.  Also, make sure the switch for the wireless is on.  This is a common mistake.

Apparently with Gutsy or eariler Ubuntu used a proprietary driver for the 3945 whicu worked very well.  Ubuntu went to an open source driver which works but has spotty performance.  There are workarounds to help its performance in Hardy.

The 4965AGN works very well in Hardy (that is what I have in my laptop).

---

### Post by stchman on 2008-06-02
> **unutbu said:**
> tico305, 
You can only use one network interface per network. In other words, if you have a wired connection to your router, you can not also have a wireless connection to the same router.

So if you want to connect to the internet using wireless, unplug the eth0 wire for now.

According to [http://bb.cactii.net/archives/2006_08.php](http://bb.cactii.net/archives/2006_08.php), wireless should work "out-of-the-box" -- at least with Dapper. One might presume after all these years, it should also work with Gutsy or Hardy.

According to [http://intellinuxwireless.org/](http://intellinuxwireless.org/), you should use the iwlwifi driver. I think the iwl3945 which you are currently using is the iwlwifi driver. 
So, are you sure you need to use some Windows .exe driver? There is a way to do that, but in your case, I don't think it is a good idea. A native linux driver is usually (maybe always?) a better choice than using ndiswrapper + windows driver.

Your lshw output shows the iwl3945 driver has been loaded. 
```
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: **driver=iwl3945** latency=0 module=iwl3945
```

But on the other hand, ifconfig fails to show a wlan0 network interface.

Are you seeing any lights turned on you wireless card? If not, please run the following command and post the result:
```
grep 3945 /var/log/messages

```

You can have the wired connection hooked up at the same time.  In network-manager you can select either a wired connection or one of the available wireless connection.

---

### Post by tico305 on 2008-06-02
> **unutbu said:**
> If you are detecting a neighbor's router, your wlan0 interface must be up. Please post the output to

```
ifconfig      # Again, just to see wlan0 is there
iwconfig      # more info about wlan0
iwlist scan   # to see what routers your card detects
```

If your router has encryption turned on, you might want to turn it off temporarily just to make it easier to establish a connection. After you get a working connection we can work on encryption.

Have you tried Network Manager (System>Administration>Network) to configure the wireless interface?


My router has a password but thats it. And yea I've tried going to network, that's where it was weird before because before the wireless option wouldn't even appear only ethernet and modem.

What you requested.

```
tico@tico-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:c3:d4:0c  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fec3:d40c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1514 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1670 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1228945 (1.1 MB)  TX bytes:335989 (328.1 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69000 (67.3 KB)  TX bytes:69000 (67.3 KB)

tico@tico-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tico@tico-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

tico@tico-laptop:~$ 

```

---

### Post by tico305 on 2008-06-02
> **stchman said:**
> The 3945ABG card work with Hardy but not too great.  Also, make sure the switch for the wireless is on.  This is a common mistake.

Apparently with Gutsy or eariler Ubuntu used a proprietary driver for the 3945 whicu worked very well.  Ubuntu went to an open source driver which works but has spotty performance.  There are workarounds to help its performance in Hardy.

The 4965AGN works very well in Hardy (that is what I have in my laptop).

> **unutbu said:**
> If you are detecting a neighbor's router, your wlan0 interface must be up. Please post the output to

```
ifconfig      # Again, just to see wlan0 is there
iwconfig      # more info about wlan0
iwlist scan   # to see what routers your card detects
```

If your router has encryption turned on, you might want to turn it off temporarily just to make it easier to establish a connection. After you get a working connection we can work on encryption.

Have you tried Network Manager (System>Administration>Network) to configure the wireless interface?

No,yea I definitely checked to see if the switch was on before I decided to ask the forum, that would've been embaressing....but an easy fix. I wish that was the problem.:lol:

---

### Post by new2linux2008 on 2008-06-02
this link help me, i'm running a hp dv9727..

[http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

also I tried running the amd 64bit version and got it to work but wouldn't connect. so I switched to the 32bit and did the advice on that link, and it all worked apon restart.

hope that helps.

---

### Post by unutbu on 2008-06-02
> **stchman said:**
> 
Apparently with Gutsy or eariler Ubuntu used a proprietary driver for the 3945 whicu worked very well.  Ubuntu went to an open source driver which works but has spotty performance.  There are workarounds to help its performance in Hardy.


Following stchman's lead, I found this guide for using the proprietary ipw3945 driver by googling "3945 Hardy": [http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html](http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html)

After reading a number of bug reports related to iwl3945, I concluded it is better to use ipw3945. 
You might want to do some googling/research to make sure I didn't miss something, however.

---

### Post by vexingmodstwo on 2008-06-02
I'm a total noob at this stuff and after trying a bunch of stuff I switched network managers from the Network Manager that's already installed to WICD then to wifiradar.

wifiradar worked.  You might want to try that as a last resort if after you've gotten the wireless card (wlan0) to show up in ifconfig.

You might also just try to create a connection in your router and then manually configure the connection on your computer and manually enter the IP address and default gateway address.

That's how I got my laptop to work wirelessly.

---

### Post by tico305 on 2008-06-03
Well, I discovered a little while ago that the real problem lied in my router. My brother told me he was having trouble with his connection with our wireless router, so I'm getting that taken cared of.

My next, and final question, would be: Why is my graphics messing up?

For example: When I played chess in 3d it would ask for python opengl and other stuff. I installed them using synaptic package manager, but that was only a quick fix and it only works for a few seconds. I think its why I can't put all the special effects on. I think its something with my video drivers....help me please?

Thanks to all of you that have been helping me, b.t.w.

---

