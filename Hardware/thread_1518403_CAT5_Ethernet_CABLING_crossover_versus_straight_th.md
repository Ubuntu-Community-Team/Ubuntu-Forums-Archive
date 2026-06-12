---
title: "CAT5 Ethernet CABLING: crossover versus straight thru"
date: 2010-06-26
forum: Hardware
---

### Post by ozark_hillbilly on 2010-06-26
I am in the midst of a perplexing problem that has CAT5 ethernet cabling at it's core.
I have a desktop and laptop computer that I use to gain internet access. Recently my desktop computer failed to link up running LINUX and working off a red CAT5 crossover cable that connects to my POE module and the microwave receiver. There is a Trendnet USB adapter that connects the ethernet cable to the desktop (thru a USB port).At present I can boot up under Windows 98 and connect to the Web using the crossover cable. I can also get web access thru the laptop pc using a straight thru CAT5 cable hooked to the POE module. The straight thru cable will not work with the desktop pc. Only the crossover cable works with the desktop. Right now I am accessing the web with the desktop running my alternate OS: WIN98 and using the crossover cable. Linux and it's browsers will not connect. I have an active eth4 connection but no data.
Pinging under Linux shows alot of packet loss. Running Intrepid Ibex and accessing the web have been peachy for a long time til now.


According to my service provider the cat5 should be a straight thru cable unless going thru some sort of switch (which I'm not).

Is there a driver configuration file I need to change or something? This is not making much sense.

Help!

Ed

---

### Post by neovandeen on 2010-06-27
If you want to connect two computers directly you have to use a crossover cable. If any of the devices network card can handle auto-sensing, you don't have to bother. But it sounds like they don't have this feature.

How do the two pc's get their IP addresses? Is there a DHCP Server, such as a router in your network, or do you use static IP addresses?

I'd like to see some output from
Linux:
```
ifconfig
```
```
route -n
```


Windows:
```
ipconfig
```
```
route print
```

Maybe there is something wrong with your default gateway.

---

### Post by ozark_hillbilly on 2010-06-27
neo,

Here is Windows data:

************************************************************************

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Owner>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection 6:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 172.17.6.21
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 172.17.6.1

C:\Documents and Settings\Owner>route print
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x10003 ...00 50 b6 07 29 69 ...... ASIX AX88772 USB2.0 to Fast Ethernet Adapter
 - Packet Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Dest  Netmask    Gateway    Interface  Metric
 0.0.0.0       0.0.0.0   172.17.6.1  172.17.6.21       30

 127.0.0.0     255.0.0.0 127.0.0.1   127.0.0.1       1

 172.17.6.0    255.255.255.0  172.17.6.21  172.17.6.21  30

 172.17.6.21  255.255.255.255  127.0.0.1 127.0.0.1       30

172.17.255.255 255.255.255.255 172.17.6.21 172.17.6.21  30

224.0.0.0     240.0.0.0     172.17.6.21 172.17.6.21   30

255.255.255.255 255.255.255.255 172.17.6.21  172.17.6.21 1

Default Gateway:        172.17.6.1
===========================================================================
Persistent Routes:
  None

*******************************************************************************

Linux data:

ed@House:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:d8:54:1b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0xa000 

eth4      Link encap:Ethernet  HWaddr 00:50:b6:07:29:69  
          inet addr:172.17.6.21  Bcast:172.17.6.255  Mask:255.255.255.0
          inet6 addr: fe80::250:b6ff:fe07:2969/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:126 errors:1 dropped:0 overruns:0 frame:1
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9652 (9.6 KB)  TX bytes:4404 (4.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:440 (440.0 B)  TX bytes:440 (440.0 B)

ed@House:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.17.6.0      0.0.0.0         255.255.255.0   U     1      0        0 eth4
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth4
0.0.0.0         172.17.6.1      0.0.0.0         UG    0      0        0 eth4
ed@House:~$ 



Would doing a system restore under Linux possibly remedy this problem?

---

### Post by jflaker on 2010-06-27
> **ozark_hillbilly said:**
> neo,

I would give you the data requested but I have two problems.
Running under Windows command prompt how do I save the ipconfig and route print data. I can "select all" but can't get it into a file.

Under Linux I can get the data but will have to figure out how to get it over to Win XP to leave it on this thread.

Would doing a system restore under Linux clear this problem up?

to file any command output, do:

ipconfig > c:\PathTo\YourFile\YourOutputFile.txt

if you want to append the information from multiple commands, then use >> two arrows as one arrow will overwrite and two will append to the file.

---

### Post by ozark_hillbilly on 2010-06-27
thanks.
I appended my msg to neo with the Windows data. Now to figure out getting the Linux results on here.

Ed

---

### Post by neovandeen on 2010-07-01
Things look good. Both IP and default route are present. Was this the laptop or the desktop? 
The MAC address tells me, that it was only one machine (00:50:b6:07:29:69). Could you please show me the output from the second one?

Neo

---

### Post by ozark_hillbilly on 2010-07-01
Neo,

The data is all from the Desktop. Getting info from the laptop would be tricky as I have no transfer medium. I guess I could try to send an email to myself with the Laptop info and grab it off the Desktop.

It is really screwy as BOTH the Jaunty Jack and Lucid Lynx installs give me intermittent web connection. I never know from boot to boot if they will connect or not. I was hoping to eliminate the problem by going forward to 10.04. 
Now I have to try and upload all my personal data files from Jaunty as the import function on the Lucid Lynx install bombed.

Seems to ALWAYS be sumthin' screwy in Denmark....

---

