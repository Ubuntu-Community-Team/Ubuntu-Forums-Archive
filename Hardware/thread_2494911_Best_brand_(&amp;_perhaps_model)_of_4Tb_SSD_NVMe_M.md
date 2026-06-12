---
title: "Best brand (&amp; perhaps model) of 4Tb SSD NVMe M.2 brand for Ubuntu 22.04 compatibility"
date: 2024-01-30
forum: Hardware
---

### Post by xznyang on 2024-01-30
Hi there,


I have bought an Asus laptop (i7 with 16Gb) that comes with Windows 11 installed in a 1Tb SSD (NVMe M.2) and I want to install Ubuntu for a dual-boot setup. Since the motherboard has space for a second SSD (NVMe M.2), my plan is to buy a 4Tb model to put there and install Ubuntu 22.04.

However, because I have owned and worked with multiple laptops using multiple versions of Ubuntu in the last years, I am well aware of the many SSD firmware compatibility issues that may raise problems under Ubuntu (the canonical example being Suspension / Hibernation). Therefore, I am here just to ask your opinions on which brand / models of SSD have had, in your experience, the best firmware support / compatibility for installing Ubuntu in a laptop.

Many thanks!

---

### Post by MAFoElffen on 2024-01-30
I have never gone wrong with Samsung SSD's and NVMe's. You pay a bit more, but they have proven their worth to me again and again. I look for sales on them at Amazon.

Note: 

In my laptop:
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ lsblk -e7 -o model | sed '/^$/d'
MODEL
Samsung SSD 870 QVO 2TB
Samsung SSD 870 QVO 2TB
Dogfish SSD 2TB

```
The first is in the traditional HDD slot. The second is in a SATA drive caddy that replaced the optical drive. The third is an mSATA card in the slot that used to have WWAN card. I couldn't find an mSATA made by Samsung and larger than 1TB...

---

### Post by #&amp;thj^% on 2024-01-30
I just have to second that:
```
lsblk -e7 -o model | sed '/^$/d'
MODEL
Sabrent
SN570 500GB
Ultra
STORAGE DEVICE
STORAGE DEVICE
PNY CS2311 1TB SSD
**Samsung SSD 980 PRO 1TB**
```
I've had an opportunity to use multiple SSD's and by far the Samsung smokes them all.

---

### Post by MAFoElffen on 2024-01-30
To add to that:

My Workstation:
```

mafoelffen@msi-ubuntu:~$ lsblk -e7 -o model | sed '/^$/d'
MODEL
WDC WD40EZAZ-00S
Samsung SSD 870
WDC WD40EZRZ-22G
WDC WD40EZAZ-00S
ST5000DM000-1FK1
HL-DT-ST DVDRAM GH24LS70
Samsung SSD 990 PRO 2TB
Samsung SSD 990 PRO 2TB
Samsung SSD 980 PRO 2TB
PCIe SSD
PCIe SSD

```
and my Server
```

mafoelffen@Mikes-B460M:~$ lsblk -e7 -o model | sed '/^$/d'
MODEL
Samsung SSD 870 EVO 2TB
Samsung SSD 870 EVO 2TB
Samsung SSD 870 EVO 2TB
Crucial_CT512MX100SSD1
Samsung SSD 870 EVO 2TB
Samsung SSD 870 EVO 2TB
Samsung SSD 970 EVO Plus 2TB
WD Blue SN570 1TB
Samsung SSD 970 EVO Plus 2TB
Samsung SSD 970 EVO Plus 2TB
Samsung SSD 970 EVO Plus 2TB
Samsung SSD 970 EVO Plus 2TB
Samsung SSD 970 EVO 2TB

```

---

### Post by xznyang on 2024-01-31
Thanks for your replies, they were indeed helpful and encouraging for me to invest a bit more on a Samsung. Out of curiosity, in your laptops have you ever tried either or both:

1- using Suspend / Hibernate?
2- having Ubuntu installed alongside Windows?

---

### Post by oldfred on 2024-01-31
I do not think I had a choice of brands with my Dell laptop.
But hibernation is not recommended. With SSD, you boot almost as fast from cold boot. And often hibernation has issues.
Linux is not Windows which needs hibernation/fast startup, fast boot in UEFI (which once configured you can use with Ubuntu) and SSD  to seem like it is booting faster.

My Dell was dual boot Windows 11 and Ubuntu 22.04. When Dell put new motherboard in, I think they forgot to reset motherboard for Windows Product key. Could not repair using any Windows tools. Only fix was a Dell total recovery which made system just like when purchased. Lost Windows changes & all of my Kubuntu install. But Linux install was a copy of desktop so no issue. 
Also have copy of desktop on external SSD which I also have used with new Dell and very old 2006 Toshiba (BIOS only).

I have only purchased Samsumg & like them. Internal drive & two external SSD in adapters. Two are NVMe & one is older SATA SSD.
One feature of Samsung is that you can download a bootable ISO and update firmware. Its Windows software does not work with Linux, But I prefer ISO anyway.

---

### Post by xznyang on 2024-01-31
> **oldfred said:**
> I do not think I had a choice of brands with my Dell laptop.
But hibernation is not recommended. With SSD, you boot almost as fast from cold boot. And often hibernation has issues.
Linux is not Windows which needs hibernation/fast startup, fast boot in UEFI (which once configured you can use with Ubuntu) and SSD  to seem like it is booting faster.

My Dell was dual boot Windows 11 and Ubuntu 22.04. When Dell put new motherboard in, I think they forgot to reset motherboard for Windows Product key. Could not repair using any Windows tools. Only fix was a Dell total recovery which made system just like when purchased. Lost Windows changes & all of my Kubuntu install. But Linux install was a copy of desktop so no issue. 
Also have copy of desktop on external SSD which I also have used with new Dell and very old 2006 Toshiba (BIOS only).

I have only purchased Samsumg & like them. Internal drive & two external SSD in adapters. Two are NVMe & one is older SATA SSD.
One feature of Samsung is that you can download a bootable ISO and update firmware. Its Windows software does not work with Linux, But I prefer ISO anyway.

Thanks for your input. About Hibernation, I strongly disagree with that common take - Hibernation is helpful not when one wants the boot to happen faster, but when one has lots of things in RAM memory that are time-consuming to put there again (in my case, very time consuming statistical analyses). But that is actually a bit out of topics - your comments on the SSDs were *vert* helpful and I appreciate them! In particular, knowing that firmware in Samsung SSDs can be somewhat easily updated is a gigantic plus for me.

---

### Post by #&amp;thj^% on 2024-02-01
I still agree with oldfred, but it's your choice after all, >>>all we can do offer our wisest suggestions.

More info on wear and tear :[https://www.howtogeek.com/885752/is-hibernating-your-pc-bad-for-your-ssd/](https://www.howtogeek.com/885752/is-hibernating-your-pc-bad-for-your-ssd/)

---

### Post by xznyang on 2024-02-01
> **1fallen said:**
> I still agree with oldfred, but it's your choice after all, >>>all we can do offer our wisest suggestions.

More info on wear and tear :[https://www.howtogeek.com/885752/is-hibernating-your-pc-bad-for-your-ssd/](https://www.howtogeek.com/885752/is-hibernating-your-pc-bad-for-your-ssd/)

I am appreciative of your willingness to help, but have you read the link you sent? It concludes:

> In short, if you like using the hibernate function on your PC, keep using it and don't even think twice about it. The level of wear and tear on an SSD created by writing the hibernation file to the disk every day (or even multiple times per day) is so small that it's inconsequential over the lifespan of the disk." Which is the conclusion of other articles and analyses too.

Also, with all due respect it's not a matter of agreeing or disagreeing. We are not talking about theoreticals, concepts or hypotheses. It's a matter of different use cases and of cost-benefit analyses. I am well aware of the eventual costs of using Hibernation (wear and tear is minimal, like your link claims; but hibernating and waking up consumes consirably more energy and battery than booting) - but also of its benefits in some special cases that are *always* disregarded as if a cost analyses would be enough, instead of a cost-benefit analysis.

Let me be clearer for future reference of those who find this conversation in the future. For the vast majority of users, indeed hibernating to SSD is not a necessity and they are better served by the really fast boots of current laptops (mine, for instance, boots in about 12 seconds). In fact, *by definition* nowadays fast boot will be faster than waking up from hibernation (due to RAM read/write bottlenecks). But some people, including many Statisticians and Data Scientists (like me), **require** hibernating for practical work. It's not a preference:

1- It's simply impracticable to save all work across open software (I am talking about 60+Gb of RAM worth of work in the RAM memory), close all open software, then later reopen the software, make load their respective stuff again to RAM and make sure they are at the stage left last time. Naively, someone could think those take the same amount of time because it's just putting stuff out/into RAM anyways. It's not. Opening software and apps, getting them to be at the analyses stage where they were before and than loading the data that was in RAM again to RAM takes much longer. Believe me, I do this for a living - it takes dramatically longer than hibernating / waking-up.

2- What should one do if their statistical models running for hours didn't finish running before one needs to turn-off the laptop? Just stop the model and start again next time the models that take hours to run just because booting is fast?

But please, don't take that as me being rude or ungrateful for your help - I just think it's important for us all to realize that not everybody's usage is the same. And everything is a cost-benefit analysis, not only a cost analysis.

Again, I sincerely appreciate your and others' concern and willingness to help. And in fact the replies were extremely helpful. Today morning I acquired a SAMSUNG 990 PRO SSD 4TB PCIe 4.0 M.2, installed Ubuntu 23, updated the SSD firmware and after upgrading the kernel to last stable mainline (6.7.2), which has tons of hardware compatibility corrections, both Suspending and Hibernating are working flawlessly!

---

### Post by #&amp;thj^% on 2024-02-01
Well in that usage then I stand corrected....and no I don't look at it like your being rude or ungrateful.

We all have differences in how we see and view our own set-ups, I and I mean just "me" don't want the needless extra wear and tear.
But I can see where your usage it would be something I might consider. And that drive is a very rugged and built for longevity.

And I see your are very capable of making a sound decision. 
Best Regards

---

### Post by MAFoElffen on 2024-02-01
I am both a Windows and Linux Admin who has customers who hire me to do recovery when things go south... I used to teach Computer Science theory, wrapped around how it works and the possibilities that could be. I put more weight on how things work, what I have seen, and what I have had to deal with in the past 35 years of providing computer support. Mostly, it's the same basic concepts applied in differing ways.

Think in this perspective: Windows Desktop's hibernation leaves the filesystem in an opened state. Any time you leave a filesystem in an opened stat, you are at risk of data corruption by just the littlest of things. I get paid very well to recover lost data. If I have my customers turn off Windows fastboot, I can recover the files and filesystem, almost every time.

If not, goodbye. Not much of a chance for success. That is just the facts. I can read the written bytes, but have a hard time putting it together in a logical manner as files that can be used by that system.

Servers do not suspend, nor do they go into hibernation, for good reason.

That is what you risk to shave off a few mere seconds of boot. My boot times for Windows and Linux are near nothing, without hibernation. Laptops and suspend... All the time. No problems.

No conflict. Just the facts. Just an observation. You are free to do whatever you want. 

Always have good backups.

---

### Post by ubfan1 on 2024-09-08
One little point to consider, the PCIx level of each  slot -- they may differ.  No sense spending money on a PCI4 ssd if you only have a PCI3 slot available. I found my MSI GP66 had one PCI3 M.2 slot and one PCI4 M.2 (with a PCI3 SSD installed). Upgraded to a PCI4 Samsung 980Pro (and noticed the speed bump), and used the original SSD to upgrade another machine. I upgraded two seldom used old laptops' HDDs with Silicon Power SSD (300GB/1TB) which were the right price, and recently got two GUDGA SSDs (128GB,256GB) for some USB3 M.2 NVME enclosures.   I did have to tweak a udev rule to allow TRIM to run on USB3 SSD, but now am very happy with the result -- both price and performance.

---

