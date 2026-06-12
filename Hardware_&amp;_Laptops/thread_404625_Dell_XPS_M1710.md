---
title: "Dell XPS M1710"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by Rasta Fari on 2007-04-08
:KS:KS:KS

I have to say that I am indeed impressed by the ease of Ubuntu. The Live CD was a great way to look around and I loved that it let me install without having to go download another 'install CD'. I consider myself moderately advance user, and I was looking for something different in a Linux distribution -- I think I found it.

My hardware is the following:

Dell XPS M1710
Logitech V270 bluetooth mouse
Intel Pro Wireless 3945 wifi
Linksys N Wireless router
FireLite USB 80 Gb external disk

I installed Ubuntu onto my USB disk because I didn't want to tamper with my Windows XP Media edition that's install on my laptop hard drive. I love to play online games and currently I need Windows for that; most of the other time I am on-line I prefer Linux.

Some notes from my installation:

I initially had some trouble getting my wifi to get working. It turns out I had to add an alias for eth1 in the /etc/modprobe.d/aliases (alias eth1 ipw3945).

My bluetooth mouse wasn't immediately recognized. It turns out I had to reset my hci0 bus then do another search.

root@caprica:~# hciconfig hci0 reset
root@caprica:~# hidd --search
Searching ...
        Connecting to device 00:07:61:6B:5D:FB


Hope this post helps someone else enjoy Ubuntu as much as I do...


:popcorn:

---

### Post by firebadger on 2007-04-11
I have the same laptop and am planning on installing kubuntu as a dual boot.  I still need Windows for work alas.  Is this the approach you took and did you have any problems?  Also, did you install Nvidia drivers and do you have any tips in that area?

---

### Post by Rasta Fari on 2007-04-11
I am running Ubuntu on that configuration and I am very pleased.
As far as the Nvidia drivers, no I didn't specifically install them (yet).
However I am not displeased by the native display either 1900x1200 @ 24db.
The USB disk has been working great and I don't notice any performance issues like running the liveCD from the DVD (oh my god).

\\:D/

---

### Post by firebadger on 2007-04-12
Thanks - I'l update this thread with my experiences as and when I get round to / work up enough courage to press ahead with my install.  Its going to involve resizing partitions that I can't afford to break hence my nervousness.

---

