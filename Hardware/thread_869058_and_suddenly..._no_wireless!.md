---
title: "and suddenly... no wireless!"
date: 2008-07-24
forum: Hardware
---

### Post by cespinal on 2008-07-24
Hello guys... I need you help in here, 

I went to a business trip yesterday and when I got back home, no wireless!. 

My pc is an HP Pavilion Dv9000 with a broadcom wireless card. I have sucessfully been using ndiswrapper since I got hardy. Now, my pc detects my home network, but the signal is in 0% and the wireless LED is ORANGE... 

could you give me advice on this? 
thanks :(

---

### Post by evets25 on 2008-07-24
if the wireless led is orange, that mean that either the wireless radio switch is turned off or the device is disabled on your computer. Most laptops have some sort of button or switch on the side of the case to manually turn the wireless on or off. Make sure this is set to "on." Next, try seeing if your wireless card is disabled in ubuntu. Are you using networkmanager (default for ubuntu)?

---

### Post by Potatoj316 on 2008-07-24
this occasionaly happens to me and this is how I fix it.  Unplug the power of your router then unplug the power ofyour modem, now plug your modem back in, and then plug your router back in.  Now wait like 5 minutes and try to connect again.  this is called power cycling

---

### Post by cespinal on 2008-07-24
thanks for the quick answer. indeed, the swicth is on but there's no wireless. How do i find the latter?

next, I am using network manager but I really dont know how to get my way through it.. I just enable roaming mode and thats it

---

### Post by Potatoj316 on 2008-07-24
Have you tried the power cycle?  I really think that would work.

---

### Post by cespinal on 2008-07-24
let me give it a try! I will be back y some minutes :P

---

### Post by cespinal on 2008-07-24
mmm nopes... nothing yet maybe somehow the wireless card got disabled...

---

### Post by evets25 on 2008-07-24
Yeah, try powercycling (rebooting) the router and your computer at least once. 

Some things to check: 
- Does your wireless network show up under netowrkmanager? Click on the little icon in the system tray. 
- open up a terminal and type in the following commands, then post the output here: 
```
iwconfig
sudo iwlist wlan0 scan
ifconfig
```

I'm assuming that your wireless device is named wlan0. iwconfig will show you any wireless devices, the second one lists access points in range, and the third command lists inormation about all your network devices.

To disable any network device from terminal use this command (assuming your device is called wlan0): 
```
sudo ifdown wlan0
```

...and to re-enable it again do the same thing, but replace ifdown with ifup.

---

### Post by cespinal on 2008-07-24
iwconfig output is: 

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11a  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:270 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

scan output: wlan0     No scan results

if config output: 

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:2c:50:e6  
          inet addr:192.168.0.135  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe2c:50e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29696 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13379 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16863448 (16.0 MB)  TX bytes:3237786 (3.0 MB)
          Interrupt:252 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8383 (8.1 KB)  TX bytes:8383 (8.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:fc:5f:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:f2200000-f2204000

---

### Post by evets25 on 2008-07-24
ok, so here's what that tells me: 

- you have another network cable plugged in to your computer (eth0) with the ip address 192.168.0.135
- your wireless card is in fact called "wlan0"
- you are not connected to any (wireless) network
- your wireless card doesn't see any wireless networks in range.

When you right-click on networkmanager, you should see two little check boxes, one each to enable your wireless and wired network card respectively. If not, then that means your wireless card isn't being recognized by networkmanager for some reason (but your system still knows it's there). If this is still the case after rebooting, I forget how to give control back to networkmanager.

If you're on a laptop, try taking your laptop up to the router and seeing if your get a signal while standing right next to it. If you're on a desktop, double check that the antenna is plugged in, and that everything is generally connected like it should be.

---

### Post by fs3rp4 on 2008-07-24
Several HP notebooks are losing the wireless card, it's a manufacturer problem. Please post the result from this command:

sudo lspci

---

### Post by cespinal on 2008-07-24
here: 

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

---

### Post by cespinal on 2008-07-24
> **evets25 said:**
> ok, so here's what that tells me: 

- you have another network cable plugged in to your computer (eth0) with the ip address 192.168.0.135
- your wireless card is in fact called "wlan0"
- you are not connected to any (wireless) network
- your wireless card doesn't see any wireless networks in range.

When you right-click on networkmanager, you should see two little check boxes, one each to enable your wireless and wired network card respectively. If not, then that means your wireless card isn't being recognized by networkmanager for some reason (but your system still knows it's there). If this is still the case after rebooting, I forget how to give control back to networkmanager.

If you're on a laptop, try taking your laptop up to the router and seeing if your get a signal while standing right next to it. If you're on a desktop, double check that the antenna is plugged in, and that everything is generally connected like it should be.

-Im using and thernet cable at this moment. 
-network manager shows two checkboxes
-Im very close to the router at this moment 

maybe the router is not working properly... but If that's the case, why de LED on my laptop is still flashing orange?

---

### Post by fs3rp4 on 2008-07-24
OK!!!
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
You have the wireless interface. Luck you.

Did you upgraded to the last linux-image-2.6.24-20?

---

### Post by evets25 on 2008-07-24
use this command to find out your kernel version:
```
uname -r
```

---

### Post by cespinal on 2008-07-24
nope... im still on 2.6.24-19 generic

---

### Post by evets25 on 2008-07-24
if it's a driver-related issue, someone else will have to take it from here... try and find more info on that HP-specific problem that the other guy mentioned.

---

### Post by cespinal on 2008-07-24
hey.. it just got solve on its own!... I guess its router-related...

---

### Post by evets25 on 2008-07-24
It's nice that it got solved on it's own, but it would be good to get to the root of the problem in case it happens again. Happy problem hunting.

---

### Post by cespinal on 2008-07-25
thank you very much to all for your quick help on this! I really really appreciate it. 

I'll switching my router next week for a friend's one to see if thats the problem.

---

