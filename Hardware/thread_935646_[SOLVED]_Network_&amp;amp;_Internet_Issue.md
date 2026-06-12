---
title: "[SOLVED] Network &amp;amp; Internet Issue"
date: 2008-10-01
forum: Hardware
---

### Post by legal on 2008-10-01
Hello Ubuntu Forums!!

i just switched from Windows and im proud haha.

well i got this small problem.

when i boot in sometimes my internet doesn't work. so i have to reboot 2 or 3 times for it to fix.

So is there a way to fix this?

thanks for the help in advance.

---

### Post by doas777 on 2008-10-01
howdy, and welcome. 

ok, to start off could you open a terminal and run these commands? 

List your hardware
```

lspci

sudo lshw -C network

```

Show your IP address and nic info (like IP config)
```

sudo ifconfig

```


please post the output of these commands, so we can see what the devices status is.

do you use a router at home or are you directly connected to the isp network?

---

### Post by legal on 2008-10-02
```
 
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff)
04:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)

``` 
Second Command

```
 
	*-generic               
       description: Ethernet interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: ff
       serial: 00:1e:8c:76:60:b7
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=twisted pair speed=1GB/s


```

and last command outputted

```

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:76:60:b7  
          inet6 addr: fe80::21e:8cff:fe76:60b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967280 overruns:0 frame:0
          TX packets:0 errors:0 dropped:138 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:8c:76:60:b7  
          inet addr:169.254.7.172  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2624 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2624 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:134057 (130.9 KB)  TX bytes:134057 (130.9 KB)


```

and i am connected to a router. could that be the problem?

---

### Post by doas777 on 2008-10-02
it looks like you are having DHCP problems, thought I can't say why as of yet.

no the Router will not be a problem. just needed to establish if there was one. I assume you have it set up to serve DHCP?

the easiest way to tell if it's a DHCP problem, would be to reboot until is DOESN'T work, then open a terminal and run:
```

ifdown eth0
ifup eth0

```

this is akin to windows "ipconfig /release ; ipconfig /renew", and will (among other things) request a new address from the local DHCP server. if it is successful, your internet should work without rebooting. Let us know whether that works, and if so, post the output of ifconfig again.

if it is a DHCP problem, one easy fix is to just establish a static IP address for your lan in the network manager.

---

### Post by legal on 2008-10-02
i tried those 2 commands and it gave me these errors

```

ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0

```

---

### Post by doas777 on 2008-10-02
ok try just running ifup and see if that does anything. 

ok it looks like you are having a hardware/driver problem then. 
can you post the contents of you network [interfaces ]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/")file?

```
sudo gedit /etc/network/interfaces
```

I can help you with network configuration issues, but driver issues may be beyond my knowledge, so if all else fails, hopefully another more knowledgeable poster will find their way to your thread.

---

### Post by legal on 2008-10-02
ok.

contents of the file is.

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 ined dhcp

```

EDIT : By the Way the Hardware Test thing does see NIC. and it says no internet. on the next test

---

### Post by legal on 2008-10-02
FIXED!

all i did was remove

```

auto eth0
iface eth0 ined dhcp

```

from /etc/network/interfaces

---

### Post by doas777 on 2008-10-02
> **legal said:**
> FIXED!

all i did was remove

```

auto eth0
iface eth0 ined dhcp

```

from /etc/network/interfaces

Kewl!

just out of curisoity, does it actually say "ined" or "inet" ?

---

### Post by legal on 2008-10-02
i jump for joy too early -.-

haha it doesn't work anymore ^.^

and i fixed the inet stuff haha i feel stupid ^.^ lol

---

### Post by doas777 on 2008-10-02
> **legal said:**
> i jump for joy too early -.-

haha it doesn't work anymore ^.^

and i fixed the inet stuff haha i feel stupid ^.^ lol

no worries man. 

do you wanna try a static ip address?

run ifconfig while the internet is working and make note of your Gateway IP address (it's probably 192.168.0.1).

[here]("http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/") is a tutorial on configuring your nic for static IP.

it may work, but I'm starting to think you have a more serious issue. give it a try.

---

### Post by legal on 2008-10-02
ok ill try that ill post once i do everything

---

### Post by legal on 2008-10-02
ok i did the ip thing. most of it

but when he asks the the servername thing using the

ifconfig /all

it says there is no command or something like that for the "/all"

---

### Post by doas777 on 2008-10-03
> **legal said:**
> ok i did the ip thing. most of it

but when he asks the the servername thing using the

ifconfig /all

it says there is no command or something like that for the "/all"

your right, there is no /all switch for ifconfig command. you don't need it, since ifconfig shows you maximal output. you can just use "ifconfig".

I'm a little confused on "the servername thing". could you describe what your doing?

---

### Post by legal on 2008-10-03
Well. in the tutorial you gave me it asks me to change the name server or add a new name server in the ile

```

sudo vi /etc/resolv.conf

```

---

### Post by legal on 2008-10-03
I fixed it. officially this time.

i upgrade my NIC Card's Drivers with more recent.

and set a static IP and it work.

---

### Post by doas777 on 2008-10-04
> **legal said:**
> I fixed it. officially this time.

i upgrade my NIC Card's Drivers with more recent.

and set a static IP and it work.

excelent!

---

