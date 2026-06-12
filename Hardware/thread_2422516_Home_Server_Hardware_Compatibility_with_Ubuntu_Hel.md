---
title: "Home Server Hardware Compatibility with Ubuntu Help :')"
date: 2019-07-09
forum: Hardware
---

### Post by p0rkb3llys0up on 2019-07-09
Hi! I'm fairly new to this whole process and I finally managed to gather some time and money to try to build a home server as a little project. I wanted to post to see if anyone can help verify if the parts I had in mind would be able to work with Ubuntu? I've been looking everywhere but I haven't found a source that mentions anything with an Intel 300 series-based build. If anyone has any sources that may assist, that would be amazing too! :) 

This is the build I had in mind:

TP-LINK TL-WDN6280
GIGABYTE H370 HD3
Intel Core i3-8100 Coffee Lake 
2x Intel Optane M.2 2280 16GB PCIe NVMe 3.0 x2 Memory Module 
PNY Nvidia Quadro FX 3800 1GB GDDR3 (VCQFX3800-PCIE-PB)
2x G.SKILL Ripjaws V Series 8GB 288-Pin DDR4 SDRAM DDR4 2400 (PC4 19200) Desktop Memory Model F4-2400C15S-8GVR
Rosewill CAPSTONE 550M 550W Modular Power Supply (80 PLUS GOLD Certified)

The reason for the Intel 300 series emphasis is the experimental processes I wanted to work with in regards to Intel Optane, and the hard drives I have lying around would benefit greatly from the boost. Further thanks in advance!

---

### Post by SeijiSensei on 2019-07-09
Why would you need an NVIDIA card on a server? Once it's up and running you're hardly ever going to look at it. 

Linux runs fine on most any collection of PC components. The bigger question you should ask yourself is what you intend to do with this server once it's built. Mine sits in a corner of my office serving up files to client machines and handling email for my domains.

---

### Post by TheFu on 2019-07-09
You understand that there isn't a GUI on "servers".  It is just a text login.  Most of the time, you'll manage the server using ssh from some other workstation.
I've been running lots of Ubuntu Servers over the years.  I probably wouldn't get an i3 CPU when the Ryzen 5 CPUs are cheaper and have 50% more CPU processing.  A Ryzen 1600 is just $80 with 6 cores, 12 threads and 12200 passmarks. An inexpensive AM4 B450 motherboard is about $40.
The Core i3-8100 is just 8000 passmarks.

No way would I use wifi in a server either.

Sounds to me like you really don't want a server, you want a desktop that might run server processes once in a while.

Let's get specific. WHAT processes and services EXACTLY do you want this machine to handle?  
[LIST]
[*]nextcloud
[*]NFS
[*]LDAP/centralized logins
[*]virtual machines
[*]email server
[*]web servers for static or webapps (I'm hosting about 20 speciality websites).
[*]photo galleries
[*]media server(s)
[*]PBX
[/LIST]
I run all of those above and a few more.
A few more ideas are here: [https://github.com/Kickball/awesome-selfhosted](https://github.com/Kickball/awesome-selfhosted)

 My physical machines, which I call "servers", are mainly desktop hardware with Intel NICs and as many cores as I can get within my budget at the time.  They all run a hypervisor for virtual machines, since any business today will mostly be using virtual machines for 99% of their "servers."  The days that 1 server == 1 program have been over since 2005. It is common to run 20-100 virtual machines on 1 physical system.  If you go with containers, that density can be 10x more, but much more complex to maintain.

If you want a server, then AMD is the better choice the last few years. Ryzen changed much. If you want a gaming desktop where the games are limited to 2-4 threads, then intel CPUs are almost always faster. AMD will have 8-16 threads which most games won't use.

As for Optane support, there was a thread here last week with someone trying to make use of it.  It wasn't being recognized, they claimed, as either RAM or disk.  I posted a link for how someone was using Optane, but the poster didn't seem to follow up on it and eventually gave up.

---

### Post by p0rkb3llys0up on 2019-07-09
> **TheFu said:**
> You understand that there isn't a GUI on "servers".  It is just a text login.  Most of the time, you'll manage the server using ssh from some other workstation.
I've been running lots of Ubuntu Servers over the years.  I probably wouldn't get an i3 CPU when the Ryzen 5 CPUs are cheaper and have 50% more CPU processing.  A Ryzen 1600 is just $80 with 6 cores, 12 threads and 12200 passmarks. An inexpensive AM4 B450 motherboard is about $40.
The Core i3-8100 is just 8000 passmarks.

No way would I use wifi in a server either.

Sounds to me like you really don't want a server, you want a desktop that might run server processes once in a while.

Let's get specific. WHAT processes and services EXACTLY do you want this machine to handle?  
[LIST]
[*]nextcloud
[*]NFS
[*]LDAP/centralized logins
[*]virtual machines
[*]email server
[*]web servers for static or webapps (I'm hosting about 20 speciality websites).
[*]photo galleries
[*]media server(s)
[*]PBX
[/LIST]
I run all of those above and a few more.
A few more ideas are here: [https://github.com/Kickball/awesome-selfhosted](https://github.com/Kickball/awesome-selfhosted)

 My physical machines, which I call "servers", are mainly desktop hardware with Intel NICs and as many cores as I can get within my budget at the time.  They all run a hypervisor for virtual machines, since any business today will mostly be using virtual machines for 99% of their "servers."  The days that 1 server == 1 program have been over since 2005. It is common to run 20-100 virtual machines on 1 physical system.  If you go with containers, that density can be 10x more, but much more complex to maintain.

If you want a server, then AMD is the better choice the last few years. Ryzen changed much. If you want a gaming desktop where the games are limited to 2-4 threads, then intel CPUs are almost always faster. AMD will have 8-16 threads which most games won't use.

As for Optane support, there was a thread here last week with someone trying to make use of it.  It wasn't being recognized, they claimed, as either RAM or disk.  I posted a link for how someone was using Optane, but the poster didn't seem to follow up on it and eventually gave up.

Hey! Thanks for giving me an overhaul with everything, as it really cleared up alot of misconceptions I had. From what I gathered from the thread you mentioned with the user asking for help on Intel Optane, I think I'm going to ditch that and focus on the AMD side of things, especially its quite cheap as you mentioned. I had orignally wanted to use Optane as I wanted to use some older hard drives that I wanted to utilize an overall system boost, but I think that may cause more issues with this specific build. 

After looking through all the categories of what processes and services I could utilize with the server, I want to focus more on virtual machines and tinkering with with how they work. I just wanted to say thank you for linking that GitHub link, I'll be doing a bit more digging before I fully commit to the hardware just yet.

---

### Post by TheFu on 2019-07-09
It isn't just any Ryzen that is cheap.  If you aren't a kernel hacker (C programmer), then you probably don't want to get any Ryzen 3xxx series for at least 6 months.  The Ryzen 1600 is cheap because it is 2+ yrs old.  I have a Ryzen 2600 that was used in a build last December. Had I waited even 4 months, it would have cost me 50% less.

Unix servers don't have GUIs.  If you are a point-n-click person, then the learning curve will be high.  It is worth while learning this stuff, but it will be like learning a whole new language.  Nobody knows this stuff when starting out.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good place to start, but only if you really want to know Unix/Linux.  Start with a desktop install (perhaps inside a VM?) and work through each chapter, in order.  Going in order teaches things in the right order. CLI skills build on each other, so learning them in the correct order is the most efficient and prevents basic gaps.

[https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign) is another set of self-hosted stuff.

But don't get too far without setting up daily, automatic, versioned, backups. Backups aren't sexy, but they are necessary.  The more services that you run, the more likely you are to be hacked. With versioned backups, you might be able to figure out what happened and how the bad-guys got in. Without versioned backups, there's no hope.

---

### Post by p0rkb3llys0up on 2019-07-14
> **TheFu said:**
> It isn't just any Ryzen that is cheap.  If you aren't a kernel hacker (C programmer), then you probably don't want to get any Ryzen 3xxx series for at least 6 months.  The Ryzen 1600 is cheap because it is 2+ yrs old.  I have a Ryzen 2600 that was used in a build last December. Had I waited even 4 months, it would have cost me 50% less.

Unix servers don't have GUIs.  If you are a point-n-click person, then the learning curve will be high.  It is worth while learning this stuff, but it will be like learning a whole new language.  Nobody knows this stuff when starting out.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good place to start, but only if you really want to know Unix/Linux.  Start with a desktop install (perhaps inside a VM?) and work through each chapter, in order.  Going in order teaches things in the right order. CLI skills build on each other, so learning them in the correct order is the most efficient and prevents basic gaps.

[https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign) is another set of self-hosted stuff.

But don't get too far without setting up daily, automatic, versioned, backups. Backups aren't sexy, but they are necessary.  The more services that you run, the more likely you are to be hacked. With versioned backups, you might be able to figure out what happened and how the bad-guys got in. Without versioned backups, there's no hope.

I've been doing a lot of digging through the resources you gave and I have a much clearer idea of how to go about the project. Thanks for the resources as they have become really useful!
The one thing I've been confused about is the implementation of hardware RAID vs software RAID. I do know that Linux uses a software RAID based on the mdadm driver, but I've also heard alot of reliability positives of using hardware RAID. Should I just go right along with using the mdadm driver for RAID configuration or should I invest the extra money in a card such as this: [https://www.newegg.com/syba-si-pex40064-sata-iii/p/N82E16816124064?Item=9SIA3XW6T73378](https://www.newegg.com/syba-si-pex40064-sata-iii/p/N82E16816124064?Item=9SIA3XW6T73378) ?

---

### Post by topiv on 2019-07-15
Do not use hardware RAID in Linux. As Linux has great built-in software raid, it offers equal performance to hardware RAID. On the other hand, most hardware RAID cards require vendor kernel module, that is often closed source and cannot be developed / debugged by the Linux community.

If your hardware RAID card ever breaks down, you will need the same model card, with even the same firmware version to be able to recover from the incident and get your data back from the hard drives that form the RAID array.

If you are using software RAID, no matter, what is the hard drive controller, you can just add a new card and attach the disks to it and restart the software array to use your data. If you buy a new motherboard, you can simply move your array to the new HW and start using it without (or with minimal) modification.

You can save the money and create the software RAID array using the existing SATA controller on your motherboard or use an inexpensive SATA controller.

I strongly suggest you to use Linux software RAID. 

Here is a longer explanation, why to use SW RAID:
[https://www.softraid.com/pages/features/software_raid_benefits.html](https://www.softraid.com/pages/features/software_raid_benefits.html)

---

### Post by TheFu on 2019-07-15
There are times to use HW RAID and there are times to use SW-RAID and there are times to use Fake-RAID. 

 RAID solves 3 things and that's it.
[LIST=1]
[*]High Availability
[*]Redundancy
[*]and, with HW-RAID, off load of disk processing to the HBA
[/LIST]
RAID is never a replacement for backups.  
RAID is never a replacement for backups.  
RAID is never a replacement for backups.  
Everyone knows that, but it needs to be said over and over.  There are RAID problems that the only solution for is wiping the RAID set and restoring from backups.  If the backups aren't all working, then we have ZERO business thinking about RAID.

For many home users, RAID is a way to write corrupt or bad data to multiple placed concurrently.

If you are a business looking for the absolute highest performance and have spare controllers on-site with someone skilled enough to replace them, then HW-RAID might make sense.  This would only make sense for medium and large enterprises.  I can't see it making any sense for a home user. Are you really going to purchase 2-3 RAID cards to have spares?   HW-RAID is very inflexible.  In the old days when CPUs weren't as fast as they are today, I bought a reputable HW-RAID card for $450 only to find that the available drivers for it only supported the 2.6.x kernels, nothing newer. Linux had drivers for the card, but not for the HW capabilities.  So my very expensive HBA could have been replaced by a much cheaper LSI JBOD card, which BTW, is still working with current kernels.

FakeRAID is the RAID that motherboards claim to provide.  They are called FakeRAID because really they are just drivers running in the OS that is tied to the specific motherboard HW.  So, you don't get the performance and offloaded throughput from true HW-RAID, but you are still tied to specific hardware.  How is that a win?  There is only 1 situation where an argument that Fake-RAID **Might** make sense - that's if you dual boot with Windows and Linux and must use Fake-RAID in Windows for some reason.  I think fake raid is stupid, but I don't dual boot and if a system is being dual booted, why would HA be needed?  Hint: it isn't.

SW-RAID on any reasonable computer made since 2006 or so is as fast or faster than the other RAID options, but it also retains all the flexibility of software.  I've been using SW-RAID since around 2005 at home.  In those years, I've upgraded the disks from 80G --> 320G --> 2TB.  I've changed from RAID5 to RAID1.  I've moved the array to 3 different systems with 3 different controllers and motherboards. I've moved from Linux release to the next release probably 5 times. Never any worry about drivers.  I've never lost 1 bit of data doing all of that.   SW-RAID is extremely flexible.

I just built a new VM host "server" which it taking  most of the storage from my older VMhost that ran 10-20 VMs concurrently on RAID1 storage and have put 9-19 VMs onto a non-RAID, quality, SSD.  The new VM host is 4+ times faster than the old one too.  If we choose the SSDs correctly, then the redundancy isn't needed. This is for home and I have daily, automatic, versioned, backups.  I don't mind if any of the VMs is unavailable for 4+ hrs.  Of course, if I were inside a business, I'd use SSDs with RAID1.

Regardless of what you decide, please search these forums for issues related to any RAID stuff BEFORE you deploy.  Ensure you have a plan when that issue happens to your computer.  I've had issues with my RAID array early on due to loose SATA connections.  I ended up replacing the cheap SATA cables used inside the array with locking SATA cables - took me about  a year to finally do that after having different disks drop from the array almost monthly.

Anyway, those are my thoughts on RAID.  We are all different.  You do you.

---

### Post by cruzer001 on 2019-07-15
> Anyway, those are my thoughts on RAID. We are all different.

For the home user (which I am) would not LVM have its place as a alternative to RAID.  If ever I needed a simple RAID like setup, I think that would be my choice.

---

### Post by TheFu on 2019-07-15
> **cruzer001 said:**
> For the home user (which I am) would not LVM have its place as a alternative to RAID.  If ever I needed a simple RAID like setup, I think that would be my choice.

Me too.  LVM actually uses the mdadm code for the available RAID modes it supports. Learned that at a storage conference a few years ago.  We can use both, 1 or the other.  I'm unsure if LVM pvmove will work in an LVM+RAID setup.

---

