---
title: "Shuting Down Problem"
date: 2008-11-02
forum: General Help
---

### Post by t4ggs on 2008-11-02
Hi, I just made a fresh install of intrepid and when I shut down my computer, after the ubuntu logo with the orange stripe, the screen turns black and there is a "_" blinking and thats all...any message or anything....and i can wait hours and still the same thing..

any idea?

---

### Post by tvtech on 2008-11-02
have you taken a look at your log files, my guess it's either hanging on networking or xorg crap    that's what always hangs me up, either that or my propriatary drivers for graphics cards as well, but that should give you a place to start looking at least.

---

### Post by t4ggs on 2008-11-02
Well thats how it looks like...sorry i dont know much..

---

### Post by Idefix82 on 2008-11-02
Hmm, I don't know much myself but it looks like the computer is switching the network on and off and on and off... What if you try to kill your network driver by hand before shutting down:
```
sudo modprobe -r r8169
```
and then shutdown?
If that works then we can turn that into a permanent solution.

---

### Post by t4ggs on 2008-11-02
didn't worked...

---

### Post by IT-Joker on 2008-11-02
I had the same problem, you can try workaround mentioned in this thread:
[http://ubuntuforums.org/showthread.php?t=965464](http://ubuntuforums.org/showthread.php?t=965464)

That worked for me. 
As for what I've read, the system WILL shut down/restart at the end, it just takes very long time. 
The problem is something between alsa-utils and network manager... the thing is that network interfaces must be shut down before alsa utils.

You have to edit this file: /etc/init.d/alsa-utils (as root)
Find this line:
stop)
and after this one, insert a new line:
ifconfig *eth0* down

...if your network interface is something else than eth0, replace *eth0* with your network interface id (in my case it was eth1).
If you have multiple network interfaces, repeat the line for each of them.

You can use the network tools in the System menu (don't know the exact name, I don't have english version of Ubuntu) or the ifconfig console command to find out which network interfaces you have. Ignore the "lo" (loopback) one

---

### Post by t4ggs on 2008-11-02
> **IT-Joker said:**
> I had the same problem, you can try workaround mentioned in this thread:
[http://ubuntuforums.org/showthread.php?t=965464](http://ubuntuforums.org/showthread.php?t=965464)

That worked for me. 
As for what I've read, the system WILL shut down/restart at the end, it just takes very long time. 
The problem is something between alsa-utils and network manager... the thing is that network interfaces must be shut down before alsa utils.

You have to edit this file: /etc/init.d/alsa-utils (as root)
Find this line:
stop)
and after this one, insert a new line:
ifconfig *eth0* down

...if your network interface is something else than eth0, replace *eth0* with your network interface id (in my case it was eth1).
If you have multiple network interfaces, repeat the line for each of them.

You can use the network tools in the System menu (don't know the exact name, I don't have english version of Ubuntu) or the ifconfig console command to find out which network interfaces you have. Ignore the "lo" (loopback) one


Did everything you said and still didn't worked...

---

