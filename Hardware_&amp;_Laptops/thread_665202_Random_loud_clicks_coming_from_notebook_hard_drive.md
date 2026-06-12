---
title: "Random loud clicks coming from notebook hard drive, what is the cause/solution?"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2008-01-12
Here's what happens:

While I'm using my Dell Vostro 1400, sometimes a loud click (much like a metronome click) will sound from the area where the CD hard disk is at. It doesn't seem to matter how active the system is, it just happens randomly.

I think it's coming from the CD drive (it sound like it's coming from the front of the laptop where the CD/DVD drive is), but after reading the (numerous?) posts on laptop-mode killing hard disks, I have began to worry.

Can someone tell me how to check:

1. if my hard disk is really powering off at these times?
2. The current "Load_Cycle_Count" on my hard disk?

I only enabled laptop mode once in /etc/default/acpi-support, but I turned it off right away because (as the comment above it states) I got some random freezes that were quite annoying.

The clicks do not seem to be at any defined interval, and they happen less frequently that I turn the laptop on and off (I probably end up cycling the power at least four times a day when I'm using it). It only seems to click once every two to four hours, maybe more. I've used it some times and it's never even clicked once.

Thanks.

Reference:
Dell Vostro 1400
Intel Core 2 Duo 2 GHz each
3 GB Ram, 1 GB swap (AFAIK never used)
nVidia Graphics card
Ubuntu Gutsy (I think... it's the latest stable one)

I've also got powersaved installed, could this be part of the issue?

[edit]
OK. I've installed smarttools, and smartctl reports a large "start_stop_count" but this goes up regardless of counts. there is no Load_Cycle_Count... Still the question remains: If I've never enabled laptop mode, is there anything to worry about? Shouldn't the drive (by default) be hdparm -B255 or whatever it is to disable it, or should I add this to the rc.local startup script?

---

