---
title: "[SOLVED] Exremely Slow Computer - Even in BIOS !!!"
date: 2008-11-17
forum: General Help
---

### Post by Deathray on 2008-11-17
I know this forum is not a Windows support forum, but I however don't believe this is a Windows related problem.

I was running this tool for educational reasons. [BarsWF]("http://3.14.by/en/md5")
It utilizes both GPU and CPU to crack MD5 extremely fast. Now I only had the tool running for 30 seconds before I went into the process manager and did something very stupid. I gave the process RealTime priority instead of the original Normal. Obviously my computer freaked out. The entire screen locked, except the mouse which reacted every 10-15 seconds. So I manually power off the computer.

But this is where the weird part starts! My Computer boots extremely slow! The Ubuntu / Windows boot animation is moving in slow motion and when I try entering the BIOS, even that reacts really slow!

What could be the problem? I tried Vacuum Cleaning my pc and loading the default BIOS settings.

**My hardware:**
MB 775 ASUS P5Q PRO / Intel P45 Express / 1600 MHz	P5Q/PRO
CPU 775 CORE2 QUAD Q6600 2.4 GHz FSB1066 2x4MB BOX	BX80562Q6600
VGA PCI-E 512 MB GEFORCE 9800 GTX INNO3D GDDR3 DUA	9800GTX-H5GTCDS
HD SATA2 500 GB SAMSUNG SPINPOINT T166 16MB 7200RP	HD501LJ
RAM 4096 MB DDR2 PC2-6400 CORSAIR XMS2 800 MHz (2x	TWIN2X4096-6400C5 G
PSU 650W CORSAIR TX SERIES ATX2.2	CMPSU-650TXEU
DVD-BURNER PIONEER DVR-215DBK 20x/10xDL DUAL-LAYE	DVR-215DBK

---

### Post by Monotoko on 2008-11-17
Hmm, that program looks dodgy, maybe when you gave it real time control it did some perminant damage to your hardware....This is why you shouldnt play with hacking tools unless you know what your doing, and definatly dont play with them in windows

You could try reinstalling windows/ubuntu

Try running top in ubuntu (either from the installation or a LiveCD) and post the output here

---

### Post by Deathray on 2008-11-17
I knew exactly what I was doing and the tool is well known and approved of.
And you didn't understand my OP. Even the BIOS was going in slow motion. How would you expect me to boot from a live CD? Good thing I'm not an idiot and listened to your advice to reinstalling my operating systems as the symptoms obviously pointed to a hardware related problem.

Besides that, I actually solved the problem myself. My mouse started acting weird yesterday so I plugged another one in and used that instead. I just forgot to unplug the defect one. After that - Back to normal :) Good lesson learned!

---

### Post by sirjoebob on 2008-11-17
Saying you're not an idiot and following it up with 'I forgot to unplug a defective second mouse' is kind of ironic... Lol.

---

### Post by Deathray on 2008-11-17
> **Monotoko said:**
> You could try reinstalling windows/ubuntu

> **Monotoko said:**
> This is why you shouldnt play with hacking tools unless you know what your doing, and definatly dont play with them in windows

No, ironic is you indirectly calling me an idiot after those two statements. Why do you feel the urge to go hostile?

I'm sorry if I offended you by throwing your help in the garbage - But I really think you should at least think twice before asking someone to reinstall there operating system(s).
Especially when in my situation the problem was persistent throughout both operating systems + BIOS configuration.

---

### Post by Marius Derekus on 2008-11-17
Let's stop calling people idiot's. BUT, if he knew what he was doing, he knew what he was doing. After all, it works now (and besides, somtimes even when you know what your doing things still go wrong).

---

### Post by bestseclub on 2008-11-17
How could a mouse make bios run slower?weird O_o

---

### Post by Marius Derekus on 2008-11-17
One time my bro had the wrong mouse in and his system wouldn't even boot. He switched the mouse and it worked fine. It happens, but who knows why.

---

### Post by Deathray on 2008-11-17
I love these types of problems because they help you learn how to attack problems in the future, isolating the true cause (: . Sometimes the issue is much more simpler than expected:KS

> **Marius Derekus said:**
> (and besides, somtimes even when you know what your doing things still go wrong).

Thank you for saying that. You are completely right :P. I was afraid he would mock me by asking why things went wrong when I knew what I was doing :b.

---

### Post by hayden92 on 2008-11-17
You should mark this thread as 'solved'

---

### Post by Deathray on 2008-11-17
> **hayden92 said:**
> You should mark this thread as 'solved'

Thanks for the heads-up. I forgot about that forum feature.

---

### Post by dcstar on 2008-11-18
> **bestseclub said:**
> How could a mouse make bios run slower?weird O_o

External hardware generally uses things called "Interrupts" to function, these are essentially signals from the hardware that cause the system to then run some code to fetch the data and process it before doing what else needs to be done.

Because a mouse is a HID (Human Input Device) most kernels give these interrupts a high priority (because humans are generally very impatient things and hate waiting for computers to respond), so if a faulty device floods a system with input then the massive amount of unanticipated interrupts can really load down a system.

A faulty keyboard could cause exactly the same problem, someone jamming a wireless keyboard/mouse receiver the right way could also - theoretically - cripple your machine.

---

### Post by Marius Derekus on 2008-11-19
> **Deathray said:**
> I love these types of problems because they help you learn how to attack problems in the future, isolating the true cause (: . Sometimes the issue is much more simpler than expected:KS



Thank you for saying that. You are completely right :P. I was afraid he would mock me by asking why things went wrong when I knew what I was doing :b.

No problem. If anyone knows what it's like to have what seems like a major problem when it's just something little (or when you do EVERYTHING right and something still goes wrong), it's me.

---

### Post by y@w on 2008-11-20
One way to catch that is to look at top (in the OP case, it would have to be a live CD) and check the %hi usage on the CPU. That'll tell you if there's something hogging the hardware interrupt on the CPU.

---

### Post by lisati on 2008-11-20
> **Marius Derekus said:**
> One time my bro had the wrong mouse in and his system wouldn't even boot. He switched the mouse and it worked fine. It happens, but who knows why.

**it happens: the usb mouse I purchased for my new laptop doesn't work with Vista (probably needs a new driver or something of that ilk) but works well with my older laptop......

(Notes: thread marked as "solved", so time to browse the forums)

---

