---
title: "questions toward buying a new ubuntu machine"
date: 2017-04-11
forum: Hardware
---

### Post by Peter_Brandon on 2017-04-11
Looks like I may need to buy a new machine.  Was hoping people would have answers to a couple questions.

One is whether it makes any sense to buy a laptop with a high-powered i7 chip (say i7-7700HQ)?  Some years ago, I splurged for a laptop with an i7, thinking I could use it for computationally intensive work, only to find that whenever total processor use was above 15% the fan would sound like my vacuum cleaner.  I find that annoying and alarming, so never used the laptop directly for my work.  Maybe I benefitted from snappier response times for other things on the machine, but I couldn't use it as a substitute workstation.  I'm wondering if the situation w/ the new generation of chips is similar or not?

I'm looking at System76 and Dell Precision 'mobile workstations' for ubuntu based machines.  I wonder whether Dell is good at dealing w/ Ubuntu (e.g. they're less upscale models seem to be stuck on Ubuntu 14.04 and come with 'service packs'--whatever that is). Anywhere else I should be looking for Ubuntu systems?  Anyone know of any systems that avoid vPro or TrustZone, which sound like invitations to hackers?

---

### Post by pdc on 2017-04-12
I had rather got behind on new advances; so when the motherboard went on our desktop; our local friendly computer shop recommended I treat myself to an SSD as well: that was a wonderful transformation; we boot in a matter of seconds now; to boot the same distro; installed on our remaining HD is instructive; much slower

---

### Post by Bucky Ball on 2017-04-12
The only thing that makes sense is to clearly state, to us and yourself, exactly what you are intending to use your computer for then match the hardware to that. If you are web surfing and checking emails, you don't need and i7 and I wouldn't waste the money (as it looks like you've discovered).

List what you do with your computer on a day to day basis, we can give more advice. Bandying about hardware specs with no idea what the machine is going to be used for is a bit pointless. :)

(Old adage: you don't need an elephant gun to kill a mosquito. An i7 with 32Gb of RAM is an elephant gun if you're checking emails, watching Youtube and listening to music. Buy an i3 with 4Gb and an SSD. I use an i7 6700 for pro-level video and audio editing. Do you really need something like that?)

---

### Post by Peter_Brandon on 2017-04-12
Thanks folks!  I now have some hope that I can rescue my old machine--doesn't look like that much has changed hardware-wise since I bought it (or maybe I just haven't experienced the new hardware)--but I might not be able to rescue the old machine and in any event it would be good to get impressions on the latest hardware (if it's attractive enough, I'll buy something new).

PDC:  Thanks for the tip on the SSD--was wondering why I'd need that.  Am a bit perplexed.  I read somewhere that SSD accesses only about 19% faster than a 7200rpm HD.  So, maybe it boots so fast because you're booting a disk image or from hibernation?  I wonder how Ubuntu handles either of those (haven't been able to hibernate in years w/o a crash, but that may be my hardware.)  Or my info was wrong?  Also, a SSD that's faster than a HD might conceivably make all system operations while you're using the system faster.  Do you notice much difference there?  (19% wouldn't be huge.)

Bucky Ball:  Fair enough.  I need the system to do a few things:  I run Windows in Virtualbox and then use Windows to VPN to a virtual desktop at work.  Takes about 15% of total CPU power, which has my fan running fairly hard (too hard in my opinion).  I also work on natural language processing with Python and Stanford CoreNLP and do Bayesian and maximum likelihood estimation that can run for a day or two, using up as much processing threads as I can throw at it.  Of course, I don't do that on my laptop--have set up a desktop as a kind of remote workstation and run anything that takes longer than 15 minutes there.  On the other hand, I do almost all my development and testing on my laptop, so it's handy to have something that can take some load for short stints and do it quickly.  Would be amazing to be able to run the longer, full estimation routines on my laptop, if it doesn't strain the system--because remote access to the desktop is shaky (depend on autossh, and it usually fails in a day or two when I'm away). Other than that, I watch streaming video and the usual--mail, word processing, web browsing, etc.  I also often run multiple users (for different purposes) and virtualbox simultaneously.  Have also been thinking of getting into secure OS's, which I gather takes some overhead.  Hope that helps.

---

### Post by oldfred on 2017-04-12
SSD is a lot faster.

This is from my SFF desktop that uses a laptop 2.5" HDD. (seems slow?)
      ```
 fred@Z170N:~$ sudo lshw -C Disk -short
[sudo] password for fred: 
H/W path               Device     Class          Description
============================================================
/0/100/14/0/2/0.0.0    /dev/sdc   disk           30GB SCSI Disk
/0/1/0.0.0             /dev/sda   disk           250GB Samsung SSD 850
/0/2/0.0.0             /dev/sdb   disk           1TB HGST HTS721010A9
HGST Travelstar 2.5-Inch 500GB 7200RPM SATA III 32MB Cache 

   fred@Z170N:~$ sudo hdparm -t /dev/sdb2
/dev/sdb2:
 Timing buffered disk reads: 402 MB in  3.01 seconds = 133.44 MB/sec
fred@Z170N:~$ sudo hdparm -t /dev/sda4
/dev/sda4:
 Timing buffered disk reads: 1580 MB in  3.00 seconds = 526.41 MB/sec 

```    

My other desktop system has a 3.5" HDD 7500RPM and it was 171.23 MB/sec     
And old system with low cost 60GB SSD from 2011 was 208.20 MB/sec and 160GB SATA HDD from 2006 was 70.46 MB/sec, so even SSD was major improvement in my old system, but not a lot faster than new HDDs.

---

### Post by Peter_Brandon on 2017-04-13
Wow oldfred:  So it seems that your test shows the SDD working 4 times as fast as your HD.  That is definitely worth the steep SDD price.  I guess the usual approach, if we're not able to splurge $500 on a big SSD would be to put the OS on it for quick OS boots and operations.  Thanks for the info!

---

### Post by Bucky Ball on 2017-04-13
Yes. Rule of thumb is OS on the SSD (or OSs) and everything else, including the /swap partition, on HD, preferably a 7200rpm one. :)

---

### Post by oldfred on 2017-04-13
The even newer NVMe SSDs are even faster.

But I do not buy a large SSD as I do not need it. 
My 120GB SSD has two 25GB partitions for / (root) current LTS and last or next LTS version. And then I wonder what to do with the rest of it?
I have all my data on the HDD in a 100GB partition and some other installs & partitions, but even my 1TB HDD is not fully used.

Even my old system with 60GB SSD had two / partitions. I was going to get a new UEFI system back in 2011, but the old SSD made it work so well, it was 4 more years before new UEFI system.

---

### Post by Peter_Brandon on 2017-04-14
Thanks!  SSD is definitely on my shopping list :)

---

### Post by Peter_Brandon on 2017-04-22
Incidentally, I recently learned about AMD's Ryzen chip.  Looks like it could be a good advance in performance and price, though it'll probably be end of year at least before Ryzen based laptops become available.  It doesn't, apparently, use TrustZone, but it still has a PSP / ARM security processor that people worry about creating back doors for attackers, including, ahem, state actors.  But one difference between AMD and Intel is that Intel vPRO / ME is specifically designed to allow remote and invisible access and control to a computer.  AMD ARM looks to be primarily a DRM / secure content scheme.  It's not inconceivable that it could connect out to the network, but that doesn't seem to be what it's meant to do.  Libreboot is also trying to convince AMD, which is acting receptive, to release the source code behind its ARM security scheme.  That would get some eyes on it and reassure the public that the ARM isn't meant to spy on people's computers.  Libreboot should start a petition!

---

### Post by henke54 on 2017-04-24
> **Peter_Brandon said:**
>  Anywhere else I should be looking for Ubuntu systems? 
[https://www.ubuntushop.be/index.php/en/](https://www.ubuntushop.be/index.php/en/)
;)

---

