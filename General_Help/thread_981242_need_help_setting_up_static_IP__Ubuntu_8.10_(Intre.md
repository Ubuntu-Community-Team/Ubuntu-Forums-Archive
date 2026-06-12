---
title: "need help setting up static IP  Ubuntu 8.10 (Intrepid Ibex)"
date: 2008-11-13
forum: General Help
---

### Post by mikel66109 on 2008-11-13
Ok let me start off by saying I'm new to linux.  Just changed from a windows server to Linux and i dont know how to set up a static ip.  It seems to be using DHCP.  I used this command to get my info but Im not even sure that i get the right info. sudo /sbin/ifconfig
This is the output from that command.
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:d0:22:ed  
          inet addr:72.128.26.215  Bcast:255.255.255.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:33556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9816 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8843360 (8.8 MB)  TX bytes:814100 (814.1 KB)
          Interrupt:251 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111022 (111.0 KB)  TX bytes:111022 (111.0 KB)

vnet0     Link encap:Ethernet  HWaddr 32:84:09:e1:44:9c  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::3084:9ff:fee1:449c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:11787 (11.7 KB)


My problem is that i dont know what to do with this info now that i have it.
I used this command to open the file I was told i needed to edit.
sudo gedit /etc/network/interfaces
This is the info in the file.
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

Now I just need to figure out what info from above needs to go in the interfaces file.
I was told at one point that i need to add this info to the file.
    # The primary network interface

    auto eth0
    iface eth0 inet static
    address 72.128.26.215
    netmask 255.255.240.0
    network I dont know where to find this info in linux
    broadcast 192.168.122.255  
    gateway I dont know where to find this info in linux

I think thats all the info i need but like i said im new to linux.
Please any help would be great.

---

### Post by porchrat on 2008-11-13
rather set it up using the network manager GUI.

Go to the network icon in the top right corner.  Left click it and select "VPN Settings" (or something like that).  Then open the "wired networks" tab and add a new connection.  Go into the connection and in there change it form DHCP to manual, change the IP settings and you're A for away.

---

### Post by Iowan on 2008-11-13
I've heard of a possible Network Manager update that might solve the problems NM has with static setups.  Otherwise, [this]("http://ubuntuforums.org/showthread.php?t=974382") thread promises a workaround.

---

