---
title: "Wifi on HP Laptop"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by qzplx on 2007-05-16
Hi all,

Introduce my name is Raffaell, im new user in Ubuntu,
Im facing problem with Feitsy wifi on my laptop...

My laptop is HP V3000 Series
-Turion 64 X2
-Broadcom Wifi

My Wificard detected as Dell Wifi Card with Broadcom Chipset but i cannot connect to any AP, when i Checked in console, the Ndiswrapper its not there....

Is there anyone can help me, how to configure the driver, i think the problem is the driver not setup correctly, since i cannot use Internet Access, ihave to configure the Ndiswrapper manually....without apt get

Thanks is advance......

---

### Post by Kobalt on 2007-05-16
Can you please give us the exact model of your wifi card, using this command line : ```
sudo lshw -C network
```

---

### Post by qzplx on 2007-05-17
Nope, its nothing happening.....
Should i reinstall the ubuntu ?

here my iwconfig
sudo lshw -C network

Dell Wireless 1390 WLAN Mini-PCI Card


raffaell@raffaell-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"R"  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Kobalt on 2007-05-17
Nope you shouldn't reinstall Ubuntu. The command line was meant just to know what type of card you have. 
Here is how to get your wifi working : [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

