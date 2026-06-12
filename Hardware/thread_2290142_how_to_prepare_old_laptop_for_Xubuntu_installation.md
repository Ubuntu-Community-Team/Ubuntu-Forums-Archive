---
title: "how to prepare old laptop for Xubuntu installation?"
date: 2015-08-10
forum: Hardware
---

### Post by ardouronerous on 2015-08-10
My father's laptop, Dell Inspiron E1505 with Windows XP preinstalled, the hard drive is about to give up I think, and my father doesn't want to purchase a new laptop, too expensive, and I convinced my father that if and when his hard drive finally gives up, to install Linux on it, preferably Xubuntu, because I'm using it on my main desktop and I have experience in using it, I started using it since 2012, starting with 12.04 LTS and now I'm using 14.04 LTS, I like to stick to the LTS versions.

The laptop was bought in 2006 and it's a fairly strong laptop to survive almost 10 years, the only problems with it is the onboard speakers are busted, but I fixed it by purchasing USB speakers, the hard drive has 200+ bad sectors, so I'll be buying a new hard drive, aside from busted speakers and imminent hard drive failure, I see no other problems on it, no issues on the video card, WIFI card and the monitor is still crystal clear.

I have no experience in installing Xubuntu on an old computer, so this is why I'm asking, is there anything I should do to prepare the laptop for Xubuntu installation?

Dell Inspiron E1505 specs
CPU     1.66-GHz Intel Core Duo T2300 processor
Operating System     MS Windows XP Media Center
RAM     1GB
RAM Upgradable to     2GB
Hard Drive Size     80GB
Hard Drive Speed     5,400rpm
Display Size     15.4
Native Resolution     1680x1050
Optical Drive     DVD+R DL
Optical Drive Speed     8X
Graphics Card     ATI Mobility Radeon X1300
Video Memory     128MB
Wi-Fi     802.11g
Ports (excluding USB)     S-Video
Ports (excluding USB)     Modem
Ports (excluding USB)     Microphone
Ports (excluding USB)     Headphone
Ports (excluding USB)     Firewire
Ports (excluding USB)     Ethernet
Ports (excluding USB)     VGA
USB Ports     4
Card Slots     5-1 card reader
Card Slots     ExpressCard
Size     14 x 10.4 x 1.4
Weight     6.8 pounds

[LIST]
[/LIST]

---

### Post by Bucky Ball on 2015-08-10
Not really, apart from putting another 1Gb of RAM in there. Not sure how your experience will be with 1Gb only. It should run but not sure how well. 

Apart from the, are you are intending to install Xubuntu only? If this is the case, create the install media, boot from it and install. That is it. 

If you are installing a dual-boot, Windows first, then Ubuntu. As it is an old machine you have no EFI boot mode to mess with, but you have got limitations. I suggest you sit down with a beverage and pen and paper to plan this.

In short, with a legacy mode install you are limited to four partitions per physical hard drive, BUT, there is a way around this.

Windows must live on a primary partition, the first on the drive is best, but Ubuntu is happy to live on a logical partition inside an extended one. So, install Windows onto a primary partition then create an extended partition with the rest of the space on the drive and install Ubuntu on logical partitions inside that. An extended partition is like a container into which you can theoretically put as many logical partitions as your hardware will handle. Logical partitions, for all intents and purposes, are just like any regular partition.

This overcomes the four partition limit.

There are many options here and I am presuming Win is in the equation. If not, disregard, but if so, you can put Windows XP on a 20Gb partition, Xubuntu on a 20Gb logical partition and use the rest of the drive as a shared NTFS data partition with symlinks from Win and Ubuntu to the data on it. (I.e. this means that 'Documents' 'Videos' etc. folders live on the data partition and both installs use them. No redundancy and confusion with duplicate files.) 

Anyway, there are many options. Give us more specifics re. dual-boot or just Xubuntu. If the latter, easy. But no, you don't need to prepare the machine. Put the other hard drive in and off you go. Good luck. :)

PS: You might need to do a little tweaking to get various hardware to work once installed, but not much you can do prior to install. Run from the live media and see how it all looks.

---

### Post by ardouronerous on 2015-08-10
Thanks for all that info!:D
The plan is to install Xubuntu only.

My father has seen me using Virtualbox to use Windows XP on my Xubuntu desktop, if he wanted to use Windows XP for whatever reason, is using Virtualbox Windows XP an option for the specs of the laptop?

---

### Post by kerry_s on 2015-08-10
i agree, upgrade the ram to the max & grab a ssd drive instead of regular drive when you replace.

---

### Post by ardouronerous on 2015-08-10
Thanks, I have been considering upgrading the RAM after reading Bucky's post:D

Are you sure about the SSD drive? I've heard horror stories of loads of failures and data loss from users of SSDs.

---

### Post by weatherman2 on 2015-08-10
I have had a couple of these E1505 laptops.  A relative is still using one of them, with Ubuntu 12.04 on it.  A friend has another one with Ubuntu 14.04 on it.  Both have the RAM upgraded to 2GB.  Both also have the wireless cards upgraded to an Intel 5100 802.11n card (full size), in case you want faster wireless (very easy to upgrade the card - maybe $10 USD on eBay for a full height 5100 card - don't get the IBM/Lenovo/HP version though.)  You may have issues with the Broadcom wireless card if your E1505 has that card in it, but you can probably find the recipe to make it work.

Some versions of the E1505 have a dedicated graphics, others have integrated graphics.  Looks like you have the dedicated graphics, you will probably want to install the Additional Driver after installation for your Radeon card.

I didn't bother with Xubuntu - I stuck with Ubuntu but on one of them used Gnome Fallback (Flashback) to get "old-style Gnome" instead of Unity.  My friend is still using Unity on his - seems to work well enough.  He also upgraded his E1505 hard drive to an SSD.  Of course, if you are familiar with Xubuntu, go for it, should work great.

Yes, these old E1505s can still work fine with Linux many years later, if you take care of them.

For installation, just let the Ubuntu installer erase the hard drive and use all of it.  I think the E1505 is only SATA I (1.5Gbps) but an SSD like my friend added might be worth doing instead of a hard drive to replace the dying hard drive.  Super easy hard drive to replace - should take about 2 minutes, tops, four screws.

---

### Post by Bucky Ball on 2015-08-10
Then those SSD stories are probably old. They run fine and technology moves fast. RAM is the issue here in any case. SSD would speed it up, yes, but nothing to do with whether Xubuntu is going to give a worthwhile computing experience. If it falls over at the processor and/or RAM, the disk is irrelevant. ;)

Even with 2Gb of RAM you would be struggling to run a virtual machine on that box. As you know, you need to split the installed RAM and that would mean 1Gb for Xubuntu and 1Gb for XP. You could try, no idea of the results, but don't expect much.

---

### Post by ardouronerous on 2015-08-10
But putting in a regular SATA 2.5-inch Hard drive is okay right? I'd rather stick with tried-and-true technology, case in point, the hard drive from the laptop is a Western Digital, it has never been replaced, it's the original from 2006, so it lasted almost 10 years, and it's still running, with 200+ bad sectors of course lol, but still 10 years is still impressive.

---

### Post by weatherman2 on 2015-08-10
The E1505 uses a standard 9.5mm 2.5" SATA laptop hard drive.  Many newer 2.5" SSD and HDDs will be thinner 7mm.  That should fit just fine - the E1505 drive has a tiny plastic bracket screwed onto the end to make it flush with the side of the laptop and it just slides into the slot.  It will be a tad thinner that's all.

---

### Post by weatherman2 on 2015-08-10
SSD to me is certainly "tried and true" technology that has been around for a long time.  (The flash technology itself has been around for 30+ years.)  I would feel more worried about the reliability of a hard drive with moving parts, having replaced too many that failed.  If you want to read about the stress tests done on SSD drives, do some web searches.  In one recent test, a tester put several different drives through tests designed to "kill" them (constant writes) and they lasted longer than the manufacturer specs in every case, longer than expected, before failure.  No doubt, any SSD you install in an E1505 is likely to last longer than the E1505 itself, which is getting pretty old.

I don't consider the fact that a ten year old hard drive is still going but with 200 failed sectors to be a big achievement - I certainly have seen other drives that have lasted longer than that without any failed sectors.

---

### Post by mörgæs on 2015-08-10
There are many unknowns in the equation. Why don't you install Xubuntu on the hardware as-is to see how it performs? 

When you have some observations it's easier to give advice.

---

### Post by Bucky Ball on 2015-08-10
SSDs are tried and true technology, but I agree with the above. Install on what you have and observe. :)

---

### Post by weatherman2 on 2015-08-10
> **Bucky Ball said:**
> SSDs are tried and true technology, but I agree with the above. Install on what you have and observe. :)

He has a hard drive with 200+ bad sectors, so he needs to replace it with something.  If those are really "bad sectors" (pending sectors, not readable), I wouldn't bother installing anything on it myself.

---

### Post by ardouronerous on 2015-08-10
The hard drive has 241 bad sectors, I just ran Speccy on it.

I can't really do anything on the laptop right now though, other than checking the specs and such, my father has this 'use it up and wear it out' mentality lol, that why we agreed on, if and when his hard drive fails, that's when we'll buy a new one and install Xubuntu.

Thanks for all the advice:D

---

### Post by weatherman2 on 2015-08-11
If a bad sector appears in a data file - picture, document, whatever - that file will probably get corrupted and be not recoverable.

Also, if a bad sector shows up in an operating system file, the OS may freeze or get very slow, in an unpredictable way.  It may not be obvious that your hard drive is causing such a problem.

As long as your father doesn't mind putting up with a potentially slow, unreliable, flaky laptop and losing his data files occasionally, then keep using this failed hard drive.  Some people use a computer only for web browsing, so I suppose you could get away with using a failed hard drive for a long time this way.  I wouldn't waste my time, though, personally.

---

### Post by ardouronerous on 2015-08-11
The laptop does freeze sometimes lol, my father uses his laptop only for web browsing and email.

That's why I practice backing up important data, like legal docs, family photos and videos, music, etc, on DVDs and USB flash drive.

---

### Post by weatherman2 on 2015-08-11
I hope are using some sort of incremental backup - otherwise, how do you know you aren't overwriting a good copy of the file with a corrupted one from the hard drive?

---

### Post by ardouronerous on 2015-08-11
Actually, we don't use the laptop for anything other than web browsing, my main Xubuntu desktop is what we use for everything else, and so everything backed up is from my Xubuntu desktop.

---

