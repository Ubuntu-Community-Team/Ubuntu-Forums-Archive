---
title: "no internet on the laptop"
date: 2008-09-08
forum: General Help
---

### Post by soundf on 2008-09-08
I've got new Acer notebook laptop and I installed Ubuntu from Windows.
I have Ubuntu on my other computer and I didn't even had to setup anything about internet, it just worked, so why there's no internet in this laptop?

Thanks.

---

### Post by jonface on 2008-09-08
Start a terminal, Applications --> Accessories --> Terminal.

Type: ifconfig <enter>

Copy/paste the output here. 

Ta.

---

### Post by soundf on 2008-09-08
Im on the new laptop right now, via wired network... :\
Why can't it connect via WiFi?

Here's the output for ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1e:68:6d:28:eb  
          inet addr:192.168.2.107  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe6d:28eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:609269 (594.9 KB)  TX bytes:83790 (81.8 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1662 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88076 (86.0 KB)  TX bytes:88076 (86.0 KB)

---

### Post by jonface on 2008-09-08
It doesn't seem to have loaded the module needed for your wireless, the same way (I guess) Windows needs a driver for hardware.

You haven't got a hardware switch on your laptop which disables the wireless? ...which you might have disabled by accident?

What's the full make/model of your laptop?
Can you also post the output from 'lsusb' and 'lspci'. 

Ta.

---

### Post by soundf on 2008-09-08
thanks all but i just forget to update.. everything's fine now

---

