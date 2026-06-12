---
title: "Wireless problems"
date: 2011-09-13
forum: Hardware
---

### Post by fekioh on 2011-09-13
Hello,

I am running Ubuntu 11.04 on a Satellite Pro L100 TOSHIBA laptop. 

Strange problem: my wireless stopped working. I found some posts about the Fn-F8 combination not working, so if wireless was switched off under windows there was problem, but the strange thing is that my wireless was working OK till a few days ago in Ubuntu and now it's turned off, for... who knows why! maybe someone out there?

Thanks!

Here's some more information[COLOR=Black] from the terminal[/COLOR]:
[COLOR=Red]fekioh@fekiohpc:~$ [/COLOR][COLOR=Red]sudo lshw -C network[/COLOR]
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:bd:20:37
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-11-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:41 memory:24000000-24000fff

[COLOR=Red]fekioh@fekiohpc:~$ rfkill list[/COLOR]
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
fekioh@fekiohpc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:6c:24:db  
          inet addr:192.168.1.80  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe6c:24db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1402 errors:5 dropped:5 overruns:5 frame:0
          TX packets:1178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1381606 (1.3 MB)  TX bytes:184414 (184.4 KB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

[COLOR=Red]fekioh@fekiohpc:~$ iwconfig[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by fekioh on 2011-09-13
Still no solution. I tried several things suggested in forums. All I managed was that the drop down meny message changed :) Now under Wireless networks it says "wireless is disabled by hardware switch". SOme help please?

---

### Post by fekioh on 2011-09-13
Oh and rfkill confirms:

fekioh@fekiohpc:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by fdrake on 2011-09-13
can you change your wifi with the bios. check your bios setting /or your switcher

---

### Post by fekioh on 2011-09-13
No, trying to go round it from the BIOS was the first thing I tried. But I didn't find any option there for wireless.

---

### Post by Pariah819 on 2011-09-13
Are you sure that there is no external switch that can enable and disable the wireless device?

---

### Post by fekioh on 2011-09-13
Haha yeh external switch... That was it. Sorry, new laptop... Sorry for wasting your time.

---

### Post by Pariah819 on 2011-09-13
No problem, please mark the thread as solved unless you need anything else.

---

