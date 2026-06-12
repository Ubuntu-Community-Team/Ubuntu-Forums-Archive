---
title: "Wireless drivers?"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by Tprice on 2007-07-01
Hey all im new to Linux and i have being trying to install ubuntu on my PC! i have installed the OS but my wireless card does not seem to want to work. it says that is is installed but when i try to connect to a router it does not connect!

My card is a linksys wmp54g card

Can any one help?

---

### Post by ugm6hr on 2007-07-01
Start with telling us what the output from the following in Terminal is:
```
lspci
ifconfig
iwconfig
```
You are looking for Network/Ethernet Controller

---

### Post by Tprice on 2007-07-01
im sorry im new to this!

how would i find that out?

---

### Post by Swab on 2007-07-01
Applications > Accessories > Terminal

Then type in the commands suggested above one by one, and paste back the results to this thread.

---

### Post by Tprice on 2007-07-01
ok this is what i got. im sorry if this is not it, i just have never done this before!


> 00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:07.0 Multimedia controller: ATI Technologies Inc Unknown device 4d52
01:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
02:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
02:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)

eth0      Link encap:Ethernet  HWaddr 00:0E:A6:88:0F:E1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1696 (1.6 KiB)  TX bytes:1696 (1.6 KiB)

ra0       Link encap:Ethernet  HWaddr 00:0F:66:74:74:A1  
          inet6 addr: fe80::20f:66ff:fe74:74a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3 txqueuelen:1000 
          RX bytes:15313 (14.9 KiB)  TX bytes:1091463 (1.0 MiB)
          Interrupt:19 Base address:0xc000 

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=67/100  Signal level=-51 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ugm6hr on 2007-07-01
This is the important bit:
01:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
The interface used is *ra0*
The chipset is *RT2500*

I suspect that means your card is: Card: Linksys WMP54G v4, 54mbps

Number 14 on this page is useful for info:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)

It looks like Ubuntu has pre-installed the RT2500 open-source driver.  

Does anyone know if this works?  If not - it looks like your options are to compile the Ralink Linux driver ([http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)) or ndiswrapper.  Or mabe just search these forums for RT2500 for solutions.

---

### Post by Tprice on 2007-07-01
well thanks for the help! i will see if i can get it to work, but i dint think i will be able to get it. im to new to linux to know what to do:(

but thanks for the fast repleys and for the help!

---

### Post by ugm6hr on 2007-07-01
Just to help you along a bit:
[http://ubuntuforums.org/showthread.php?t=413594](http://ubuntuforums.org/showthread.php?t=413594)

Just reading the first page (always dangerous) - suggests that the RT2500 driver does work - but just not with Network Manager.

Try reading through it all first, but I think this is probably the easiest (potential) solution:

I would try uninstalling Network Manager (Go to System->Synaptic Package Manager, search for network-manager, then right-click on it and select uninstall, then apply), then rebooting, and then installing Wicd (I use v1.2.9 because I found v1.2.7 *unstable*, but now there is v1.3.0 testing - worth trying first).

In Wicd preferences - edit the entries so that the wireless interface is *ra0*.

Wicd:
wicd.sourceforge.net

---

### Post by Tprice on 2007-07-01
well i would just like to take my hat off to you! you really help i am not posting this message thought Ubuntu!!

I am using Wicd to connect to mt router!

I could connect to one of my router that didnt have encryption but the one that did i can,, but i will find out how to do that latter!

Thank you so much!!

---

### Post by ugm6hr on 2007-07-01
Glad that it helped.

As for encryption - WEP should just work with Wicd - as long as you use the HEX key (sometimes you have to enter the password with "quotemarks" either side).

WPA may require a bit of research though....

---

### Post by Austin_KW on 2007-07-02
The supplied "serialmonkey" driver works for encrypted networks.
For WPA you need to add some pre-up config commands to /etc/network/interfaces

gksudo gedit /etc/network/interfaces
and add/replace the ra0 config with the following; set appropriate values for *MyNetworkName* and *WPAPSK="xxxxxxxxxxxxxx"*. 
```

auto ra0
iface ra0 inet dhcp
    pre-up ifconfig ra0 up
    pre-up iwconfig ra0 mode managed
    pre-up iwconfig ra0 essid MyNetworkName
    pre-up iwpriv ra0 set EncrypType=TKIP
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwconfig ra0 essid MyNetworkName
    pre-up iwpriv ra0 set  WPAPSK="xxxxxxxxxxxxxx"
    pre-up iwconfig ra0 essid MyNetworkName

```

---

