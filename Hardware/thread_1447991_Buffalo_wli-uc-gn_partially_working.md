---
title: "Buffalo wli-uc-gn partially working"
date: 2010-04-06
forum: Hardware
---

### Post by rshakin on 2010-04-06
Hello people, 

I have a small problem, I finally got a this w-lan card working, as far as hardware goes, as per instructions in this thread, but for some reason I cannot use it to connect to a WPA/2 enabled access point. It will connect fine to an unsecured access point, any ideas ? 


Bus 001 Device 006: ID 18e3:7102 Fitipower Integrated Technology Inc 
Bus 001 Device 005: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 001 Device 004: ID 0411:015d MelCo., Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:0112 Chicony Electronics Co., Ltd KU-8933 Keyboard with PS/2 Mouse port
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


wlan0     Link encap:Ethernet  HWaddr 00:24:a5:50:18:f5  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:a5ff:fe50:18f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4037 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1816600 (1.8 MB)  TX bytes:198340 (198.3 KB)

[    9.549721] rtusb init --->
[    9.551129] usbcore: registered new interface driver rt2870
rshakin@newline:~$ dmesg | grep rtusb
[    9.549721] rtusb init --->
rshakin@newline:~$ dmesg | grep rt2870
[    9.543738] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[    9.551129] usbcore: registered new interface driver rt2870

---

