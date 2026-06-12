---
title: "Serious video card issues."
date: 2009-05-06
forum: Hardware
---

### Post by amplifier.worship on 2009-05-06
Greetings.
I recently had a rather serious hardware issue and I'm wondering if it could be linked to Linux somehow. I've been using Ubuntu for a month or two and it performed rather well. After 9.04 came out I decided to make a fresh install because I wanted to reorganize my disk partitions. I also wanted to try KDE out so I installed Kubuntu on my system. After a few days of usage my video card suddenly died on me. This is pretty much what it displays if it's plugged in:
[http://i40.tinypic.com/2psn1gh.gif](http://i40.tinypic.com/2psn1gh.gif)
The card is Geforce 8500GT with passive cooling. It wasn't overclocked or physically damaged anyhow by the way. I wasn't doing anything fancy with the card (no 3D stuff or gaming) and I was running KDE with its basic settings. I see this jitter all the time now, even when the PC is booting up. I tried changing the thermal grease but it didn't help. I'm using my old card now and it works fine.
Now this could have been just a hardware fault but I'm worried if it wasn't provoked by faulty Linux drivers or something. I've been using the restricted nVidia drivers and they seemed to do their job just fine (at least on Gnome they did). Right now I'm considering buying a new video card. I'm thinking of something like 9600GT with passive cooling (I kinda prefer passive cooling because it's both silent and Linux doesn't seem to have a good fan speed control (at least the fan on  my ATI card is always running at full speed under Linux)) but I'm rather afraid if something like that would happen again. So basically, what I'm asking is could this fault have been caused by the Linux drivers?

---

### Post by amplifier.worship on 2009-05-06
Anyone? :confused:

---

### Post by Stavro on 2009-05-06
Looks like your card received a static charge somehow. Does it share RAM with the system? I would say that this is just an unfortunate coincidence, hardware such as a graphics card can&#8217;t really be physically damaged by a bad driver. Do you think you could have had a surge?

---

### Post by brendan.lefoll on 2009-05-06
> **amplifier.worship said:**
> Greetings.
I recently had a rather serious hardware issue and I'm wondering if it could be linked to Linux somehow. I've been using Ubuntu for a month or two and it performed rather well. After 9.04 came out I decided to make a fresh install because I wanted to reorganize my disk partitions. I also wanted to try KDE out so I installed Kubuntu on my system. After a few days of usage my video card suddenly died on me. This is pretty much what it displays if it's plugged in:
[http://i40.tinypic.com/2psn1gh.gif](http://i40.tinypic.com/2psn1gh.gif)
The card is Geforce 8500GT with passive cooling. It wasn't overclocked or physically damaged anyhow by the way. I wasn't doing anything fancy with the card (no 3D stuff or gaming) and I was running KDE with its basic settings. I see this jitter all the time now, even when the PC is booting up. I tried changing the thermal grease but it didn't help. I'm using my old card now and it works fine.
Now this could have been just a hardware fault but I'm worried if it wasn't provoked by faulty Linux drivers or something. I've been using the restricted nVidia drivers and they seemed to do their job just fine (at least on Gnome they did). Right now I'm considering buying a new video card. I'm thinking of something like 9600GT with passive cooling (I kinda prefer passive cooling because it's both silent and Linux doesn't seem to have a good fan speed control (at least the fan on  my ATI card is always running at full speed under Linux)) but I'm rather afraid if something like that would happen again. So basically, what I'm asking is could this fault have been caused by the Linux drivers?

[http://www.semiconductor.net/article/CA6575415.html](http://www.semiconductor.net/article/CA6575415.html)

I'll let you decide if rumours are true that this only is the case for notebook GPUs.

Theories seem to say that because of higher temps in laptops, failures where first noticed en mass there, but will spread since the die problem is on virtually all G8x cards.

---

