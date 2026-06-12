---
title: "Wireless dropped off.."
date: 2010-02-05
forum: Hardware
---

### Post by Coach_Mark on 2010-02-05
I am running 32-bit 9.04 on a Dell laptop.  A few days ago, I stopped picking up wireless signals.  A friend asked a couple of questions, but wasn't sure what was going on.  He then suggested I post all the information I have/found here to see if anyone else had any ideas.  OK...here is what i see:

Upper right side.  You have the network icon thing, the calendar and the user name menu thing.  When I click the network icon, I get the following options:  "wired network" (gray), "Auto Eth0" (black, with a dot next to it), "wireless networks" (gray), then "VPN connections" (black, not bold) with a submenu of "configure VPN" (black) and "disconnect VPN" (grey).  next on the main list, I get "connect to hidden wireless network" followed by "create wireless network."  Now, in >System>Preferences>Network Connections, the wireless tab has my wireless connection listed.  But, it does not connect.  When I open the edit function for my network and click on the tab for IPv4 Settings, it has Method as "automatic (DHCP)."  The DHCP Client ID box is blank.

He also had me run "uname -a" and "ifconfig".  Here are the outputs:

coach@coach-laptop:~$ uname -a
Linux coach-laptop 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009 i686 GNU/Linux
coach@coach-laptop:~$ 


coach@coach-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:ae:41:9f:01  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:aeff:fe41:9f01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:644854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:348767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:788697265 (788.6 MB)  TX bytes:31608138 (31.6 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:5f:be:40:45  
          inet6 addr: fe80::222:5fff:febe:4045/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1616 (1.6 KB)  TX bytes:1616 (1.6 KB)

coach@coach-laptop:~$

Does anyone have any ideas what happened?  (my apologies if this is in the wrong thread, by the way...just wasn't sure where this should go)

---

### Post by mellors.john on 2010-02-05
same thing happened to me... very frustrating

---

### Post by Coach_Mark on 2010-02-06
OK.  I just had my DUH! moment for a while... There is a BIOS function on Dell computers (specifically the Inspirion 1545) which allows you to set the function keys to either function or multimedia.  I had it set for function, because I don't use the multimedia by default.  but somehow the multimedia for wireless got keyed--turning off the wireless modem. 

So, for anyone with a Dell that experiences this...here is your possible fix.

---

