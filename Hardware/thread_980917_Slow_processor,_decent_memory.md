---
title: "Slow processor, decent memory?"
date: 2008-11-13
forum: Hardware
---

### Post by Flakey on 2008-11-13
Howdy!

I recently installed Ubuntu 8.10 on a system with a 500Mhz Celeron processor.  The system has 512Mb of RAM, and a video card with 128Mb of RAM.  I performed a standard install using the standard installer CD.  I noticed the machine was lagging, so I turned off visual effects.  Helped somewhat, but I'm still experiencing lag.  I checked the system monitor and the processor usage consistently averages 90% or better!

I'm looking for suggestions on what I can do or which flavor I should install (should I need to reinstall).  Most of the information I've run across has suggestions for machines with limited memory.  I think this machine has plenty of RAM to run comfortably, but the processor is clearly the bottleneck.

Thanks in advance for any advice!

C

---

### Post by OrangeCrate on 2008-11-13
I have a 1.4 GHz Celeron (PIII family), with integrated video, and 512 meg of RAM. It's not exactly the same setup as yours, but similar.

I have been running Ubuntu, and it runs decently, but I recently decided to install Xubuntu 8.10, and the difference in speed is very noticeable over Ubuntu 8.10. If you like Ubuntu, that might be something to try.

---

### Post by Flakey on 2008-11-13
Thanks for the reply!

After reading these forums a little more this morning, can anyone tell me how much I would reduce the load on the processor by using Fluxbox as the window manager for my existing 8.10 Ubuntu install?  Am I pretty much forced to reinstall using Xubuntu?

Thanks!

C

---

### Post by Mardoct909 on 2008-11-13
500 Mhz? really?

If at all possible, I'd recommend a CPU upgrade. A dual-core Celeron with 1.6Ghz is about 70$ CAN if you go to a good store. You could upgrade it yourself, or - less risky - have someone else do it. You could probably get it upgraded for no more than 120$ CAN.

If that isn't possible, there is a guide [here](http://www.howtogeek.com/howto/ubuntu/installing-fluxbox-on-ubuntu-linux/) on installing Fluxbox, which will no doubt improve performance.

You could also try migrating to Damn Small Linux, but I don't know if there is decent support over there.

---

### Post by m_l17 on 2008-11-13
Backup your files and or /home dir. Do a fresh install of Xubuntu.

---

### Post by joe.turion64x2 on 2008-11-13
By reducing running services you would free CPU power, granted not the best solution, but it might help in a rush.

Thanks.
Joe.

---

### Post by HotCupOfJava on 2008-11-13
I'm running Xubuntu 8.04 on an old 500MHz Celeron w/ only 256Mb. Works quite well. I'd recommend it in your situation.

---

### Post by tgalati4 on 2008-11-13
Linux Mint Darnya XFCE should run well on that hardware.  I have a Dell GX1 with similar specs and it runs acceptably well.

---

### Post by RedSquirrel on 2008-11-15
For Ubuntu on those specs, I would go with a minimal installation:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

and add a light window manager such as Openbox, Fluxbox, or, if you want a full desktop environment, **xfce4**.

```
sudo apt-get install xfce4
```

---

