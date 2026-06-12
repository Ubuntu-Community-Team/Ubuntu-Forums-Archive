---
title: "Wireless Network Connections"
date: 2010-02-01
forum: Hardware
---

### Post by deril on 2010-02-01
Hi all,

I have just started using ubuntu and I am still noob/green with it :(...

(I will hopefully get better eventually.)

Anyways, can someone help me connect to a wireless network?

I have ubuntu installed on a notebook, hp pavilion dv5 1150, do I require any drivers? I couldn't find any official drivers on the HP website.
Maybe unofficial ones will do?


Thanks,
Deril

---

### Post by chaanakya_chiraag on 2010-02-01
Well, that depends...is there an applet with a wireless symbol in the top-right-hand corner?  It should be called Network Manager.  If you click on it, it will show you the available wireless/wired networks.  If you don't see anything in that list, then your hardware is not being detected and you need additional drivers.

---

### Post by deril on 2010-02-01
I don't seem to have the applet.
Although I do have a way to manually configure a wireless network, this involves alot of settings, which I can easilly get one of them incorrect, and makes it virually impossible for me to check weather it is because I am inputting incorrect data, or weather it is not connecting because hardware issues. :-s

---

### Post by chaanakya_chiraag on 2010-02-01
So there is no applet with a wireless bars symbol and a big "X" through it to say "you don't have network connectivity!!!!!!!"?

---

### Post by chaanakya_chiraag on 2010-02-01
Okay...go to a terminal (Applications->Accessories->Terminal) and type in ```
sudo ifconfig
``` and paste the output.

---

### Post by deril on 2010-02-01
This is what I have...

Image in attachment.

If cannot view, visit: [http://i46.tinypic.com/2s0lgm0.png](http://i46.tinypic.com/2s0lgm0.png)

---

### Post by chaanakya_chiraag on 2010-02-01
Could you please pos tthe output of the command I posted above?  Thanks!

---

### Post by deril on 2010-02-01
> eth0      Link encap:Ethernet  HWaddr 00:23:8b:7f:8a:e6  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe7f:8ae6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31949918 (31.9 MB)  TX bytes:3960198 (3.9 MB)
          Interrupt:32 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

That is the output.

But I am currently connected to the Network using an Internet Cable. (Hopefully temporarily)

---

### Post by chaanakya_chiraag on 2010-02-01
I think it's detecting your hardware.  Have you tried looking at the man  pages for ifup and ifdown (If I were at my Ubuntu box right now, I'd  tell you the command, but I don't remember it offhand)??

---

### Post by deril on 2010-02-01
i have solved the problem

just downloaded all the latest hardware drivers, using the system > administration > hardware drivers


thanks anyways
deril

---

### Post by chaanakya_chiraag on 2010-02-01
You're welcome!  If this problem has been fixed, please mark the thread as solved by going to Thread Tools->Mark as Solved.  Thanks! :)

---

