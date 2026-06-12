---
title: "dell 6000 intel pro 2200 wireless b/g card not detected"
date: 2006-03-13
forum: Hardware &amp; Laptops
---

### Post by solarwind on 2006-03-13
Hello everyone, 

I have a newly purchased dell 6000 laptop with the intel 2200 built in wireless network card. I have successfully installed Ubuntu 5.10 without problems but only one thing bugs me. Windows has successfully dectected my wireless card and I am able to use it and configure it perfectly. As for linux, I have tried Mandriva Linux, Suse Linux and finally Ubuntu Linux, but all distributions have  not recognised my internal wireless card.

Here is my output for lspci:

root@ubuntu:/home/vg# lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5460
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
0000:03:01.2 0805: Ricoh Co Ltd: Unknown device 0822 (rev 17)
0000:03:03.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
root@ubuntu:/home/vg#



It has dected my internal lan card but not my wireless card. The problem could be that the internal wireless card is not currently turned on. If so, there is a key on the keyboard which will turn it on : fn+F2. But that only worked in Windoze and not in Linux. The wifi status light only turns on and off in windoze when i press fn+F2. Not in linux.


Here is what iwconfig returned:root@ubuntu:/home/vg# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

root@ubuntu:/home/vg#

And here is what ifconfig returned:
root@ubuntu:/home/vg# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:ED:CA:AA
          inet addr:xxxxxxxxxxx  Bcast:xxxxxxxxx  Mask:xxxxxxxxx
          inet6 addr: fe80::214:22ff:feed:caaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:81453168 (77.6 MiB)  TX bytes:2672378 (2.5 MiB)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:645266 (630.1 KiB)  TX bytes:645266 (630.1 KiB)

root@ubuntu:/home/vg#

(I have blocked out the numbers with xxxxx)


It is not decting wlan0 or eth1. Why is this?

I am prepared to use ndiswrapper at will. But I first have to get the card recognized by Linux right?

Thanks for any help!

---

### Post by solarwind on 2006-03-13
Can someone help me please? I really need my wireless networking. I don't think that the internal wifi card is even on when linux starts. Any ideas? The volume controls on the front are working well, but I can't use the Fn keys to turn on the wireless.

All help is much appreciated. Thankyou.

---

### Post by Teroedni on 2006-03-13
You could try a Dapper install
Dapper is developing and is not a finnished product, still i find it pretty stable.

The reason Dapper may be good is that it contains newer modules, which may mean your card is supported.

---

### Post by solarwind on 2006-03-13
Hello, thankyou for your response. I have read other forums with problems similar to mine. I have found out that every one else's distrobution has detected the card but no driver is found. But in my case, the card is not even detected.

---

### Post by Teroedni on 2006-03-13
0000:03:03.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)

Thats the reason i think Dapper would be better for you.
Since Dapper may detect your card  , and  hopefully got support for your card:D

---

### Post by jml on 2006-03-13
If you are not interested in running Dapper Drake, you might want to try the latest Mepis release.  Current version is 3.4-3.  I don't like it as well as Ubuntu, but it may have more current drivers.  It was able to detect the Broadcom based wireless card in my HP notebook, when none of the other distros would.

---

