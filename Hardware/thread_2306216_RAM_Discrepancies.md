---
title: "RAM Discrepancies"
date: 2015-12-13
forum: Hardware
---

### Post by typos1 on 2015-12-13
I recently got a new pc with 8Gb of RAM and integrated graphics, I noticed that System Settings/Details it reports 7.0Gb of RAM and yet Catalyst reports that the integrated graphics uses 768Mb of RAM, meaning a discrepancy of 424Mb (if you take 8Gb of RAM as 8x1024Mb). I thought it was a bit strange as all my installs of Ubuntu have added up to the correct amount of RAM, where could the other 400 odd Mb be ?

Anyway, I wiped the HDD of my old pc and re-installed Ubuntu 15.10. This pc has 4Gb RAM and a graphics card with 512Mb of RAM. System Settings/Details has always reported "4Gb" of RAM in the 3 and a half years I ve had it. But after installing 15.10 System Settings/Details now reports 3.2Gb of RAM. 

Why the discrepancy ? Its connected to the monitor via the DVI out of the graphics card, so surely it cant be that its not recognising that. I havent installed the nVidia driver yet but I cant see how that would make any difference anyway. I originally installed 12.04 on this pc and upgraded it when each new version came out, this is the first fresh install I ve done since I ve had it. 

I m wondering , what with the lost 400Mb on my new pc, if later versions of Ubuntu do something different, or whether theres a bug or something ? Anyone got any ideas ?

---

### Post by typos1 on 2015-12-13
Well, I seem to have a dodgy (1Gb) RAM module on my old pc, it was fine a few days ago, now when removed it says 2.9 Gb for system RAM. That answers it for my old pc.

Still dunno where the "lost" RAM is on my new one though . .

---

### Post by Doug S on 2015-12-14
You should be able to closely examine your /var/log/kern.log file to determine exactly how your 7.0 GB number is derived. See [this]("http://ubuntuforums.org/showthread.php?t=2299975&p=13377824#post13377824") example, from my system.

---

### Post by typos1 on 2015-12-14
Thanks, I ll check it out.

---

### Post by typos1 on 2015-12-17
Actually, the BIOS on my old pc reports the correct 4.096Gb of RAM. I m a bit confused here - the pc has a 512Mb graphics card and Ubuntu always reported 3.9Gb RAM, all I did was wipe the hard drive and then install Xubuntu (WITHOUT removing the graphics card), why would Xubuntu only report 3.25Gb of RAM ?

And on my new pc I get this:

```
1M3XAP-00:~$ grep Memory /var/log/kern.log
Dec 17 14:15:58 M1M3XAP-00 kernel: [    0.000000] Memory: 7126700K/7545816K available (8148K kernel code, 1237K rwdata, 3800K rodata, 1460K init, 1292K bss, 419116K reserved, 0K cma-reserved)
```

All that I can workout form that is the total IS 8.1Gb (as it should be), seeing as the graphics uses 768 I d expect 7.380Gb to be available, but I get 7.126 out of 7.545 available, surely this doesnt make any sense ?

---

### Post by Doug S on 2015-12-17
> **typos1 said:**
> Actually, the BIOS on my old pc reports the correct 4.096Gb of RAM. I m a bit confused here - the pc has a 512Mb graphics card and Ubuntu always reported 3.9Gb RAM, all I did was wipe the hard drive and then install Xubuntu (WITHOUT removing the graphics card), why would Xubuntu only report 3.25Gb of RAM ?I don't know. You would have to examine your kern.log file the same way as you are doing on your new pc.
> **typos1 said:**
> And on my new pc I get this:

```
1M3XAP-00:~$ grep Memory /var/log/kern.log
Dec 17 14:15:58 M1M3XAP-00 kernel: [    0.000000] Memory: 7126700K/7545816K available (8148K kernel code, 1237K rwdata, 3800K rodata, 1460K init, 1292K bss, 419116K reserved, 0K cma-reserved)
```

All that I can workout form that is the total IS 8.1Gb (as it should be), seeing as the graphics uses 768 I d expect 7.380Gb to be available, but I get 7.126 out of 7.545 available, surely this doesnt make any sense ?BIOS kept some memory for itself, and gave 7545816K to the kernel, which it turn is has reserved 419116K, leaving 7126700K available. As mentioned on the other thread, some of that might be freed later in the boot cycle to give the number that you ultimately get when you look at mem total in /proc/cpuinfo.

---

### Post by typos1 on 2015-12-17
I ll check it on my old one, but I didnt think Xubuntu would do anything different to Ubuntu mem allocation wise.

I-Nex reports 7173 total, system monitor reports 7000 available, settings/system reports 7.0Gb. 

But swap is 7.2, suggesting the installer saw 7.2Gb available when I installed it.

Couldnt see anything about "/proc/cpuinfo" in the thread you linked to, not used it myself.

---

### Post by Doug S on 2015-12-17
> **typos1 said:**
> I-Nex reports 7173 total, system monitor reports 7000 available, settings/system reports 7.0Gb. 

But swap is 7.2, suggesting the installer saw 7.2Gb available when I installed it.

Couldnt see anything about "/proc/cpuinfo" in the thread you linked to, not used it myself.Sorry, I meant to write /proc/meminfo.
I am a server guy and not familiar with I-Nex or system monitor or settings/system.

---

### Post by Yellow Pasque on 2015-12-18
First of all, you need to be familiar with a few concepts:
[https://en.wikipedia.org/wiki/3_GB_barrier](https://en.wikipedia.org/wiki/3_GB_barrier)
[https://en.wikipedia.org/wiki/PCI_hole](https://en.wikipedia.org/wiki/PCI_hole)

That explains why you saw 3.2GB on your old computer and saw 2.9 when you took a stick out. It's not because you had a bad stick of RAM. You may have been able to see all 4GB if you were running a 64-bit OS and your BIOS supported remapping the hardware addresses over 4GB.

```
419116K reserved
```

Some of the space is used for hardware addressing. Your BIOS has probably remapped the hardware addresses over 4GB, but since you have so much physical RAM, the two address spaces are conflicting again.

> seeing as the graphics uses 768
It may be dynamically allocated (i.e. it only allocates 512MB or less at boot and only tries to allocate more under very demanding tasks).

Long story short: All of these things that you're seeing are par for the course and aren't cause for worry. (Note: Windows "hides" these things to some degree). The only things you can do are:
1. Make sure you use a recent 64-bit version of Ubuntu
2. Make sure your BIOS is up to date and has memory (hole) remapping (aka memory hoisting) enabled if the option exists. On older systems or OEM systems, you often don't get the option.

---

### Post by typos1 on 2015-12-18
Thanks, I ll read those links re: my new pc.

But, what I dont understand is how my old pc showed 4Gb all the time I used it with Ubuntu (from 12.04 to 15.04, all 64bit versions) yet now it only shows 3.2 when the ONLY thing that has changed is that its running Xubuntu 15.10 64bit, everything else is exactly the same as it was before, including the BIOS which is the most up to date version. (I havent used Windows for over 6 and a half years BTW).

---

