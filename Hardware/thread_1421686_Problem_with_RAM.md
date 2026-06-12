---
title: "Problem with RAM"
date: 2010-03-04
forum: Hardware
---

### Post by YaMo69 on 2010-03-04
So I just bought an ASUS Eee PC 1201N and I installed Ubuntu on it.
I had already heard that there would be some trouble to get the wireless to work, so first thing I did was fixing that.
This netbook is supposed to have a Dual Core processor and 2GB RAM. At this point System Monitor seemed to think my processor has 4 cores and it only displayed 1.7GB of RAM.
Once I had my internet connection running I did the update through update manager and I restarted my system.
Now, after updating, [this]("http://img514.imageshack.us/img514/5654/naamloospu.jpg") is what System Monitor says. It still says I have 4 processors instead of 2 and it only shows up to 749.2MB RAM.
How can I get this thing to use my full 2GB?

---

### Post by lloyd_b on 2010-03-04
> **YaMo69 said:**
> So I just bought an ASUS Eee PC 1201N and I installed Ubuntu on it.
I had already heard that there would be some trouble to get the wireless to work, so first thing I did was fixing that.
This netbook is supposed to have a Dual Core processor and 2GB RAM. At this point System Monitor seemed to think my processor has 4 cores and it only displayed 1.7GB of RAM.
Once I had my internet connection running I did the update through update manager and I restarted my system.
Now, after updating, [this]("http://img514.imageshack.us/img514/5654/naamloospu.jpg") is what System Monitor says. It still says I have 4 processors instead of 2 and it only shows up to 749.2MB RAM.
How can I get this thing to use my full 2GB?

First off, the reason you're seeing 4 processors is that your cores are "Hyperthreaded", and each core shows up to system like it was two independent processors (each processor runs two independent threads).

As for the RAM, could you post the output of the terminal command "free -m"?  I'm curious what *it* shows for total memory and memory used.

Lloyd B.

---

### Post by YaMo69 on 2010-03-04
```
             total       used       free     shared    buffers     cached
Mem:           749        728         20          0         26        366
-/+ buffers/cache:        334        414
Swap:         5145          3       5142

```

---

### Post by YaMo69 on 2010-03-04
Okay, my system just froze... so  I had to restart by holding the power button and now it looks like I have 1.7GB RAM again... Still not 2GB though.
```
             total       used       free     shared    buffers     cached
Mem:          1760        558       1201          0         97        219
-/+ buffers/cache:        241       1518
Swap:         5145          0       5145

```

---

### Post by lloyd_b on 2010-03-04
> **YaMo69 said:**
> Okay, my system just froze... so  I had to restart by holding the power button and now it looks like I have 1.7GB RAM again... Still not 2GB though.
```
             total       used       free     shared    buffers     cached
Mem:          1760        558       1201          0         97        219
-/+ buffers/cache:        241       1518
Swap:         5145          0       5145

```

That is very weird - the total RAM seen by Linux should *never* vary.  The fact that sometimes it sees one amount, and sometimes another, would tend to indicated a hardware issue (on a desktop I would suspect a RAM stick that wasn't properly seated).

As for why not 2GB, what kind of video card does that machine have?  Could it be using a big chunk of system RAM (rather than having its own dedicated RAM)?

Lloyd B.

---

### Post by YaMo69 on 2010-03-05
> **lloyd_b said:**
> That is very weird - the total RAM seen by Linux should *never* vary.  The fact that sometimes it sees one amount, and sometimes another, would tend to indicated a hardware issue (on a desktop I would suspect a RAM stick that wasn't properly seated).

As for why not 2GB, what kind of video card does that machine have?  Could it be using a big chunk of system RAM (rather than having its own dedicated RAM)?

Lloyd B.

The video card is a NVIDEA ION.
I also saw while using Windows 7, on the Computer Properties screen it said "Memory(RAM): 2GB (using 700MB)". I believe it wasn't exactly 700MB but a bit more.
So it looks like it sees 2GB but it just doesn't use all of it :???:

---

### Post by EpidemiaN on 2010-03-13
I'm having the exact same problem: System Monitor (and free command) shows only 749.2 MB of physical memory (instead of the actual 2GB that the BIOS and Windows recognize) on an Asus 1201n with Ubuntu 9.10.

I though it could be that Ubuntu was "switching off" unnecessary RAM or something. But it seems that is not the case. I made a program that just eats RAM and it could allocate up to 3000 MB, but it just used all 749 MB of recognized RAM and than started eating the swap.

I don't know what might be causing this, but it is quite annoying.

---

### Post by hsoulen on 2010-04-07
Guys, update your BIOS.

This is a known issue with the 1201n. Latest BIOS is 0325 from Asus.

Future reference, occasionally when you restart your 1201n from Linux the BIOS will stop and ask you to "Press F1 to run setup or F2 to restore defaults". If you choose F2 you will only have ~700MB of RAM... Great bug right?

Press F1, then go to exit and save changes to reboot. You will then have all your RAM.

Side note. 1201n only Addresses 3.5GB of RAM (even with a 64-bit OS, as the Atom 330 only addresses this much) and the ION takes a chunk of that for video.

So if you have 2GB, ION will grab ~256MB so you will show ~1.7GB, if you have 4GB, you will only show around ~3.2GB.

Welcome to the 1201n.

---

### Post by stefaca on 2010-05-26
can U tell me how to update BIOS? I'm only using ubuntu :)

---

### Post by hsoulen on 2010-05-26
> **stefaca said:**
> can U tell me how to update BIOS? I'm only using ubuntu :)

Absolutely! I am on Linux only as well.

Asus has a utility called "EZFlash" which allows you to flash your BIOS without booting any OS.


[LIST=1]
[*]Download the newest BIOS from support.asus.com
[*]Extract the BIOS file to a USB Key or SD card (must be formatted FAT) and rename the file to "1201N.ROM" this part is VERY IMPORTANT as the name must always match the model
[*]Reboot your computer and hit "alt+F2" to start the utility (do this when you see the eeePC splash screen before Grub)
[*]The utility should find the USB Drive or SD card and you should be good to go!
[/LIST]

Cheers,

Hank

---

### Post by pterion on 2013-03-22
> the change of the brightness during a linux session leads to a crash of the bios (bios settings are reset) at the next reboot. Under linux there is a package laptop-mode-tools which allows to control the brightness (for example 60% on battery, 100% on AC)...therefore I get my problem when I plug/unplug the AC...the brightness was modified and then at next reboot.

from [http://forum.eeeuser.com/index.php?/topic/77915-1201n-problem-with-ram-2gb-but-768mb-usable/](http://forum.eeeuser.com/index.php?/topic/77915-1201n-problem-with-ram-2gb-but-768mb-usable/)

---

