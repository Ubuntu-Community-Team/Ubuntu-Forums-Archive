---
title: "Network manager cant detect wireless network card....."
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by Tails on 2006-11-05
For some odd reason, Network Manager can't detect my broadcom wireless network card.... and I installed the driver...

> 
tails@laptop:~$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present 



any idea why???

Thanks!

:D

---

### Post by happy-and-lost on 2006-11-05
Is this an Acer machine?

---

### Post by chriscando on 2006-11-05
I too am unlucky enough to have a Broadcom wireless card.
Double check that the ndiswrapper module is loaded 'lsmod |grep ndiswrapper'
If its not just 'sudo modprobe ndiswrapper' to bring it up.

---

### Post by pitkali on 2006-11-05
> **Tails said:**
> For some odd reason, Network Manager can't detect my broadcom wireless network card.... and I installed the driver...

You have to remove your wireless interface from /etc/network/interfaces. Network Manager handles only interfaces not listed there.

Regards,

---

### Post by Tails on 2006-11-05
Thanks for the replies, but still not working.. :(


@happy-and-lost: Nope, it is a compaq R4100

@chriscando:

Here is the output of it...

```

tails@laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           208656  0 
usbcore               134912  5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd

```

@pitkali:.. not working either.. :(

here is the content of the interface file atm..

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.51
netmask 255.255.255.0
gateway 192.168.1.1

```

Thanks! :)

---

### Post by pitkali on 2006-11-05
Just to ensure - eth0 is your Ethernet wired card, right?

In any case - what does ifconfig -a say? Or iwconfig -a?

---

### Post by Tails on 2006-11-05
> **pitkali said:**
> Just to ensure - eth0 is your Ethernet wired card, right?

In any case - what does ifconfig -a say? Or iwconfig -a?

yes, eth0 is the wired card

```

tails@laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:75:49:9C  
          inet addr:192.168.1.51  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:358 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:465943 (455.0 KiB)  TX bytes:29825 (29.1 KiB)
          Interrupt:225 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.84.1  Bcast:172.16.84.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.169.1  Bcast:192.168.169.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

vmnet1 and vmnet8 is used by VMWare...

```

tails@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

```

---

### Post by pitkali on 2006-11-05
So it is a driver issue after all (the interface does not show up in ifconfig -a). Unfortunately I won't be able to help with that - I'm the happy owner of Intel card.

Good luck,

---

### Post by DC@DR on 2006-11-09
Hi Tails,

I'm happily enjoying the Broadcom wireless card using ndiswrapper in Dapper right now, so just to make sure with you that ndiswraper works fine with Broadcom cards.

Here is what I have:
```

lspci | grep Broadcom
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

Then:
```

ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

```

If you did install the bcm43xx driver, remove/blacklist it using:
```

sudo rmmod bcm43xx
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

```

I assume you did install ndiswrapper-utils, then where you got driver files from? I got mine from: [http://home.nc.rr.com/thehinnants/stuff/drivers/](http://home.nc.rr.com/thehinnants/stuff/drivers/) (copy both files .inf and .sys). Make sure after running this step by step to get the things done right:

```

sudo ndiswrapper -m
sudo modprobe ndiswrapper

```

Double check by issuing this:
```

cat /etc/modules

```
to make sure ndiswrapper is there.

Then here is the tricky part --> open your favorite text editor, then put this bash scripts in a file called editconf.sh:
```

#!bin/bash
for conffile in /etc/ndiswrapper/bcmwl5/*.conf
do
   sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done

```

then make it executable:
```

sudo chmod +x editconf.sh

```

then run it by:
```

sh editconf.sh

```

then follow by: 
```

sudo /etc/init.d/networking restart

```
or just reboot, then when you do:
```

sudo ifconfig -a

```
you will find your wireless card there, as in mine like this:
```

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:BB:8E:5D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1072 (1.0 KiB)  TX bytes:1072 (1.0 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0B:7D:17:5C:53
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:7dff:fe17:5c53/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1893 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2014570 (1.9 MiB)  TX bytes:216707 (211.6 KiB)
          Interrupt:5 Memory:fafee000-faff0000

```

if you do:
```

sudo iwlist _your_wireless_interface_name scanning

```
then get some scanning results, your driver should be working properly now :)

---

