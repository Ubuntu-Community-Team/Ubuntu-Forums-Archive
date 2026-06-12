---
title: "Bluetooth on dell studio 17 does not work"
date: 2010-09-25
forum: Hardware
---

### Post by GreenFuze on 2010-09-25
Hey

I installed Ubuntu on my new awesome laptop.
I got everything up and running but I am really stuck with the bluetooth device.

I can see the bluetooth icon, and when I get into "preferences" it says that "bluetooth is diables".
I click on the BIG BUTTTON "Turn On Bluetooth" and the button become disabled, and... thats it. nothing else happen even after 20 minutes.

here is my ifconfig output:

```

eth0      Link encap:Ethernet  HWaddr 00:26:b9:d2:5f:89  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:36 

eth1      Link encap:Ethernet  HWaddr 78:e4:00:bf:b4:9e  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7ae4:ff:febf:b49e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:76956 errors:0 dropped:0 overruns:0 frame:95331
          TX packets:55894 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:107648552 (107.6 MB)  TX bytes:5636133 (5.6 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1936 (1.9 KB)  TX bytes:1936 (1.9 KB)

```

Help anyone??? :confused:

---

### Post by GreenFuze on 2010-10-04
For the sake of future generation, here is what happened.

I have dual-boot with windows 7, now, I noticed that when I disable my bluetooth in windows, I cannot enable it in ubuntu.

So if I want to use bluetooth in ubuntu, I have to enable it in windows first, and than boot to ubuntu.

---

### Post by v1nsai on 2011-01-03
Thanks for taking the time to post your solution, looks like that was the same thing that was happening to me, I just spent 20 minutes loading and reloading the bluetooth module, grep'ing around /etc/init.d to make sure I hadn't changed anything myself >.<

Windows can affect a lot of low-level stuff like that, I had a similar problem with a friend's laptop trying to enable the Quick-whatever its called BIOS which was really neat and let you check email, chat and browse the web from a BIOS program (linux based of course :-D ).  I enabled the option in BIOS and rebooted 100 times but it wasn't until I installed a special program and enabled it in Windows that I got it to work.

If all else fails, enable it in Windows!

---

