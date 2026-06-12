---
title: "Internet connects but doesn't work"
date: 2012-04-28
forum: Hardware
---

### Post by Kelan76 on 2012-04-28
I recently upgraded to 12.04 on my Dell xps m1330. Before the upgrade everything was working fine. Now that I upgraded my internet states that it connected and is staying connected but web pages won't load nor can I update anything etc.  I even did I fresh install of 12.04 to see if that may fix it. Same issue. I do not know where to go from here. Also a wired connection does the same thing. In both instances I can rarely get a web page to load. Usually not long after it connects. Then nothing. I'm not sure how ill be able to post any logs either since my only internet access now is my phone. As much as I love ubuntu this is a real pain. I work on my pc for my job. Without it I cant get paid. Please help.

---

### Post by Kelan76 on 2012-04-28
I was able to figure out a way to at least browse the web but updates and addition drivers wont work still.  i changed my ipv4 settings to an open DNS but i dont want to keep it that way and would like to be able to run updates and such.  but i am now able to post logs anyway...

---

### Post by Kelan76 on 2012-05-04
Updgraded my desktop and now back to square one on both systems. Both connect but cannot do anything. Can anybody help me out here?? And btw the desktop is not wireless.

---

### Post by Kelan76 on 2012-05-05
No one knows anything about this? It's not my internet or isp. Something could be causing my computers to not communicate with my router?

---

### Post by ahallubuntu on 2012-05-05
Your post is miscategorized - it should be in "Networking and Wireless" where you'll likely get better response:

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

But:

What is your desktop physically connected TO?  A router?  A modem?  What?

In a terminal window type

```
ifconfig
```

What do you get?

---

### Post by Kelan76 on 2012-05-05
eth0      Link encap:Ethernet  HWaddr 00:1f:bc:07:ce:17  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:bcff:fe07:ce17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:96597 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:119687888 (119.6 MB)  TX bytes:8088466 (8.0 MB)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8035 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:754257 (754.2 KB)  TX bytes:754257 (754.2 KB)


my desktop is connected to a gateway (modem routher in one)

---

### Post by Kelan76 on 2012-05-05
i am also only by chance able to respond on here every now and then.  web pages will load here and there rarely then stop.

---

