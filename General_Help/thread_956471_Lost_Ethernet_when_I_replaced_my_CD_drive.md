---
title: "Lost Ethernet when I replaced my CD drive"
date: 2008-10-23
forum: General Help
---

### Post by Mr Sumatra on 2008-10-23
I am using Ubuntu 8.04 and recently replaced my CD drive with a new LG GH22.  After having issues with a PCI bus error, I had to reinstall.  

Now I can't see my ethernet card, which IIRC, was never a worry.  So I can't get online.  

What can I do?  In the terminal I got this:
                               ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57296 (55.9 KB)  TX bytes:57296 (55.9 KB)

Manual configuration of the network only shows the Point to point connection and nothing can be done to that anyways.

I have always had easy, painless experiences with Ubuntu, until now.  Please help.  I am not a total noob, but I do not use the terminal too much.

---

### Post by cmnorton on 2008-10-23
This sounds like an interrupt conflict.

Start by looking at the output from: cat /proc/interrupts

---

