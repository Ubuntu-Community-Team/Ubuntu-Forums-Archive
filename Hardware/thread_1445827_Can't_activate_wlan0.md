---
title: "Can't activate wlan0"
date: 2010-04-03
forum: Hardware
---

### Post by bgaechter on 2010-04-03
Hi,

I have got an asus 1201n and i installed Ubuntu 9.04 on it.

Now i tried to get wireless working. After a while i found that[ bug on launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126"). i followed the instructions there and after i copied the driver into the right place it showd me wlan0 if used ifconfig -a

but it seems not to work correctly. It doesn't display any wireless network. if i try to bring it up it says me:

```
sudo ifconfig wlan0 up
[sudo] password for bgaechter: 
SIOCSIFFLAGS: Operation not permitted
```and that's how ifconfig -a looks like:

```
~$ ifconfig -a
eth0      Link encap:Ethernet  Hardware Adresse 48:5b:39:1e:15:eb  
          inet Adresse:192.168.1.111  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::4a5b:39ff:fe1e:15eb/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:1
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:5002 (5.0 KB)  TX bytes:5219 (5.2 KB)
          Interrupt:27 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  Hardware Adresse 1c:4b:d6:6f:3d:48  
          BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Speicher:f8678000-f8678100 

```does someone know how i can get my wireless finally working?

---

### Post by hsoulen on 2010-04-07
Hi,

I have an Asus 1201n as well.

Couple of quick questions...

You said you followed the instructions on the bug report at launchpad, which instructions did you follow? Did you install the Realtek driver from the Realtek support site or did you go with Ndiswrapper?

Here is what worked for me:

If you have installed a driver older than the one below, please "sudo make uninstall" from the folder you unpacked the driver into and reboot before proceeding.

My best advice for Karmic (9.10) is check the Realtek site for the most  recent driver "rtl8192se_linux_2.6.0015.0127.2010" is the latest.

Do not unpack the archive to the desktop as this causes problems with  compiling the driver, unpack it to something like "~/Drivers" then run  the following:

cd rtl8192se_linux_2.6.0015.0127.2010
sudo make
sudo make install

You can also remove the driver with "make uninstall" from the same  directory should you need to.

You will need to re-make the driver every time you install a new kernel  (bit of a pain) but wireless works very well with this driver.

Cheers.

---

### Post by emoguitarist06 on 2010-05-04
> **hsoulen said:**
> Hi,

I have an Asus 1201n as well.

Couple of quick questions...

You said you followed the instructions on the bug report at launchpad, which instructions did you follow? Did you install the Realtek driver from the Realtek support site or did you go with Ndiswrapper?

Here is what worked for me:

If you have installed a driver older than the one below, please "sudo make uninstall" from the folder you unpacked the driver into and reboot before proceeding.

My best advice for Karmic (9.10) is check the Realtek site for the most  recent driver "rtl8192se_linux_2.6.0015.0127.2010" is the latest.

Do not unpack the archive to the desktop as this causes problems with  compiling the driver, unpack it to something like "~/Drivers" then run  the following:

cd rtl8192se_linux_2.6.0015.0127.2010
sudo make
sudo make install

You can also remove the driver with "make uninstall" from the same  directory should you need to.

You will need to re-make the driver every time you install a new kernel  (bit of a pain) but wireless works very well with this driver.

Cheers.

I SECOND THIS ANSWER
as the official realtek driver works perfect
download here:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)
choose RTL8191SE-VA2

---

