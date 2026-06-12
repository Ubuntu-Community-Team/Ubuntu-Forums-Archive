---
title: "File copying slows down the whole system"
date: 2011-10-23
forum: Hardware
---

### Post by Gelupah on 2011-10-23
Hi all,

Since my fresh 11.10 install (after a format), every time I copy files, from one HD to another, from USB to HD etc, my whole system becomes incredibly slow and unresponsive. The mouse cursor drags and freezes for small amounts of time, any music or video playing will jitter, browsing is impossible...

What could be the cause, any ideas? It's very frustrating, my 6 core processor with 4Gb of RAM should easily cope ! Driver problem?

I didn't used to have this issue with 11.04 (upgraded from 10.10)

Thanks for any ideas, getting desperate here !

---

### Post by bbashy on 2011-10-26
Got the same issue, trying to copy 5GB from /media/ to /home/ and it didn't even complete.

Copying one file at a time now (150MB) and even that is freezing everything :/

---

### Post by WasMeHere on 2011-10-26
> **Gelupah said:**
> ... It's very frustrating, my 6 core processor with 4Gb of RAM should easily cope ! Driver problem?

I didn't used to have this issue with 11.04 (upgraded from 10.10)

Thanks for any ideas, getting desperate here !

Hi Gelupah,

Do you have a backup? In that case I suggest that you restore your working 11.04 system. 'If you like solving problems, update to a bleeding edge version, otherwise sit back and avoid upgrading until a lot of the bugs are found and fixed.'

Have fun instead of frustration :-)
Olle

---

### Post by diasf on 2011-10-26
That reminds me of when DMA wasn't a standard feature.... worth checking if anything disabled dma for the device in question....

---

### Post by neoargon on 2011-10-31
Same problem here too. Mine is ubuntu 11.10 . The problem is not for just file copying. While the Banshee is scanning, or while the nepomuk is indexing, slow down occur. You can't even play an mp3 . It gets stuck

---

### Post by Gelupah on 2011-11-02
Excellent remark. I recall having that exact problem back in the win95 98 days, and couldn't recall what it was due to. I think it was sometimes motherboard drivers, but very often all I had to do was tick the DMA checkbox in the settings somewhere...

DMA sounds very possible; how can I check, any ideas? I'll look into it on my side, thanks for your input. :D


> **diasf said:**
> That reminds me of when DMA wasn't a standard feature.... worth checking if anything disabled dma for the device in question....

---

### Post by WasMeHere on 2011-11-03
Hi guys,

Have you checked if there is some process, that is occupying the CPU(s) or RAM? You can use the System Monitor (from the menus) or install ***htop*** from the repositories
```
sudo apt-get install htop
``` It has a small footprint and is very good for looking into which processes are making the computer busy.

What about your graphics drivers? Have you checked if there are any proprietory drivers, that are offered to be installed? What happens if you change whatever is your driver state (to or from the proprietory driver)? Have you tried different desktop configurations?

---

### Post by Gelupah on 2011-11-08
> **Olle Wiklund said:**
> Hi guys,

Have you checked if there is some process, that is occupying the CPU(s) or RAM? You can use the System Monitor (from the menus) or install ***htop*** from the repositories
```
sudo apt-get install htop
``` It has a small footprint and is very good for looking into which processes are making the computer busy.

What about your graphics drivers? Have you checked if there are any proprietory drivers, that are offered to be installed? What happens if you change whatever is your driver state (to or from the proprietory driver)? Have you tried different desktop configurations?

Thanks for the advice. 

htop installed. As I am running just a few low key programmes (firefox, Audacious, etc), I get the following:
- 6 cores are only used between 0.7 and 7.8% max
- Mem is at 1030/3959
- Swp 0/2047

Copying files onto a USB external drive:
- 6 cores vary between 0 and 32% max
- Mem is at 1134/3959
- Swap still at 0

Copying a file from USB to HDD1; + at the same time, copying a file from HDD0 to HDD1
- 6 cores between 7 and 56%, overall higher usage though
- Mem only at 1046/3959
- Swap... 0

CPU, Mem and swap look fine to me; yet, when I copy files I actually get keyboard lag. At the very moment I'm typing this message, words sometimes stutter and take a while to show up. Strange.


glxgears is giving me the following:

```
299 frames in 5.0 seconds = 59.691 FPS
299 frames in 5.0 seconds = 59.685 FPS
300 frames in 5.0 seconds = 59.890 FPS

```

Strange. Could it be graphics related? Why would the HDD be a factor in that case?

What do you mean by "different desktop configurations"?

---

### Post by Gelupah on 2011-11-08
Well, there's one improvement for sure :

glxgears
```
32574 frames in 5.0 seconds = 6514.748 FPS
32578 frames in 5.0 seconds = 6515.445 FPS
32582 frames in 5.0 seconds = 6516.333 FPS

```

I am hoping this weird symptom was actually caused by the fact I hadn't installed the proprietary drivers... Fingers crossed, I'll keep you updated.

---

### Post by WasMeHere on 2011-11-09
Yes, let us hope that your problem is solved :-)
Requests for graphics might have created a bottleneck somewhere in the internal communication.

Olle

---

### Post by Gelupah on 2011-11-15
> **Olle Wiklund said:**
> Yes, let us hope that your problem is solved :-)
Requests for graphics might have created a bottleneck somewhere in the internal communication.

Olle

Thank you, seems fixed to me :) Must have been a bottleneck indeed.

Who would have thought...

---

