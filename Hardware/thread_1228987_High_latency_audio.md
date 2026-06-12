---
title: "High latency audio"
date: 2009-08-01
forum: Hardware
---

### Post by fela on 2009-08-01
My audio keeps skipping on my ubuntu 9.04 box, I assume due to incredibly high latencies. I can't use the real time linux kernel patch due to nvidia's drivers not working with it ](*,). This means that I can't watch movies or listen to music.

It wasn't like this in earlier versions of Ubuntu, it only started in Jaunty (am right now considering installing version 8.10). Is there anything I can do to make my audio play better? Sorry to sound like a n00b (I ain't one), I know I'm asking a difficult question but I'm wondering if it's just a bug or something.

I have crummy integrated realtek HD audio (mobo: gigabyte ga-m52l-s3 rev2). My CPU should be fine, it's a dual core Athlon X2 6000 at 3.1GHz, and I have 4GB of RAM so that should be more than enough.

Audio plays fine under Winblows, but I don't want to have to use that crap all (any) of the time, so I'm just wondering if it's something as simple as maybe giving the audio server a lower nice value or something.

Thanks for any answers.

---

### Post by fela on 2009-08-06
Well, I had to do a reinstall as my primary HDD with Linux on it got its sixth head crash and could take no more :(. The upside is that I had an excuse to install 8.10, and now the audio works perfect with the generic kernel. I might file a bug report in the jaunty generic kernel.

Shame I didn't get a chance to test out audio on the rt kernel on jaunty though, as the bug might exist on the rt kernel aswell. Oh well. I've learned the lesson now that if it ain't broke don't fix it!

---

### Post by Bucky Ball on 2009-08-06
Are you saying you replaced the drive?

---

### Post by fela on 2009-08-07
> **Bucky Ball said:**
> Are you saying you replaced the drive?

No. I had 2 drives in there. One 250GB, one 750GB, the 750GB (which was the one with Linux on it and a shared NTFS partition) died, so now I have 2 partitions on the 250GB: one Linux and one Winblows. Luckily I had my most important data backed up onto my Linux server before my drive broke.

EDIT: oh, I see what you mean about maybe the music being corrupt because it's on a corrupt drive - I proved this wrong three times, lol. One, the exact same music was playing fine on winblows, two, I put an installation of studio64 linux on the 250GB drive (shrank winblows partition, etc.) and it played fine on that (which had a realtime kernel patch installed), and also the music I'm playing now is copied over from the 750gb drive (I copied all my music from the 750gb to the 250gb as soon as I realized the drive was on its way out).

---

### Post by MarkRatslayer on 2009-09-05
CRUNCHBANG LINUX 9.04.01,KERNEL RT
I HAVE SATELLITE TUNER  TechnoTrend S-1401 DVB-S card PCI (IRQ16)
 how to set the priority of real time for IRQ 16?
and then how to verify that IRQ uses the priority of real time?
 how to do that at boot system RTIRQ load automatically?

---

### Post by Bucky Ball on 2009-09-05
> **MarkRatslayer said:**
> CRUNCHBANG LINUX 9.04.01,KERNEL RT
I HAVE SATELLITE TUNER  TechnoTrend S-1401 DVB-S card PCI (IRQ16)
 how to set the priority of real time for IRQ 16?
and then how to verify that IRQ uses the priority of real time?
 how to do that at boot system RTIRQ load automatically?

You would be much better to post a new thread giving a descriptive title for YOUR problem and as much information as possible about what you have done and what you are trying to do. :)

This thread and the title of it have nothing to do with your problem and you are not going to get a lot of attention buried deep in a thread that has been inactive for a month.

---

### Post by MarkRatslayer on 2009-09-06
thank

---

