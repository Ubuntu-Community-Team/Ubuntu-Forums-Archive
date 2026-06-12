---
title: "Frustrating HDD problem"
date: 2006-03-15
forum: Hardware &amp; Laptops
---

### Post by kc2idf on 2006-03-15
First off, I'm sorry about cross-posting.  I posted this to Ubuntu/Desktop support before realising that there is a hardware support forum.  I am reposting here because I think this is the better forum for it.  Anyway....

I have a very frustrating HDD problem that seems to be triggered by putting a particular motherboard together with any Debian derivitave. As Ubuntu is my Debian derivative of choice, it is relevant here.

Other people have posted this problem to this forum and that, and, inevitably gotten a reply of "looks like a bad hard drive". I believe this answer is incorrect, because of what I have tried.

I have:
Two Via Epia MII motherboards (identical in every way)
Two Seagate 250GB HDDs (Brand new), ATA/100
One Western Digital 120GB HDD (three years old) ATA/66
One Western Digital 10GB HDD (very old) ATA/33

I have tried:
Motherboard #1 with the 10GB drive with Ubuntu
Motherboard #1 with a 250GB drive with Ubuntu
Motherboard #1 with a 250GB drive with Slackware
Motherboard #2 with the 120GB drive with Fedora Core
Motherboard #2 with the 120GB drive with Ubuntu
Motherboard #2 with a 250GB drive with Ubuntu

In all cases involving Ubuntu, with these motherboards, I get sporadic issues with the hard drive freezing up for up to 30 seconds, and I get the following on the console:

hda: timeout waiting for DMA
hda: drive not ready for command
hda: no DRQ after issuing MULTWRITE_EXT

Note again, all three hard drives are PROVEN GOOD using non-Debian systems. Both motherboards are PROVEN GOOD using non-Debian systems.

I have also tried compiling a custom kernel, but the problem remains.

So what "not the kernel", "not the HDD", "not the motherboard" thing is there that could cause this problem, that is specific to Debian derivatives such as Ubuntu?

---

### Post by John.Michael.Kane on 2006-03-15
@kc2idf Have you tried to edit your hdparm? /etc/hdparm.conf .
[http://leuksman.com/pages/Ultra-DMA_HOWTO/Activating_and_Deactivating_UDMA](http://leuksman.com/pages/Ultra-DMA_HOWTO/Activating_and_Deactivating_UDMA)
[http://www.die.net/doc/linux/man/man8/hdparm.8.html](http://www.die.net/doc/linux/man/man8/hdparm.8.html)

heres my hdparm command..
```
command_line {
       hdparm -q -B255 -q -M128 -q -c1 -q -m16 -q -W0 -q -d1 /dev/hda
}
```

---

### Post by kc2idf on 2006-03-16
Yes, I have done that.  I edited it to match the settings that Slackware selected by default, because the HDD performance under Slackware was positively stellar.  Doing so did boost the throughput to almost the same as Slackware, but it seemed to increase the frequency of these hangup episodes.

Here's what I ended up with in /etc/hdparm.conf: 

/dev/hda {
        io32_support = 1
        dma = on
        mult_sect_io = 16
        interrupt_unmask = on
}

---

### Post by HelLios on 2006-03-16
I had a similar problem a while ago.
It might be the cable..
Try setting with hdparm the udma mode to udma2, that helped with me..

---

### Post by kc2idf on 2006-03-17
Several cables have been tried.  Besides, if it were the cable, then the problem would also manifest on Slackware.

hdparm -X udma2 hung the system so well that an actual power cycle (as opposed to hitting the reset button) was necessary to recover.

Thanks for trying.

---

### Post by mevan on 2006-03-29
Hi. Recently installed Ubuntu 5.10 to get rid of "timeout waiting for DMA" message from Fedora 3...

Nothing, after a few reboots I got the same from Ubuntu! Tried several hard drives and cables both with fedora and ubuntu. The same! So only thing left is the HDD controller chipset.. Mine is a Promise PDC20265 UATA 100.
To me it seems incompatible(??) with debian derivatives.
(just to mention, under suse 9.3 or windows xp everything works ok)

Kc2idf what HDD controller does your motherboard have??

Also tried editing hdparm.conf. Maybe some command combinations work, but I don't have enough time to try them all!!!

Should I give up trying? Is there anything else to do??

Thanx!!!

---

### Post by nodyad on 2006-05-22
I am trying to install Ubuntu 5.10 to an Epia M10000 motherboard with a 30G Maxtor standard ATA HDD.  A little more than halfway through the unpack (somewhere after the interminable Python config steps), the HDD goes quiet, and shortly thereafter I get the "hda: timeout waiting for DMA" error. I am an inexperienced Linux user, but this sounds like the same issue reported in this thread, with similar hardware.  I was able to install Linspire 4.0 successfully on the same HDD and system, FWIW, and can run the damnsmalllinux liveCD successfully (except for not detecting the network card at all).  In my case (recompile is not an option), wait for the next release?
--
Don

---

### Post by Arno_A on 2006-05-23
Hi, you can solve this problem by removing the longhaul module. This problem always bothered me in my breezy install on an EPIA MII12000, and it took me a while to figure it out.

I got the tip from the viaarena forums. 

Just remove the module and you'll be fine.

A.

---

