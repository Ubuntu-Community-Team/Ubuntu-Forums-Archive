---
title: "Firmware Missing-NO LAN-TRIED EVERYTHING"
date: 2012-03-11
forum: Hardware
---

### Post by rtaube on 2012-03-11
Ok,

I am about 5 hours into this project. I KNOW I need the drivers to get the wireless working on my computer. I am aware that hooking up an ethrenet cord can allow me to download them easily. Problem is, when I plug in my LAN cable, the computer detects the cord but says the internet is currently disconnected. I've tried all the different forums (including the how to set up the wireless without a connection--which failed) to try and solve this. PLEASE HELP!

---

### Post by winh8r on 2012-03-11
Is there a small icon with two arrows on it at the top of your screen?

if so, click on it and select "enable networking"


or

connect the ethernet cable and then insert the Ubuntu live cd and restart the machine, connection should be automatic for live cd.

---

### Post by rtaube on 2012-03-11
There are not arrows...

Can you walk me through how to do this with the LAN line. I used my external hard-drive to run the install...not a CD

---

### Post by winh8r on 2012-03-11
ok which version of ubuntu are you using , 11.10?

---

### Post by rtaube on 2012-03-11
yeah

---

### Post by winh8r on 2012-03-11
Make sure the ethernet cable is connected, and the router/modem is on then 

open a terminal and enter:

```
ifconfig
```

and post the result in your next post

(use the # code tags in the reply box)

---

### Post by rtaube on 2012-03-11
i am a total noob...not sure how to do the code thing, here is a try

#code
 :~$ ifconfig
  eth0      Link encap:Ethernet  HWaddr 00:c0:9f:a8:20:87  
            inet6 addr: fe80::2c0:9fff:fea8:2087/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:3518 errors:0 dropped:0 overruns:0 frame:0
            TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:216796 (216.7 KB)  TX bytes:18179 (18.1 KB)
            Interrupt:18 Base address:0xa000
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:688 errors:0 dropped:0 overruns:0 frame:0
            TX packets:688 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:54704 (54.7 KB)  TX bytes:54704 (54.7 KB)

---

### Post by winh8r on 2012-03-11
looks like that interface is up and running , 

try entering into the terminal:

```
ping -c 4 www.google.com
```



( to use the code tags, copy and paste the text into the reply box, then highlight the text you want to appear in the code box and click on the # symbol at the top of the box)

---

### Post by rtaube on 2012-03-11
before I do that, I have tried opening up firefox and it says there is no website. It also brings up a a box in the upper left corener saying wired connection is not connected: you are not connected to the internet

---

### Post by winh8r on 2012-03-11
Click on the "file " tab in firefox and make sure that "work offline" is not checked.

---

### Post by rtaube on 2012-03-11
not in offline movement. 

output from the ping: unknown host [www.google.com](www.google.com)

---

### Post by winh8r on 2012-03-11
enter this in terminal:


```
sudo /etc/init.d/networking restart
```

and report what happens

---

