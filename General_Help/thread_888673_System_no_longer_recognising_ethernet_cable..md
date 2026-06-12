---
title: "System no longer recognising ethernet cable."
date: 2008-08-13
forum: General Help
---

### Post by Cantankerous on 2008-08-13
I have only just installed the latest version of Ubuntu, and due to a misunderstanding at the partitioning section of installation, i no longer have access to Vista. But i don't really mind this, i wanted XP anyway.
**_The real problem:_**
The system won't recognise that i have an ethernet cable plugged in. Or, atleast, it seems this way.
It lights up as per usual, but it won't actually work. I cannot access the internet at all; i cannot download the software needed to activate drivers for my Graphics card, nor can i download general updates.
I'm sorry if this is the wrong forum for this sort of problem, perhaps i was being a bit too pedantic while looking for where to post this.

---

### Post by theyranos on 2008-08-13
With the cable plugged in, please run
```
sudo /etc/init.d/networking restart
``` and ```
ifconfig
``` from a terminal and get the output on this form somehow. (My suggestion is to copy-and-paste to a text file on a flash drive.)

---

### Post by Cantankerous on 2008-08-13
I've just done what you said, here's what comes up:
```
robert@Roberts:~$ sudo /etc/init.d/networking restart
[sudo] password for robert: 
 * Reconfiguring network interfaces...                                   [ OK ] 
robert@Roberts:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2414 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:120892 (118.0 KB)  TX bytes:120892 (118.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:aa:8b:5b  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:feaa:8b5b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:6434 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8696084 (8.2 MB)  TX bytes:658577 (643.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-AA-8B-5B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by theyranos on 2008-08-13
If you type **ifconfig eth0** do you get a "Device not found" message? If so, Ubuntu probably hasn't loaded the drivers for your ethernet card. 

Please paste the output of
```
lspci
```

---

### Post by Cantankerous on 2008-08-13
Aha, it does say device not found:
```
robert@Roberts:~$ ifconfig eth0
eth0: error fetching interface information: Device not found
robert@Roberts:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0405 (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)
08:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
```

---

### Post by TreeFinger on 2008-08-13
this thread may help you:

[http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)

---

### Post by theyranos on 2008-08-13
Here's your problem:

> **Cantankerous said:**
> Aha, it does say device not found:
```

02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)
```

It looks like getting the driver for your card is going to take some work. There are driver building instructions posted [here](http://ubuntuforums.org/showpost.php?p=4825848&postcount=7). Since I haven't got one of these cards, the best I can do at this point is wish you luck.

Good luck.
-Theyranos

**Edit:** *Aah, TreeFinger beat me to it :)*

---

### Post by Cantankerous on 2008-08-13
Ah, thanks very much, both of you!

Was panicking for while there :P

EDIT:
> cd into <HOME_DIR>/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src
Could anyone inform me as to what they mean by "cd into"?

---

### Post by theyranos on 2008-08-18
They're assuming you're using a terminal for the entire process. Once you've extracted the zip, you should open up a terminal and type ```
cd */path/to/that/src/directory/they/reference*
```replacing */path/to/that/src/directory/they/reference* with wherever your archiver put the l1e-l2e-linux-v1.0.0.4/src folder.


sidenote: I'm not aware of any way to get ubuntuforms to send e-mail notifications when a post in a thread gets edited. And that's why the response took so long. Sorry.

---

