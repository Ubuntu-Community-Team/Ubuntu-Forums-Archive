---
title: "on wireless: i did my homework"
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by fcendejas on 2007-04-09
Fresh install of Feisty beta on a Dell Inspiron 700m.  I'm trying to connect to a completely unprotected wireless network.
I did my homework before posting and read many similar threads, but couldn't come to a solution.  I did run these terminal commands, and have posted the results.


iwconfig:```

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


iwlist eth1 scan:
```
eth1      No scan results
```


*which is probably because...*
lshw -class network```

  *-**network:0 DISABLED    **
       description: Wireless interface
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth1
       version: 03
       serial: 00:11:f5:08:05:fe
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-14-generic latency=32 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:e0204000-e0205fff irq:10
```


How does eth1 become ENABLED?  On the Network administrator, my wireless connection is on roaming (not "not configured"), and going to "create new wireless network" or "connect to other wireless network" on the top panel and typing in my network name doesn't work.  

Advice is much appreciated.

---

### Post by josephus on 2007-04-09
To enable eth1 either go to System->Administration->Networking and make sure eth1 is checked off.

From the command line you can use
```
sudo ifdown eth1
sudo ifup eth1
```

to turn on and off network interfaces.

---

### Post by fcendejas on 2007-04-09
Through the Network Manager this does not work.  It shows that Roaming is enabled, and there is a horizontal line through the checkbox.  Using the two given commands results in 

sudo ifdown eth1
```
ifdown: interface eth1 not configured 

```

and sudo ifup eth1
```
Ignoring unknown interface eth1=eth1.

```

Alternatively, if I set the wireless connection through the Network Administrator to the correct Essid and on dhcp and check it off, it still doesn't connect, and i get the following:
sudo ifdown eth1
```
ifdown: interface eth1 not configured

```

sudo ifup eth1: a long series of "send_packet: Network is down" and "DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7"

---

### Post by josephus on 2007-04-09
hmm...  weird

can you type dmesg and see if there are any error messages.

if you can post anything related to it that would be helpful

to limit the output to lines with key phrases try:
```

dmesg | grep eth
dmesg | grep bcm
dmesg | grep BCM
```

---

### Post by fcendejas on 2007-04-09
I'm really stumped: 
dmesg  | grep bcm gives tons of errors, with pagefuls of the following:
```
[ 2502.056000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2625.240000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2748.424000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2871.608000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2994.792000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

```

dmesg | grep eth1, where eth1 is the alias for the wireless, comes up blank, because there are no references to eth1 throughout the whole dmesg output.

I should be able to connect to a network regardless of whether I'm on roaming mode or not, right?  In either case, nothing can tell me that eth1, my wireless, is working, even though I can configure it in the Network Settings.

---

### Post by josephus on 2007-04-09
looks the trouble is that your card is not properly supported out of the box.  this wiki explains how to get your card working

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

basically there are two ways.  you can use ndiswrapper which basically wraps the windows driver in a way that linux can use them.  or you can use firmware cutter, which i don't quite understand.  the second method seems more difficult to me, but i don't know which one has a higher success rate.

let me know which one you decide and i can try to help you along.

---

### Post by fcendejas on 2007-04-10
The firmware cutter did the job, thanks much.  The solution, however, makes me think that I was lucky for having a card that was internally supported, and which just needed firmware - the process seems much more difficult with ndiswraper.

Thanks again!

---

### Post by josephus on 2007-04-10
glad to help.

---

