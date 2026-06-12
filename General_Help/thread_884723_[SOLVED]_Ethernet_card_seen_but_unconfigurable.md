---
title: "[SOLVED] Ethernet card seen but unconfigurable"
date: 2008-08-09
forum: General Help
---

### Post by ltb on 2008-08-09
Hello,

1) I know my way through Windows, and DOS before that.
2) I am a first time user of Linux in any form, and would like to stay within the graphic environment, just to be a bit sure...

Installing Wubi failed on the desktop (as many Live CD versions before) but succeeded on the Acer Aspire 9500 laptop at the first attempt today.
Internet did not work, nor could it find a shared printer on the networked Desktop.
So I browsed to Network tools, where the Wireless Network displayed the correct hardware address. Trying to configure it gave the flabbergasting message: "The interface does not exist" 
What goes wrong here?

---

### Post by pytheas22 on 2008-08-09
I know you want to use GUIs, but to help diagnose the problem, it would be a lot simpler and easier to see output from the command-line.  Please open a terminal and enter these commands:
```

lshw -C Network
lspci -nn
lsusb
ifconfig -a
```

and post the output here so that we can figure out what's wrong.

---

### Post by ltb on 2008-08-11
> **pytheas22 said:**
> I know you want to use GUIs, but to help diagnose the problem, it would be a lot simpler and easier to see output from the command-line.  Please open a terminal and enter these commands:
```

lshw -C Network
lspci -nn
lsusb
ifconfig -a
```

and post the output here so that we can figure out what's wrong.
OK, I tried the terminal. Did not understand much of the commands nor their result. Before I could copy the output to Firefox, the internet connection died (it was a weak one on a neighbour's network, my own modem persistently is not seen under Ubuntu). I now reply from my Desktop under Windows.
I saved the terminal dialog to a text file, but can't get it on a place where Windows can reach it. I'm stuck...

---

### Post by spike.robinson on 2008-08-11
If you can get back on to Ubuntu, you can save the terminal output in the /host folder. This will then be visible on the root folder of your Windows boot disk (probably C:\ folder) when you reboot into Windows. 

Is your home internet connection wireless by the way? It might help to turn off any encryption and authentication on your wireless modem, until you get it working with Ubuntu.

---

### Post by ltb on 2008-08-11
> **spike.robinson said:**
> If you can get back on to Ubuntu, you can save the terminal output in the /host folder. 

Ah, you tripled my knowledge of Linux :-)

> **spike.robinson said:**
> This will then be visible on the root folder of your Windows boot disk (probably C:\ folder) when you reboot into Windows. 


Actually I could browse to a folder that I shared with my desktop under Windows. I have attached the file.

> **spike.robinson said:**
> 
Is your home internet connection wireless by the way? 

It is, needed be, because I can't reach my office from where the phone line enters the house and the router/ADSL-modem : two stairs between them.... Use wireless phones also.

> **spike.robinson said:**
> It might help to turn off any encryption and authentication on your wireless modem, until you get it working with Ubuntu.
Need to look up how I have that organised... 5 years ago I think...

Thanks for your help.

---

### Post by ltb on 2008-08-11
I don't see the file attachment... Can I copy it into a msg?

---

### Post by ltb on 2008-08-11
OK, itÅ› just that I do not know the commands.. Where can I find out about Terminal commands?

InbetweenI have this internet connection via one of my neighbours. While it works well under Wndows, I cannot find my Router/ADSLmodem  under Ubuntu...


root@Acer-Laptop:/home/ltb# lshw -C Network
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:94:55:a7
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:34:8e:f0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.106 latency=128 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
root@Acer-Laptop:/home/ltb# 
root@Acer-Laptop:/home/ltb# 
root@Acer-Laptop:/home/ltb# 


root@Acer-Laptop:/home/ltb# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port [8086:2591] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 04)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 04)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d4)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 04)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility X700 (PCIE) [1002:5653]
06:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
06:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)
06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)
06:04.1 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0530] (rev 01)
06:04.2 SD Host controller [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller [1524:0550] (rev 01)
06:04.3 FLASH memory [0501]: ENE Technology Inc FLASH memory: ENE Technology Inc: [1524:0520] (rev 01)
06:04.4 FLASH memory [0501]: ENE Technology Inc SD/MMC Card Reader Controller [1524:0551] (rev 01)
root@Acer-Laptop:/home/ltb# 
root@Acer-Laptop:/home/ltb# 


root@Acer-Laptop:/home/ltb# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
root@Acer-Laptop:/home/ltb# 
root@Acer-Laptop:/home/ltb# 


root@Acer-Laptop:/home/ltb# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:94:55:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:34:8e:f0  
          inet6 addr: fe80::213:ceff:fe34:8ef0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:9 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3578118 (3.4 MB)  TX bytes:319781 (312.2 KB)
          Interrupt:23 Base address:0x4000 Memory:b0001000-b0001fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:120890 (118.0 KB)  TX bytes:120890 (118.0 KB)

root@Acer-Laptop:/home/ltb#

---

### Post by spike.robinson on 2008-08-11
I'm too dumb to interpret your terminal output but thanks for posting it anyway. ;)

Since Ubuntu can see your neighbour's WiFi automatically, I suggest you turn off any security on your own WiFi modem base station, and hopefully you will then be able to see your own WiFi modem in Ubuntu.

---

### Post by pytheas22 on 2008-08-11
Thanks for the output ltb.  Just to clear things up--because I'm a little confused--are you trying to get your wired (ethernet) or wireless connection working in Ubuntu?  If it's the wired connection, what happens when you try to connect?  It looks like it should work based on the output you gave.

If the problem is with the wireless, what exactly is going on?  Ubuntu doesn't see your wireless network, but it sees other networks and can connect to them?  Or is it just that Ubuntu can see your network, but can't connect to it?

If Ubuntu can't see your network at all, you may want to check the settings and make sure it's broadcasting on the right frequency.  If you set it up five years ago and haven't touched it since, it may be operating in 11b mode, which could be the reason that Ubuntu doesn't see it at all.  See if you can switch it to 11g.

It would also be helpful if you posted the output of:
```

iwlist scan
```

and tell us the name of your wireless network.

---

### Post by ltb on 2008-08-11
Hello all who contributed: problem is solved.

When I configured my wireless network and Internet access some 5 years ago, I had the problem that the router/ADSLmodem, was downstairs, while my office is two stairs up. The manual for the thingy (Thomson/Alcatel speedTouch) assumed that while configuring I could connect the desktop with an Ethernet cable, but I had no such a long cable... That, added to the fact that the manual was ill-written, made me use only MAC-address verification, no WEP. WPA was non-existent then.

Ubuntu would not accept a configuration without a key, or without an SSID (a term that I had forgotten..)
I have now reconfigured the Network using Windows, adding WEP to the MAC-verification. When that all worked, it took me 5 minutes to get Ubuntu to recognize the Router, and internet worked instantly.
Now time to go to bed, the network connection will come later in the week.

---

### Post by cooke77 on 2008-08-18
ITB,you have Ethernet(LAN), ADSL and Wireless, right?
The LAN has a 'gateway'.
The Wireless (router) also has a 'gateway'.
The ADSL also requires a 'gateway'.
Each HAS to 'know' what 'gateway' is being used.
You have 3......all with differing 'gateways'.
Start from the ADSL. (This is the 'point-of-entry'...into your house, isn't it?)
And, work back to your computer.....making sure that each 'connection'......recognizes that 'original gateway'(of your ADSL).

In essense, you are 'daisy-chaining'.......linking every UNIT.......to the ADSL 'starting-point'.(Regardless of the fact THAT you are using a 'wireless set-up'...within the house.)

---

