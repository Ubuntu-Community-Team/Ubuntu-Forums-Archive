---
title: "HDD diagnosis tools"
date: 2011-11-12
forum: Hardware
---

### Post by Little Blue on 2011-11-12
Hi,

About a month ago I installed a second hard drive into my 10.04 desktop, and whilst there's nothing overtly wrong with it (e.g., it seems to mount ok), looking at the SMART data from Disk Utility it warns me about a few bad sectors.

Specifically a Reallocated Sector Count (1 sector) and a Current Pending Sector Count (13 sectors).

In addition, the self-tests I can run in the disk utility gui (short, extended and conveyance) all report "FAILED (Read)" and benchmarking crashes after a couple minutes with an input/output error. Since I installed the drive both this and the original drive also run a bit hotter in the chassis, which is sort of expected since this is an enclosed space with no cooling on the HDDs directly but this is a surprisingly large jump (the original went from idling at ~35 to 40C, the new drive idles at 45 which is a bit warm for comfort), which I just thought I'd mention in case its also a bad sign.

I really want to try and get to the bottom of this to see if this disk is dying young or something else so I'm wondering if there's anything else I can use to check the health of the drive? I know there's things like fsck for checking file systems but would that also cover the general health of the drive?

Cheers!

---

### Post by Rubi1200 on 2011-11-12
In a situation like this it is best to start preparing for the worst.

Start backing up all important data now.

Also, go to the website of the disk manufacturer and see if they also have a diagnostic tool available for download. Then you can run and compare the results.

In any event, you should keep a very close eye on the status of both those counts.

---

### Post by Johnny3 on 2011-11-12
If is is a WD hard drive you can use their Life Guard to check.
[http://support.wdc.com/product/download.asp?lang=en](http://support.wdc.com/product/download.asp?lang=en)

Or if it is another make try the web site.
Good Luck and God Bless Johnny3 65++

---

### Post by MoreOrLess on 2011-11-12
> the original went from idling at ~35 to 40C, the new drive idles at 45 which is a bit warm for comfort
3.5" disks are usually rated to 65C, so this is nothing to worry about. Also, Google did a study and found that newer disks are more likely to die operating at lower temps. Only after 2-3 years is temp correlated with failure rate.

---

### Post by Little Blue on 2011-11-13
Thanks to you all.

Having a look for tools on the manufacturers website (it was WD so thanks for the link Johnny3) led me to some tools. Booting into windows to run their tools I get the same self-test failures but it only mentions one bad sector, not any pending counts... In any case, the failure of the self-test again is concerning.

> **Rubi1200 said:**
> In a situation like this it is best to start preparing for the worst.
Thinking about it a bit more since I posted the thread, I'm inclined to go with this. Its not even a month old so I'm probably going to take off all the data on it (fortunately I have some spare capacity on some other drives), and hopefully get it replaced by either WD or the retailer...

> **MoreOrLess said:**
> 3.5" disks are usually rated to 65C, so this is nothing to worry about. Also, Google did a study and found that newer disks are more likely to die operating at lower temps. Only after 2-3 years is temp correlated with failure rate.
The disk specs says its rated up to 60C. I might be overreacting but idling near 45 concerns me, and I haven't even put it under any great load yet...

---

