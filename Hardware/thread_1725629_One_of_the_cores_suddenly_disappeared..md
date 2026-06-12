---
title: "One of the cores suddenly disappeared."
date: 2011-04-10
forum: Hardware
---

### Post by GTMoraes on 2011-04-10
Hello.

Yeah,that's exactly what it sounds like. While I was watching peacefully my copy of Harry Potter and the deathly hallows, my XBMC halted for a sec, making me press pause and play twice to keep the movie going on. When the movie ended (no perceptible lag, it's the Media Center PC, check the sig), I closed XBMC to check the ubuntu forums. The first thing I saw was an Error report from a Awn miniapplication, which chekcs for the Core frequency variations. The Core1 Monitor had crashed for no apparent reason. I've removed it and continued on with my life. While multitasking (extracting a big archive, thousands of Chrome tabs open, some with Flash and listening to music on Audacious), I've noticed a major lag and 100% CPU Usage @ 2.6GHz. I opened the system monitor and noticed a lack of a second core (It used to show CPU1 and CPU2 on Resources tab), so I restarted to see if it was something software related. After the reboot, before GRUB kicking in, the Boot On Lan came in, so did a spine cold. I thought my HD/Processor died or something, Ctrl Alt Del'ted and it booted fine and there are two cores working. The Awn freq monitor now does find two cores, so does the system monitor. I'm typing this message from the Media Center PC.


I updated today the kernel to 2.6.38 and I've set the Processor type to Athlon/Opteron/K7 (or something like that).

What might have caused it? Faulty hardware? some random bug? kernel bug?
It might be nothing, but I'm just worried with this machine. 

P.S.: Even when the second core disappeared, the Awn temperature monitor did find two cores and was reporting the temp of both normally
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 256MB | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" 1366x768 LED | 6:30hrs Battery
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by Yellow Pasque on 2011-04-10
Losing cores in the middle of a session - that's a new one to me. Just to be sure, you don't have one of those Athlon II's that got rebranded as Athlon series, do you? I've read that Athlon/Phenom II's have dynamic core control, so I could see it shutting down a core if overheating (though more likely, they would scale back clock/voltage first).

I would check dmesg at the time it happened (older dmesg logs get tar'd to save space, but they're still there in /var/log).

---

### Post by GTMoraes on 2011-04-10
This processor was bought when "Athlon 64 X2" was the master chief of AMD. It still has the white-black sticker with a big 64 infront of it. I don't think it has such technology, but indeed the processor was heated.

It happened yesterday at around 23:30 (It's 16:42 from today). I'm on the netbook, I'll try copy the log to here soon.

What's weird is the fact that the core disappeared - but was still reporting its temperature, and upon restart, everything went ok.

[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 256MB | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" 1366x768 LED | 6:30hrs Battery
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by BrandyBear on 2011-04-10
i suppose that your core had over heated and had shutdown to avoid explosions And waited a few Minutes or an hour To reboot so that is why you movie had jolted then stopped so the core had time to shut doewn and you computer had stopped to Allow the system to recognise it

---

### Post by GTMoraes on 2011-04-10
Whoops, I restarted, not the machine itself. The machine was running fine, but slowly. But you've got a point

---

