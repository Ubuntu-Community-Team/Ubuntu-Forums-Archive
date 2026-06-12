---
title: "Problems with Belkin: Wireless Desktop Network Card F5D6001"
date: 2008-08-09
forum: General Help
---

### Post by sendblink23 on 2008-08-09
This is my THREAD over NETWORK & WIRELESS 
(seems nobody is helping over there) :/
[http://ubuntuforums.org/showthread.php?t=884900](http://ubuntuforums.org/showthread.php?t=884900)

Problems with Belkin: Wireless Desktop Network Card F5D6001

Well I was trying to figure how to make it work.. during the process I messed up my BOOT & Lots of other stuff of Ubuntu, so I decided to *Erase partition & Refresh Install again Ubuntu (just to make sure I don't have anything messed up, on any of the commands i had made before from terminal)

Well now that I'm Fresh New again in Ubuntu, can anybody help me out Again how to be able to fix it?? YES I have internet through connected in LAN Ethernet, I updated everything of Ubuntu, I have Flash working on Youtube (still haven't fix the sound for Youtube page)... Anyways I really need to be connected through Wireless *personal Reasons ;) (And the *Wireless doesn't appear in the GUI of NETWORK)

*NOTE I'm a NOOB, so please explain NOOBIE WAY*

---

### Post by sendblink23 on 2008-08-09
anybody Want to help me ???

---

### Post by nathaniel.porter45 on 2008-08-09
[http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

This is the same link I used for my wireless internet. I had the same problem a couple of days ago. I´m extremely new at this too.

---

### Post by sendblink23 on 2008-08-09
> **nathaniel.porter45 said:**
> [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

This is the same link I used for my wireless internet. I had the same problem a couple of days ago. I´m extremely new at this too.

Nopes that didn't work .. that was actually the First method i tried...

And my hardware does show *Present..

```
sendblink23@sendblink23-desktop:~$ sudo ndiswrapper -l
bel6001 : driver installed
	device (1799:6001) present
sendblink23@sendblink23-desktop:~$ 

```


here where i have my problem during that Method:

```
5. Activating your wireless card via terminal

Here is everything you should need to know for bringing up a wireless (or any internet connection) from the terminal. Keep in mind that your wireless connection may not always be called wlan0. For example, my interface is eth1. the command "iwconfig" should give you the interface name.

To scan for a wireless network (essid)
Code:

sudo iwlist wlan0 scan

To bring up the interface
Code:

sudo ifconfig wlan0 up

To bring down the interface
Code:

sudo ifconfig wlan0 down

To connect to a router
Code:

sudo iwconfig wlan0 essid ID key k

where "ID" is the name of the router you want to connect to (returned by iwlist scan wlan0), and "k" is the network key to connect to the router

Now that you know what each command does, here is what most people should have to type into their terminal
Code:

sudo iwlist wlan0 scan
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid ID key k

I am unsure if this terminal method works with WPA encryption, so keep that in mind, as I use WEP because of the difficulty I have had with WPA in general. In theory it should work, but I don't know if thee are any extra steps to it.
```


Well how can i get "Keep in mind that your wireless connection may not always be called wlan0. For example, my interface is eth1. the command "iwconfig" should give you the interface name."

I tried that and this is what it shows for me:
```
sendblink23@sendblink23-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sendblink23@sendblink23-desktop:~$ 

```


Any help there?

---

### Post by sendblink23 on 2008-08-09
Any other help people?  :)

---

### Post by nathaniel.porter45 on 2008-08-09
sorry =/. I´d help if I knew how to. once I installed ndiswrapper for my drivers, I just went to System->Administration->Networking found my router and it established the connection. Sorry again for my lack of information.

---

### Post by sendblink23 on 2008-08-09
Bump

---

### Post by sendblink23 on 2008-08-09
Bump

---

### Post by sendblink23 on 2008-08-09
I just found this wierd ...

Can anybody verify whats going on here and well can this Info help you gusy help me??

```
sendblink23@sendblink23-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:d8:f2:07:16  
          inet addr:10.0.0.64  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fef2:716/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2806 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3535677 (3.3 MB)  TX bytes:259133 (253.0 KB)
          Interrupt:21 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:105800 (103.3 KB)  TX bytes:105800 (103.3 KB)


```
```

sendblink23@sendblink23-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:f2:07:16
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.0.0.64 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Wireless PCI Card - F5D6001
       vendor: Belkin
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
sendblink23@sendblink23-desktop:~$ 
```

---

### Post by sendblink23 on 2008-08-09
> **sendblink23 said:**
> i just found this wierd ...

Can anybody verify whats going on here and well can this info help you gusy help me??

```
sendblink23@sendblink23-desktop:~$ ifconfig
eth0      link encap:ethernet  hwaddr 00:11:d8:f2:07:16  
          inet addr:10.0.0.64  bcast:10.0.0.255  mask:255.255.255.0
          inet6 addr: Fe80::211:d8ff:fef2:716/64 scope:link
          up broadcast running multicast  mtu:1500  metric:1
          rx packets:2806 errors:0 dropped:0 overruns:0 frame:0
          tx packets:2098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          rx bytes:3535677 (3.3 mb)  tx bytes:259133 (253.0 kb)
          interrupt:21 base address:0xe400 

lo        link encap:local loopback  
          inet addr:127.0.0.1  mask:255.0.0.0
          inet6 addr: ::1/128 scope:host
          up loopback running  mtu:16436  metric:1
          rx packets:2116 errors:0 dropped:0 overruns:0 frame:0
          tx packets:2116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          rx bytes:105800 (103.3 kb)  tx bytes:105800 (103.3 kb)


```
```

sendblink23@sendblink23-desktop:~$ lshw -c network
warning: You should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: Rtl-8139/8139c/8139c+
       vendor: Realtek semiconductor co., ltd.
       Physical id: 2
       bus info: Pci@0000:02:02.0
       logical name: Eth0
       version: 10
       serial: 00:11:d8:f2:07:16
       width: 32 bits
       clock: 33mhz
       capabilities: Bus_master cap_list ethernet physical
       configuration: Broadcast=yes driver=8139too driverversion=0.9.28 ip=10.0.0.64 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 unclaimed
       description: Ethernet controller
       product: Wireless pci card - f5d6001
       vendor: Belkin
       physical id: 3
       bus info: Pci@0000:02:03.0
       version: 20
       width: 32 bits
       clock: 33mhz
       capabilities: Bus_master cap_list
       configuration: Latency=64 maxlatency=64 mingnt=32
sendblink23@sendblink23-desktop:~$ 
```



bump!!!!!

---

### Post by sendblink23 on 2008-08-10
thats it nobody wants to help me???  only 1 person has tried today ?

---

### Post by sendblink23 on 2008-08-10
here goes nothing....

This feels retarted ...   But I've searched back.. like way back ...   The Problem of this Driver over *LINUX* has been stated since 2003

how the hell hasn't any Programmers of Ubunto ...  Fixed this Problem *through all the Upgrades New Versions different Linux ... 

*yes only 1 version LINUX did work 
"Works out of the box in Ubuntu 6.06 (Dapper Drake)" (Wiki List)

What happened afterwards... why didn't it kept being that same way on any Later versions .. ??

... having it since 2003, they should already have in it to Automatic READ the Wireless driver Card... By now

Well I've only seen 1 person (Yesterday) *Recently stating he has his working (has the same one as me), he tried to help me...  but nothing

And so far TODAY ....  hello what's happened to the People who help around users with Wireless card driver Problems ?? No Where to be found around my Threads...  can anybody be helpful, and simply start willing to help me out?

---

### Post by sendblink23 on 2008-08-10
bump  still need help .. nobody is helping

---

### Post by Stratok on 2008-10-16
ok if it worked on 7.10, you should only need to instal ndiswrapper common and utils.. .deb versions:   [http://security.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://security.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)

install both common and utils of latest version. download ur cards driver for winxp, either drivers.com or the page from the owner. a  .zip is ussualy downloaded, copy and extract somewhere.
en la terminal cd "folder with extracted drivers", without ""
then in same terminal  sudo ndiswrapper -i "driver.inf" without ""

create a new launcher with the comand "modprobe ndiswrapper" (without the "") and click the louncher... i got an external pcmcia card working like this.

You could also install the ndiswraper gui frontend if u can find it... is easyer:guitar:

---

