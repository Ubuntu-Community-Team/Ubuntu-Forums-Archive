---
title: "Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)"
date: 2009-12-30
forum: Hardware
---

### Post by TheGuyWhoGotOn on 2009-12-30
I cannot get this wireless card working, it's never been this hard and I've installed them on like 5 other painful laptops.

lspci:

```
0c:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```

ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:25:64:53:fe:9b  
          inet addr:192.168.2.15  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe53:fe9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1408634 (1.4 MB)  TX bytes:267621 (267.6 KB)
          Interrupt:30 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

I've installed MadWifi, tried enabling ath9k, ath5k, installed the Windows Wireless Drivers. After the Windows Wireless Drivers "Enable Wireless" (Though it still wouldn't allow me to check off the box) isn't even shown anymore.

All I want is wireless internet to work. Could somebody please help me?


I'm on Karmic Koala (9.10).

---

### Post by dummy910 on 2009-12-30
Have you tried installing the "backports" package?

**How To**
1- Add Repository in a Terminal:
```
gksudo gedit /etc/apt/sources.list
```
2- then add the following line to the bottom of the file:
> ## added manually to add repo for backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-backports main universe multiverse restricted
3- then:
```
sudo apt-get update
```
4- then:
```
sudo apt-get install karmic-backports
```
5- then:
[color=red]reboot[/color] and you should have wireless!

---

### Post by TheGuyWhoGotOn on 2009-12-30
I get the error "E: Couldn't find package karmic-backports" after adding in the source and going "sudo apt-get install karmic-backports". Are you sure that's the package?

Thanks for helping :).

---

### Post by TheGuyWhoGotOn on 2009-12-30
Bump :) Feels like I'm close could someone please finish helping? :)

---

### Post by TheGuyWhoGotOn on 2009-12-31
Bump 2


Edit: Followed all the steps here: [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072). Still nothing...

---

### Post by TheGuyWhoGotOn on 2010-01-02
Bump 3

---

### Post by dummy910 on 2010-01-02
I stand corrected, as I typed my original reply here out of memory, so here's the proper code, after adding the repos etc listed above, in a terminal:
```
sudo apt-get install linux-backports-modules-karmic

```

---

### Post by TheGuyWhoGotOn on 2010-01-04
Thanks for the help again! :) But ifconfig still shows no wlan0 :(.

---

### Post by TheGuyWhoGotOn on 2010-01-05
:'( Bump

---

### Post by Mooki on 2010-02-28
Ubuntu newb here.

I don't mean to hijack this thread but just though I would say that dummy910's advice helped me get my card working. I installed Karmic 9.10 on an Asus N81Vg-X2A laptop that had this same Atheros card in it. My problem wasn't that it wasn't recognized but that the current out of the box driver was providing a terrible wifi connection.  I added the suggested repo and installed the backports and I just did the following that was suggested by dummy910 and now my wireless connection is strong as it should be (like it was in Windows 7 prof x64bit). This helped get my wireless card working with the signal without trying to use ndiswrapper and try to use the current windows driver I had.  Thanks again and I hope yours begins to work TheGuyWhoGotOn.

Also, just a question on the backports repo and installation.  Do you leave this source installed and in the /etc/apt/sources.list and update it every time or do you remove it once the backports or whatever have been installed. I was reading the documentation for it but didn't quite understand everything. I guess I'll keep reading. Thanks for your help!

---

### Post by profslughorn on 2010-03-01
try what this guy did and see if it helps. i googled "ar9285 ubuntu karmic" and turned up lots of stuff. 

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1286503](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1286503)

thanks to the above poster that mentioned the "backports" solution. it's improved my wireless situation a bit. i used to get 40% (2 bars) signal in a room next to the router and now it's at 80% (4 bars).

what is that "backports" thing anyway? noob question i know.

---

### Post by Mooki on 2010-03-01
> **profslughorn said:**
> try what this guy did and see if it helps. i googled "ar9285 ubuntu karmic" and turned up lots of stuff. 

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1286503](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1286503)

thanks to the above poster that mentioned the "backports" solution. it's improved my wireless situation a bit. i used to get 40% (2 bars) signal in a room next to the router and now it's at 80% (4 bars).

what is that "backports" thing anyway? noob question i know.

I can't remember how I came across this, but maybe it will help.  I read over it a little bit.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

