---
title: "Can't connect to wireless network"
date: 2011-02-15
forum: Hardware
---

### Post by Seltox on 2011-02-15
Hi,
I just downloaded & installed Ubuntu 10.10 today.  I've got a desktop computer with a wireless card (Asus PCE-N13 Wireless Adapter)

My problem is that when i'm running Ubuntu, I just can't connect to the internet.  It can actually find the network, and asks me for a password and such (which I have,) but then it looks like it's trying to connect for about 2-3 minutes, then comes up asking for the password again.  Repeat endlessly.

I thought it could be a driver problem, but I have NO idea how to install stuff in Linux - and all the documentation i've found has all been "It's so simple, you just select what you want, and it downloads & installs it for you!"  which does sound nice, but not when I have no internet access.

The disc that came with the adapter does have linux drivers on it, but again, I have no idea how to 'install' these, and even if the driver is the problem in the first place.  There's a readme for the linux drivers, but that was no help at all - it was all pure jargon to me unfortunately.

Anyone have any ideas?

Cheers,
Seltox

---

### Post by sanderj on 2011-02-15
When you temporarily turn off WPA on the Wifi Access Point, can you connect via Wifi?

---

### Post by Seltox on 2011-02-15
That's also a problem, as I just recently moved into a share house and I have no idea what modem/router they have, or even where it is...

So I can't change the settings.

---

### Post by sanderj on 2011-02-15
Can you connect if you run ubuntu 10.04 (for example from live-CD or live-USB)? Googling for your wifi card reveals it might be a ubuntu 10.10 bug ...

---

### Post by Seltox on 2011-02-16
Okay, I downloaded 10.04.1 and installed it (Live-USB wouldn't boot up strangely enough.  And the installer wouldn't work until I unplugged my second monitor, but afterwards it was fine.) and the wireless worked perfectly fine straight away.

So now i'm just wondering what i'm missing out on with having 10.04.1 instead of 10.10, and if I can update 10.04.1 and not lose my wireless?

Just to be clear for anyone who does a search looking for the Asus PCE-N13 Wireless Adapter, it doesn't work properly in Ubuntu 10.10, but does in 10.04.1
Hopefully that saves people a few hours of searching :)

---

### Post by sanderj on 2011-02-16
> **Seltox said:**
> Okay, I downloaded 10.04.1 and installed it (Live-USB wouldn't boot up strangely enough.  And the installer wouldn't work until I unplugged my second monitor, but afterwards it was fine.) and the wireless worked perfectly fine straight away.

So now i'm just wondering what i'm missing out on with having 10.04.1 instead of 10.10, and if I can update 10.04.1 and not lose my wireless?

So, as I expected: a bug in 10.10. The same threads I read, mention a Ubuntu bug report, and they tell a way how to install the driver from the hardware manufacterer (which include make-ing the source) on 10.10.

10.04 is TLS, so updated regularly. Maybe you miss new software, but I wouldn't worry too much about.

My advice: stay on 10.04, unless you like to play with Ubuntu and you do know what "./configure" and "make" means; in that case you can search the threads and try to make it work on 10.10.

---

### Post by Seltox on 2011-02-17
Absolutely new to Linux in general, so i'll stick with 10.04 for now.  Cheers for the suggestion.

---

