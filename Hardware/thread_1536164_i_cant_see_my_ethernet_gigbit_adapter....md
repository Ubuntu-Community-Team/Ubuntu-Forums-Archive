---
title: "i cant see my ethernet gigbit adapter..."
date: 2010-07-21
forum: Hardware
---

### Post by ansary on 2010-07-21
guys when i opened** ect/network/interfaces**



i got only:

auto lo
iface lo inet loopback



my wireless adapter is ok! but my ethernet is not!

i used also the command **ifconfig** and i got:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1920 (1.9 KB)  TX bytes:1920 (1.9 KB)

wlan0     Link encap:Ethernet  HWaddr 78:e4:00:22:7a:47  
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:xxx.xxx.xxx.xxx
          inet6 addr: fe80::7ae4:ff:fe22:7a47/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46711 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42397676 (42.3 MB)  TX bytes:3517993 (3.5 MB)



please help me.. im new to ubuntu..

---

### Post by NFblaze on 2010-07-21
Go to Applications > Accessories > Terminal

Try

```
sudo ifup eth0
sudo ifup eth1
```

---

### Post by ansary on 2010-07-21
sir thanks to ur reply..

i tried your commands but i got this errors:

ansary@ubuntu:~$ sudo ifup eth0
[sudo] password for ansary: 
Ignoring unknown interface eth0=eth0.
ansary@ubuntu:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.

---

### Post by NFblaze on 2010-07-21
What does

```
sudo lshw | grep network -A 6
```

---

### Post by ansary on 2010-07-21
**i got this output from ur command:**

           *-network UNCLAIMED
                description: Ethernet controller
                product: AR8151 v1.0 Gigabit Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                version: c0
--
           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0

---

### Post by NFblaze on 2010-07-21
Seems like your driver isnt installed for the device? 

But googling says that there was a patch submitted to the kernel for your device.

What version of the Linux Kernel are you running?

```
 uname -a
```

---

### Post by ansary on 2010-07-21
sir according to the command that ugave to me (uname -a):

[B]ansary@ubuntu:~/Downloads$ uname -a
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
[/B]

---

### Post by NFblaze on 2010-07-21
Yea it looks like the Atheros Ethernet developers have worked on it.

[http://kernel.org/pub/linux/kernel/people/mcgrof/ethernet/AR81Family-linux-v1.0.1.6.tar.bz2](http://kernel.org/pub/linux/kernel/people/mcgrof/ethernet/AR81Family-linux-v1.0.1.6.tar.bz2)

Though, I didnt see any mention of it in the current kernel changelog. So, it looks like for now if you want it you will have to compile it.

---

### Post by ansary on 2010-07-21
sir actually i found this .tar.gz already..

and now my problem is.. I DONT know how to deal with this files.. how to install this files sir..

can u give some steps to install this files??

i really much appreciated sir that u really helped me some showing commands that i didnt see before..

i jot down all the commands that u showed up..

THANK U..

---

### Post by ansary on 2010-07-21
sir I installed already the tar files that u linked to me (i dont know if i installed it correctly).

i used:

./configure
make
make install


but nothing happened?
i got the same result.

           *-network UNCLAIMED
                description: Ethernet controller
                product: AR8151 v1.0 Gigabit Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                version: c0
--
           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0

---

### Post by NFblaze on 2010-07-21
Well, you just have to follow the README.

In a nutshell.

tar -xjvf AR81Family-linux-v1.0.1.6.tar.bz2
cd src
sudo make install
sudo insmod arl1e

Also, it might help to reboot.

---

### Post by ansary on 2010-07-21
hahahhaha.. I already solved it.. 

after that installation.. u need to reboot ur desktop to apply changes..

Sir THANK YOU SO MUCH .. u helped me  a lot

---

### Post by ansary on 2010-07-21
sir what command that will show the the video card that u are currently using?? (like in pci lspci -nn)

---

### Post by NFblaze on 2010-07-21
You can just use  **sudo lshw** to view all your hardware. Most likely it will be listed under VGA controller or Video Card or Graphics...etc

---

### Post by ansary on 2010-07-22
sir can u help to me my bluetooth.. im using Bluetooth 2.1+EDR.

and my probem is that it is not installed in my ubuntu desktop

---

