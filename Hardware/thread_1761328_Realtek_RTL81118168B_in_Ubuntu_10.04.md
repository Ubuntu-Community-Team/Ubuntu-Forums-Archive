---
title: "Realtek RTL8111/8168B in Ubuntu 10.04"
date: 2011-05-18
forum: Hardware
---

### Post by Richardcavell on 2011-05-18
Hi everyone.  I'm on 32-bit Ubuntu 10.04.  On Windows, my NIC works perfectly.  On Ubuntu on the same machine, it doesn't.  lspci gives:

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

linux-firmware is installed and up to date.  A wireless card on the same machine works both in Windows and Ubuntu.  What should I do?

TIA,

Richard

---

### Post by mr_luksom on 2011-05-18
Hi Richard,

You need the specific Realtek driver for your NIC. They are available for download from the Realtek site. I took a look and found these: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D(L)%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8168E](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D(L)%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8168E)

It will include enclosed instructions for compiling and loading the driver into the kernel.

I haven't used this NIC specifically, however I have used others that are similar. If you have issues, post back.

---

### Post by Richardcavell on 2011-05-18
Hi,

It appears to be installed.  However, if I reboot, it's no longer installed.  How do I make it stick?

Also, it doesn't appear to be working.  When I turn off my wireless connection, I have no Internet connection.

Richard

```


richard@richard-desktop:~/Desktop/r8168-8.023.00$ ls
Makefile  README  autorun.sh  src
richard@richard-desktop:~/Desktop/r8168-8.023.00$ sudo ./autorun.sh

Check old driver and unload it.
rmmod r8169
Build the module and install
[: 48: r8168: unexpected operator
Depending module. Please wait.
load module r8168
Completed.
richard@richard-desktop:~/Desktop/r8168-8.023.00$ lsmod | grep r8168
r8168                 161151  0 
richard@richard-desktop:~/Desktop/r8168-8.023.00$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:27:40:2f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10536 (10.5 KB)  TX bytes:10536 (10.5 KB)

wlan0     Link encap:Ethernet  HWaddr d8:5d:4c:a3:9a:44  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::da5d:4cff:fea3:9a44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1072 errors:0 dropped:0 overruns:0 frame:0
          TX packets:732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:754250 (754.2 KB)  TX bytes:121931 (121.9 KB)

```

---

### Post by mr_luksom on 2011-05-19
Auto loading of driver on bootup:

I never had to do this when installing my drivers, however I believe if you edit /etc/
modules, adding the module name it will be loaded at boot time.

As for the driver not actually working:

I think I know the answer to this, but can you configure eth0 via network manager? If not, what does 'ifconfig eth0 up' do? Does your 'ifconfig -a' look any different?

Can you post a 'dmesg | grep r8168', and a 'dmesg | grep eth0'?

---

### Post by Richardcavell on 2011-05-20
I added the line "r8168" to my /etc/modules.  Now I get:
```

richard@richard-desktop:~$ lsmod | grep r81
r8168                 161151  0 
r8169                  34108  0 
mii                     4381  1 r8169

```
System->Preferences->Network Connections currently does not know of any wired connection.  (If I reinstall the driver from source, "Auto eth0" will appear but will be gone the next time I reboot).

sudo ifconfig eth0 up does absolutely nothing.  ifconfig -a looks different the one I first posted, after I added a line in /etc/interfaces at the suggestion of someone on IRC.  It now contains this:
```

eth0:avahi Link encap:Ethernet  HWaddr 1c:6f:65:27:40:2f  
          inet addr:169.254.4.154  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:28 Base address:0x6000 

```
```

richard@richard-desktop:~$ dmesg | grep r8168
richard@richard-desktop:~$ dmesg | grep eth0
[    1.571450] eth0: RTL8168d/8111d at 0xf8036000, 1c:6f:65:27:40:2f, XID 083000c0 IRQ 28
[   18.716406] r8169: eth0: link down
[   18.716545] ADDRCONF(NETDEV_UP): eth0: link is not ready

```
I just tested the cable with a different computer, and the cable is fine.  The same NIC works in Windows on the same computer.

---

### Post by Richardcavell on 2011-05-29
Hi, everyone.

Just for the sake of completeness, I'll add that testing the NIC with Realtek's own diagnostic utility in Windows shows that the NIC hardware is faulty.  So it's not an Ubuntu problem.  Please move along.

Richard

---

### Post by bhagatg on 2011-07-01
Hi Richard,
                   I have similar problem with the wireless driver. I followed the steps that you have mentioned and i didn't see wlan in my response. Appreciate if you can help me out.

Steps followed:
============
gopi@gopi:~/Desktop/r8168-8.024.00$ ls
autorun.sh  Makefile  README  src
gopi@gopi:~/Desktop/r8168-8.024.00$ sudo ./autorun.sh 

Check old driver and unload it.
rmmod r8169
Build the module and install
[: 48: r8168: unexpected operator
Backup r8169.ko
rename r8169.ko to r8169.bak
Depending module. Please wait.
load module r8168
Completed.
gopi@gopi:~/Desktop/r8168-8.024.00$ lsmod | grep r8168
r8168                 173834  0 
gopi@gopi:~/Desktop/r8168-8.024.00$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr f0:de:f1:65:87:fa  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f2de:f1ff:fe65:87fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19353 (19.3 KB)  TX bytes:8030 (8.0 KB)
          Interrupt:45 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

gopi@gopi:~/Desktop/r8168-8.024.00$ sudo ./autorun.sh 

Check old driver and unload it.
rmmod r8168
Build the module and install
[: 48: r8168: unexpected operator
Depending module. Please wait.
load module r8168
Completed.
gopi@gopi:~/Desktop/r8168-8.024.00$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr f0:de:f1:65:87:fa  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f2de:f1ff:fe65:87fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5911 (5.9 KB)  TX bytes:7786 (7.7 KB)
          Interrupt:45 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

gopi@gopi:~/Desktop/r8168-8.024.00$ 

gopi@gopi:~/Desktop/r8168-8.024.00$ sudo lshw -C network
[sudo] password for gopi: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:65:87:fa
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.024.00-NAPI duplex=full ip=192.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:45 ioport:5000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:d1d00000-d1d03fff
gopi@gopi:~/Desktop/r8168-8.024.00$ 


I'm not sure whats going on. I tried all different ways of installing the driver and finally found that your approach is much closer one.  Would really appreciate your effort thanks.

Thanks,
Gopi

---

