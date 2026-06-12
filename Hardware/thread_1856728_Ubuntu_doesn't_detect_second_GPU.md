---
title: "Ubuntu doesn't detect second GPU"
date: 2011-10-08
forum: Hardware
---

### Post by TacticalApe on 2011-10-08
My laptop (HP Pavilion dv7-4270us) has 2 graphics cards, one power saving on and a high performance one. Ubuntu can only use the power-svaer one, and I everything is extremely slow. I looked in the the catalyst menu, and it showed the name of the power-saver one, but it says "[Unknown Display] Unknown Adapter" The other card is a ATI Mobility Radeon HD 4200 Series. I know nothing about graphics cars/processors/whatever, so if you can help me fix this, that would be awesome. 



EDIT: Well, I went to their site, downloaded something to update the  drivers, rebooted, and ubuntu won't boot right. It just keeps displaying  some text that says things were loaded [OK] after it.
In other words, I can't use my laptop right now. Is there a way to reinstall the drivers off of the ubuntu disk?


Also, here's a screenshot of what it says:
[IMG]http://i.imgur.com/2GKye.png[/IMG]
[IMG]http://i.imgur.com/235dU.png[/IMG]

---

### Post by wolfen69 on 2011-10-08
Did you install the ATI drivers? You can install them from *Hardware Drivers*.

---

### Post by Redblade20XX on 2011-10-08
Can you post your buntu version and kernel version, please?  :)

- Red

---

### Post by TacticalApe on 2011-10-08
Ubuntu 11.04
Kernel Version 2.6.38 (I think ,and I can't check either)

> **wolfen69 said:**
> Did you install the ATI drivers? You can install them from *Hardware Drivers*.
I can't even get into the GUI anymore.

---

### Post by Jagoly on 2011-10-09
not even through recovery mode?

even from a gui-less recovery mode, you can still install ati drivers (sudo apt-get install fglrx, you may need to type "init 3" then log in first)

however, you have the catalyst control center installed, which has fglrx as a dependency (means already installed)

if you can, from a gui or non gui (if non gui will need to do "init 3" and log in first, run ```
sudo apt-get purge fglrx
sudo apt-get autoremove
sudo apt-get install radeon --reinstall
```

then try booting graphically. It won't be fully accelerated, but it will work enough to figure out why fglrx was misbehaving.

---

### Post by TacticalApe on 2011-10-09
> **Jagoly said:**
> not even through recovery mode?

even from a gui-less recovery mode, you can still install ati drivers (sudo apt-get install fglrx, you may need to type "init 3" then log in first)

however, you have the catalyst control center installed, which has fglrx as a dependency (means already installed)

if you can, from a gui or non gui (if non gui will need to do "init 3" and log in first, run ```
sudo apt-get purge fglrx
sudo apt-get autoremove
sudo apt-get install radeon --reinstall
```then try booting graphically. It won't be fully accelerated, but it will work enough to figure out why fglrx was misbehaving.
No, i can't even get into recovery mode. It skips GRUB, tries to boot into Ubuntu, then gets to some black screen with text that lists a bunch of different things, and with [OK] across from them. I've never seen that. 
Would it work if I used the LiveCD to ru n those commands?


Also, what do I do once I can get into the GUI? Because you said it won't be fully accelerated...

EDIT: I tried the LiveCD... That won't work either. It just goes black and shows the cursor, and doesn't do anything.

---

### Post by Jagoly on 2011-10-09
Wait, so you can't boot the live cd? That's not good...
If it was skipping grub, then that means it has nothing to do with graphics drivers.

I smell a hardware problem.

---

### Post by TacticalApe on 2011-10-10
> **Jagoly said:**
> Wait, so you can't boot the live cd? That's not good...
If it was skipping grub, then that means it has nothing to do with graphics drivers.

I smell a hardware problem.

It didn't do that until I messed with the drivers, and I had just gotten the harddrive replaced because that was corrupted. 

After hours of trying to figure this out, I decided to reinstall ubuntu (I didn't have much stuff on there, so I didn't lose anything) and I'm back to square one. Everything is super slow and laggy.

---

### Post by Jagoly on 2011-10-10
wait, how did you reinstall if you couldn't boot the live cd?

anyway, if it's laggy, that what I meant by partially accelerated. You're now running the radeon driver.

You now have two choices, both to install fglrx (amd/ati's proprietary graphics driver. The first and probably best is to just install it from addition drivers within ubuntu, or go to amd's website and get the latest version. That's a lot more work and probably wont make a difference performance wise. And it didn't seem to work too well last time you tried.

Altohugh, now that I think about it, perhaps just using the radeon driver for a few days, and then set everything up properly once 11.10 is out would be a better idea?

---

### Post by TacticalApe on 2011-10-10
> **Jagoly said:**
> wait, how did you reinstall if you couldn't boot the live cd?

anyway, if it's laggy, that what I meant by partially accelerated. You're now running the radeon driver.

You now have two choices, both to install fglrx (amd/ati's proprietary graphics driver. The first and probably best is to just install it from addition drivers within ubuntu, or go to amd's website and get the latest version. That's a lot more work and probably wont make a difference performance wise. And it didn't seem to work too well last time you tried.

Altohugh, now that I think about it, perhaps just using the radeon driver for a few days, and then set everything up properly once 11.10 is out would be a better idea?
Only the "Try Ubuntu" option doesn't work. Installing works fine.
For some reason, after downloading updates and setting everything back up, it's working pretty good. I'll wait until 11.10 and see how things go once that's all set up.

---

### Post by Jagoly on 2011-10-11
glad to hear! :-)

BTW, are you using the radeon or fglrx drivers at the moment?
On my lappy, a dv6 with radeon 5650, the radeon drivers are quite usable, and in my testing (using at school) the battery life was just as good as fglrx, unlike what most people say. Their plenty fast enough for normal use and are much more stable than fglrx. I just use fglrx because I need the full acceleration to play oblivion (even minecraft works great for me on the radeon driver). On a non gaming machine I'd prefer the radeon driver over amd's.

---

