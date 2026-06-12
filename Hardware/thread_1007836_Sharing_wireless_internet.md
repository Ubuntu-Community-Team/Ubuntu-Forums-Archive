---
title: "Sharing wireless internet"
date: 2008-12-10
forum: Hardware
---

### Post by -Cluster- on 2008-12-10
Ok i have read sooooo many how to's and i think i have gone i FUBARed the whole thing

After all these tutorials i found out about firestarter 

installed it and it says eth0 not ready

so i see some more tutorials and the menus it talks about don't exist
System>Administrator>Networks

all i have is network tools with no option to get properties on the eth0

Now in the top right where i click the network connection it doesn't seem to connect to the eth0


help.....

---

### Post by iponeverything on 2008-12-10
start from the begining.

what are your trying to do. How do you want to do it. What is your current setup. And provide provide some details on what your running.

---

### Post by iponeverything on 2008-12-10
don't know how the top one got dup'ed

---

### Post by -Cluster- on 2008-12-11
ok ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:13:a9:82:a2:fe  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19160 (19.1 KB)  TX bytes:19160 (19.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:6c:f9:67  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe6c:f967/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:139795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:204217102 (204.2 MB)  TX bytes:7029261 (7.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-6C-F9-67-39-36-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I have a Vaio laptop AR21S, i am trying to connect to the internet wirelessly (wlan0) then share this internet via and ethernet cable (eth0) (cross over) to my xbox.

I have followed a few tutorials and got as far as to understanding i need firestarter.

However when i run firestarter it says "eth0 not ready". I found a thread that said make the eth0 static so:

sudo ifconfig eth0 192.168.3.1

This then makes firestarter work but an Unknown error message comes up before hand. The thread said this happened but it still worked but mine didn't i could not connect my xbox to the my laptop.

I think thats all you need to know

---

### Post by iponeverything on 2008-12-11
You don't need firestarter.


Configure Eth0 like so:

```
sudo nano /etc/network/interfaces

```
Add the section:

```

auto eth0

iface eth0 inet static
address 192.168.3.1
netmask 255.255.255.0

```

now edit:
```
sudo nano /etc/rc.local
```

Add:

```
iptables -t nat -A POSTROUTING -s 192.168.3.0/24  -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/conf/all/forwarding
exit 0

```

Then reboot.

Then configure your Xbox to with an IP address of say 192.168.3.2 and netmask of 255.255.255.0 and gateway of 192.168.3.1

And it should be good to go.  If the Xbox needs DNS servers have it use:

the opendns servers at 208.67.222.222 and 208.67.220.220.

---

### Post by -Cluster- on 2008-12-11
Mate you are a solid legend

Works a dream.....but

I can't use my ethernet for anything else how do i revert what i did?
just delete what i wrote?

---

### Post by iponeverything on 2008-12-11
There are a number of ways of doing it. There is good example in the interfaces man page "man interfaces"

or you could just have a the old interfaces file as interfaces.orig and copy it back into place and run:

```
sudo ifconfig eth0 down; sudo /etc/init.d/network restart
```

or reboot.

---

### Post by -Cluster- on 2008-12-12
Thanks a lot mate

Tell you what i did labeled the code i put in and simple put "#" in front of it when i need it take them out when i don't put them back

---

