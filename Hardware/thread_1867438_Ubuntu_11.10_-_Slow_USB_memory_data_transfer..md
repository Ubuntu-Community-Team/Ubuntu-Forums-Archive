---
title: "Ubuntu 11.10 - Slow USB memory data transfer."
date: 2011-10-22
forum: Hardware
---

### Post by ponchopv on 2011-10-22
Hi,

I've just installed Ubuntu 11.10 and I have had a couple of problems, one of them is that the usb data transfer is very very slow. 

The speed is like working in mode 1.0.

Any suggestion?

Regards.

---

### Post by dleric on 2011-10-23
Same here..   1.2 MB/sec.  Aprx 100 meg per minute..

---

### Post by mikekorncnx on 2011-10-30
Problems with USB transfers here too. Initially very fast and seems to make a complete transfer, but the file transfer window will freeze and need several minutes to actually close. Very disappointing. Ubuntu has never handled USB transfers particularly well and this is a major drawback. Seems like it would be such a simple fix.

---

### Post by aallengraphics on 2011-11-01
Same Problem, tried to transfer a few files to usb stick - seems fast at first - then hangs at the end for a very long time! Hope it get fixed soon!

---

### Post by repilce on 2011-11-03
Same ol' crap.. anyone know a distro that does not have this problem?

---

### Post by bluexrider on 2011-11-03
Has anyone made a bug report? Seams like the thing to do.

---

### Post by repilce on 2011-11-03
> **bluexrider said:**
> Has anyone made a bug report? Seams like the thing to do.

If you search around (and or have been toying with ubuntu for some time) You can see that this problem has been around since 8.**

I can find post after post from version to version, have never found a proper solution. I'm just going to look elsewhere I need to get off my Ubuntu training wheels anyway.

---

### Post by tmattoneill on 2011-11-06
Definitely MUCH worse. I backed up my Ubuntu 10 to an external HD. About 80Gb took about 5-7 minutes. (17-20Mb/s)

Then I installed 11.10 and the same transfer BACK to the computer is taking forever. Transfer is at between 800KB/s - 1.8Mb/s.

This is horrible. I've noticed a lot of things are MUCH more sluggish with this new distro. 

Any help/pointers greatly appreciated.

---

### Post by filamento on 2011-12-14
I can confirm this bug also appears in my Compaq Mini 701ES netbook.

I've formatted a USB flash drive with "Linux Live USB Creator", as recommended by the official Ubuntu webpage.

Then I've tried to boot up Ubuntu 11.10 to try it.

It takes AGES. Almost 20 minutes to boot up. This is ridiculously slow.

Using the same USB flash drive Fedora 16 boots in less than a minute.

There's a huge problem with USB in Ubuntu 11.10

---

### Post by Flash__Gordon on 2012-01-25
> **repilce said:**
> Same ol' crap.. anyone know a distro that does not have this problem?

10.04.3 32 bit worked flawlessly with usb. I am able to transfer 3.4GB @ 21 MB/s (with an older flash drive) , not so in 11.10 64 bit 7 MB/s if I'm lucky.

Flash

---

### Post by edujillo on 2012-02-05
Hi there!

I am having the same problem using Release 10.04 (lucid) (kernel 2.6.32-38, Gnome 2.30.2, on an Asus MB + AMD Phenom 64-bit quad-core).

I use Krusader to manage files, and when copying a big file, the process takes a looong time, frequently stalling along the way. When it finally reaches 100%, it usually stalls for a VERY LONG time. Even if I kill Krusader, the memory stick remains mounted for quite a while. 
I have not found a way to unmount it sooner for taking it off safely.
Does anybody have a hint about this issue, or a fix for it?

Thanks!

---

### Post by mubeen304 on 2012-02-07
I hate this problem .... I installed Ubuntu 11.10 on my netbook (Medion Akoya E1228 -  N570, 2GB DDR3) using Wubi in Win7.

****- ** A part from the USB problem, there is another issue .. the data transfer rate from other partitions on hard-disk is also extremely sluggish, and halts even for 30-40 minutes.

****- ** I found it better to use bash command line to transfer date between USB & Ubuntu, it is a little bit quicker and finally finishes in finite time.

I think that perhaps these problem are due to installation using Wubi.

---

### Post by icansolvetheproblem on 2012-02-20
I upgraded from 10.03 to 11.10 and my USB transfer rate dropped to 1.4 MB per second.   Downgraded to 11.04 - USB transfer rate starts out around 48 MB per second but in about five seconds it drops to 2 MB per second.  

I didn't use Wubi. This seems to be hardware specific as a different box running 11.10 doesn't exhibit any USB throttle.

Machine  with USB transfer issues (same with 11.04 and 11.10 64bit):

Intel DP45S mobo w/p45 chipset, Q8400 @ 2.66Ghz proc, 8 GiB corsair DDR3, dual velociraptor 1tb sata drives mirrored 

Machine without any USB transfer issues (running 11.10 64 bit):

Intel Core 2 duo, 4GiB DDR2, dual Seagate 1tb sata drives mirrored

---

### Post by Botruckle on 2012-03-10
This issue has been going on for quite some time, as "replice" noted back in November. If anyone is actually investigating this issue, they have not come up with a solution. A simple transfer of an audiobook to my walkman will start out fine, then stall for several seconds, then another spurt of transfer followed by another stall, etc. Frustrating! I'm on 11.04.

---

### Post by mubeen304 on 2012-03-13
[COLOR=Red]Some results from my experiment:[/COLOR]
After my last reply on 7th Feb. , I continued struggling with this problem, it was Wubi installation (64-bit) with Win7 starter (on tiny netbook). Someone advised me to check the "mount.ntfs" process during transfers.
Whenever I am doing something important on system (installing softwares, data transfers) this moron "mount.ntfs" brings the CPU down to knees, and everything stalls.
Perhaps it was due to installing Ubuntu on "ntfs" partition of windows.
So I installed Ubuntu on a separate partition (obviously without wubi), this time 32-bit (not like previous 64-bit), and the netbook+Ubuntu lived happily ever after :D; the result is consistent faster transfer speeds around 15-25 MB/s.

---

### Post by recluce on 2012-03-13
> **bluexrider said:**
> Has anyone made a bug report? Seams like the thing to do.

Bug reports for Ubuntu are mostly pointless, unless a developer shares in your pain personally or "feels" like descending from Mount Olympus to take care of the bug. You don't believe me? Check out the number of unresolved bugs on Launchpad....

Maybe some of you could have the problem I had and solved in 10.04:

[http://ubuntuforums.org/showthread.php?t=1867460](http://ubuntuforums.org/showthread.php?t=1867460)

---

### Post by Axis Mann on 2012-03-15
I was researching a slow usb 2.0 problem when I came across this entry.  I've found complaints like this one across many versions of ubuntu.  I'm surprised that any of this stuff works some of the time much less all the time.  In my situation, USB 2.0 read speed is approx 5 MB/s for Lucid on my Intel G41M4-F motherboard but is approx 30 MB/s  for same drive on my Dell Dimesion when booted with Lucid Live CD.  However, when I test USB 2.0 on my Intel G41M4-F mother board using Oneiric for same drive, I get approx 30 MB/s read speeds.  In all cases, the write speed is approx 30 MB/s.  I'm starting to think that some hardware is better supported than others or that USB is not that universal.  I hope my problem will eventually go away in 2013 when I upgrade to the next LTS version 12.04 (yeah, I'm going to wait a while)  which I hope works as well as Oneiric.  I sure wish I could find som one to confirm that they experience the same problem with Lucid 10.04 running on a G41M4-F that I'm having. Or maybe my motherboard is bad?  You can test by booting a live CD for lucid.  Thanks.

---

### Post by GuiGuy on 2012-03-22
The USB file transfer saga on ubuntu (and linux, I suspect), is shameful. For me it's been going on at least since Karmic across all manner of hardware. The fanbois, of course, will accuse me of being too stupid to use linux and that it's all my fault. 

The fact remains that given the same hardware on W7 I can transfer files at speeds consistently higher than 12MBps. On linux a 1G file will take around one to two hours, depending on the ambient temperature.

I, as have others, have raised bug reports. One I raised in the day of karmic, with at least a 100 others listed as 'affected', remains 'triaged' to this day. 

I'm ranting about this now because today I needed to transfer 2 X 2G files from a server to a USB stick. My Ubuntu machines proved hopeless. In the end I ate humble pie and borrowed someone's Win7 notebook. I was able to to do in minutes what was going to take my otherwise very smart Ubuntu Oneiric desktop over a day.... as I stated, it is shameful.

---

### Post by McWire on 2012-04-03
I'm running 11.10 amd64. My speeds are starting at about 8MB/sec, and slowly climb by one-tenth/sec until stabilizing at 20.4MB/sec. :confused:

---

### Post by GuiGuy on 2012-04-03
> **McWire said:**
> I'm running 11.10 amd64. My speeds are starting at about 8MB/sec, and slowly climb by one-tenth/sec until stabilizing at 20.4MB/sec. :confused:

I'm pleased for you, although that doesn't help the rest of us who need to use alternative OSs when we have some serious file transfers in mind.

---

### Post by slumbergod on 2012-04-16
Yup, same old problem dating back a couple of years of Ubuntu use for me. Never been resolved. Bought a new 16Gb drive to archive some multimedia files I need to use frequently. It was so painfully slow transferring 4Gb that I had to go away and have a coffee while I waited.

I'd never change from linux but you'd think after all these years that basic functionality like file transfers would be on par with windoze.

---

### Post by Axis Mann on 2012-11-12
I worked with a developer on this problem, supplying USB trace information back in March of 2012.  I found an old Bug #624510 reported on launchpad that hadn't been resolved ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/624510](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/624510)).  I went round and round with them for about a month before they finally got it fixed for me.  They needed me to provide trace information to figure out my problem.  It took me some research to figure out how to give them what they wanted.  I've since forgotten what I had to do but I learned what I needed from the bug record I think.   I encountered the problem while trying to copy data to an external hard drive over a 2.0  USB port.

---

