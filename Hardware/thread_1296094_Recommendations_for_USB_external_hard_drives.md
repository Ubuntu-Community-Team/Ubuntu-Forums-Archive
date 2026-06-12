---
title: "Recommendations for USB external hard drives?"
date: 2009-10-20
forum: Hardware
---

### Post by azumi123 on 2009-10-20
I'm planning on buying an external USB hard drive for a desktop system but I've never actually used one. As with all things they tend to be labelled as "windoze vista required" etc.

My question is - is that just for the backup software that comes with it or are drivers needed to get a hard drive working across USB?

Ideally I'd like to swap it between my desktop system and my UBUNTU laptop to have a 1TB transportable archive. 

Can anyone recommend what makes work with UBUNTU and give me any other tips
or pointers etc? Just general tech stuff - the kids in the local computer
shops don't seem to know anything that isn't printed on the side of the box. 

TIA

Az.

---

### Post by R.Bucky on 2009-10-20
I operate a home web server and have used the 1TB Fanton GreenDrive for a little over a year. It is connected via eSATA. The drive is utilized daily for my server, photos, and music backups. I have had zero complaints with that drive. It operates at around 45C, while my RAID array and other drives are at around 30C. It is a great drive.

---

### Post by Dark_Stang on 2009-10-20
You can reformat the hard drive however you want. Linux will recognize fat32 and ntfs just fine though. I'd recommend fat32 for easiness sake as long as you don't have any files larger than 4GB (fat32's limit).

As far as the actual drives go... I used to recommend Segate. At the time the Segate drives were faster than the Western Digital drives. Now they seem to be pretty much the same. Just stick with a good name. Segate (Maxtor is the same thing now), Western Digital, Hitachi, Toshiba, etc. The only one's I don't recommend are the Western Digital drives that have "WD SmartWare." That is a HUGE pain in the *** to deal with.

Note: eSata is fantastic if you have the ports to run it. Very fast. You can pick up an eSata card for pretty cheap at your local electronics store or online if you want one.

---

### Post by R.Bucky on 2009-10-20
I originally used fat32. However, I found the 4GB filesize restrictive. Do you ever move or store movies (.iso's) or larger archives? Just a thought. 

Agreed on Western Digital. Not too great on external drives...

---

### Post by cascade9 on 2009-10-20
Another vote for 'get eSATA if you can'. Its a lot faster than USB 2.0 and less CPU use. 

As for WD drives, yeah, some of the external boxes WD has put out are..meh. Software problems though, not really any issue with the hardware in the box. 

@ Dark_Stang- I'm pretty sure that the fastest WD drives are faster than seagates current range. WD Caviar blacks are very fast, as are Raptor 2 drives. Not that it will make any difference if you hook up to a USB port, even an old ATA-100 7200 RPM will transfer data faster than USB 2.0 will allow.

---

### Post by sgosnell on 2009-10-20
I have a WD Passport, and I like it pretty well.  It works, and is fast enough for what I use it for.  It comes with Windows backup software, but it's easily deleted if you don't want it.  Linux works with pretty much any hard drive, regardless of what software might be on it, no special drivers needed.  Just plug it in and it works.

---

### Post by Dark_Stang on 2009-10-20
> **cascade9 said:**
> @ Dark_Stang- I'm pretty sure that the fastest WD drives are faster than seagates current range. WD Caviar blacks are very fast, as are Raptor 2 drives. Not that it will make any difference if you hook up to a USB port, even an old ATA-100 7200 RPM will transfer data faster than USB 2.0 will allow.
Oh yeah, the 10,000 rpm drives are definitely faster. MUCH higher failure rates and significantly lower capacities though. The 7200 RPM WD Black's are nice, but I'm pretty sure they are the same speed as the Segate Barracuda's. At the time I was just looking for a standard 7200 rpm desktop drive and the Segate drives back them were a little faster for my dollar at the time.

---

### Post by cascade9 on 2009-10-20
I've never seen any hard data on the 10K raptor (mark 1 or 2)  hdds failure rate..and to be honest I've not sure how you would get that data anyway. If it is an issue, I would guess that its just cause the raptors are consumer level hdds...the SCSI and SAS server boys (and girls) dont have any issues with the 15K drives so its not the technology behind the drives. 

As for Seagate vs WD, the most recent tests I've seen have WD out in front of Seagate by a few %. 

[http://www.xbitlabs.com/articles/storage/display/1tb-14hdd-roundup.html](http://www.xbitlabs.com/articles/storage/display/1tb-14hdd-roundup.html)

Maybe Seagates new drives might drop that lead, who knows?

---

### Post by Dark_Stang on 2009-10-21
> **cascade9 said:**
> I've never seen any hard data on the 10K raptor (mark 1 or 2)  hdds failure rate..and to be honest I've not sure how you would get that data anyway.
Most of my data comes from personal experience. I work for an extremely large computer repair company that operates world wide. I've seen a lot of hard drives get installed and sold. For the few dozen raptor drives that I've seen go out, I'd have to say about 1/4 to 1/3 of those have come back within a year failing. Some were having random issues and would fail extended diagnostics only. Most were total failures. Keep in mind, these are just my personal experiences.

---

### Post by azumi123 on 2009-10-21
Thanks to all for the info and comments.

I need to pin down whether or not these external drives need their
own drivers or not though. Can ayone give a simple yes/no please? 

The reason is one of my systems (my workhorse) uses Win98SE and I need
to use that also if possible. If it needs drivers it won't work. 

If they use drivers then I need a different answer (maybe a PCI eSATA card)
or similar if that would do it but none I found specify win98.

I'm not bothered about reliability issues and so forth. Just anything that
might stop me using them for simple file transfer/archiving on different systems. 

All I want is a big external drive I can (ideally) hot swap between systems.  
(Its nice to know I can use FAT32 - that helps) 

As suggested I've been looking at eSATA and that seems quite a good idea
assuming again I can get it to work with UBUNTU and Win98 and (Until I can get rid) my remaining Vista "thing" "spit" "curse"

I need to buy online so I want to pin down any problems before I start buying.

TIA

Az.

---

### Post by Dark_Stang on 2009-10-21
Windows 98 is probably not goint to work.

---

### Post by sgosnell on 2009-10-21
The drives haven't needed drivers on Ubuntu, but Win98??  I don't remember if that even recognized USB.  That's pretty ancient, and I wouldn't guarantee that anything built in the past few years would work on it.

---

### Post by Ravernomina on 2009-10-21
Also if you have a FireWire Port get Firewire sense it is amazingly fast. But only for USB get USB 2.0 i got a Western Digital Passport and it runs great!. Not a problem yet. Hell i even dropped it when running a few times still works. And Linux can mount it with ease no worries (:

---

### Post by Dark_Stang on 2009-10-21
> **sgosnell said:**
> The drives haven't needed drivers on Ubuntu, but Win98??  I don't remember if that even recognized USB.  That's pretty ancient, and I wouldn't guarantee that anything built in the past few years would work on it.
Some windows 98 machines have USB ports on them (1.0 or 1.1, can't remember which) but I'm almost certain they weren't plug and play.

---

### Post by azumi123 on 2009-10-21
My Win98 system has 8 USB 2.0 ports. 4 on the mobo and 4 on a PCI card.
USB like most things works just fine on Win98. Stop listening to M$ propaganda. (I also have and use 1GB ram before anyone starts on the 512 thing)

Let me try again:

The question is does a USB port need a driver to treat an external drive as a drive - if UBUNTU doesn't is that because it's already built in? 

Do these devices come with a disk of software and is some of that system or driver software of any flavour or is it all just application software?

Az.

---

### Post by cascade9 on 2009-10-21
> **sgosnell said:**
> The drives haven't needed drivers on Ubuntu, but Win98?? I don't remember if that even recognized USB. That's pretty ancient, and I wouldn't guarantee that anything built in the past few years would work on it.
 
 Yep, win98 supports USB. Win95 OSR 2.1 was the 1st MS OS to support USB. They were plug and [play as well (though in those days, it was more 'plug and pray' LOL)  

BTW, on the raptor drives, I have heard that the early versions had some issues with returns, but that was a manufacturing error. I think. I've dealt with less of them than you though (mostly is just been the odd fix-up job for people) and I've built a few computers with them- for other people. From the usage patterns I've seen, the raptor drives get some heavy use, that might have been a factor as well. 
 
> **Ravernomina said:**
> Also if you have a FireWire Port get Firewire sense it is amazingly fast. But only for USB get USB 2.0 i got a Western Digital Passport and it runs great!. Not a problem yet. Hell i even dropped it when running a few times still works. And Linux can mount it with ease no worries (:

Friewire is faster than USB. Well, technically USB 2.0 has more bandwidth, but Firewire is faster. 

I'm not 100% sure on this, but it might be possible to get eSATA going with win98. It wont be 'proper' eSATA cause win98 wont recognise SATA drives, but you might be able to get it going by remapping the SATA drive as IDE. You wont be able to connect/disconnect while running, etc, so I'm not sure if thats even a good option for you. 

> **azumi123 said:**
> My Win98 system has 8 USB 2.0 ports. 4 on the mobo and 4 on a PCI card.
USB like most things works just fine on Win98. Stop listening to M$ propaganda. (I also have and use 1GB ram before anyone starts on the 512 thing)

Let me try again:

The question is does a USB port need a driver to treat an external drive as a drive - if UBUNTU doesn't is that because it's already built in? 

Do these devices come with a disk of software and is some of that system or driver software of any flavour or is it all just application software?

Az.

Gah! 1GB on win98! Well, if its working for you thats good. 

Nah, USB external drives dont need a driver. Or at least I've never had to install one with any OS or drive I've used. The USB ports themselves need a driver, but thats not normally an issue.

Some USB externals come with software, but is normally just for backups.

---

### Post by mysteriousdarren on 2009-10-22
I use a 500gb Western Digital hard drive that works for ext32. I currently have it at ext3 which works good for what i use it for. I am going to buy another 1 tb Western Digital hard drive because of the the good luck.

---

### Post by sgosnell on 2009-10-22
I think, but can't say for sure, that whether a driver is needed for a USB drive depends on whether the OS kernel has support for it, and I have no idea what support is in the Win98 OS.  About all I can suggest is to try a drive on the Win98 machine and see if it works.  Can you try a USB flash drive on it and see if it works?  If so, it should work with a USB HDD.

---

### Post by azumi123 on 2009-11-07
> **cascade9 said:**
> 
...
Gah! 1GB on win98! Well, if its working for you thats good. 
...


Just enable vcache in system.ini Its windows itself that can't go above 512 not applications. I installed 1Gb to play Far Cry because it wouldn't run at all on my system without the extra ram. But win98 itself never needs more than around 200MB anyway. 
Its still the most responsive desktop you can get.

Az.

---

