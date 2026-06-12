---
title: "Question: Running Ubuntu w/ an SSD for a Laptop"
date: 2017-01-10
forum: Hardware
---

### Post by mareeks22 on 2017-01-10
Hey Gang,

My name is Matt and I'm a new Ubuntu user.  So far I'm trying it out and I love it.  So I've decided to make it my primary OS.  Before I pose the question let me give all of you some background into my situation.  On 1/1/17 my hard drive crashed.  I was running Windows 8.1 and to my dismay I discovered I'd lost my OS key and would have to re-buy Windows (lame).  So I began looking into a new OS and a new hard-drive.  Long story short.  I decided to run an SSD w/ Ubuntu (cool).  However; I've learned that some SSD's have trouble running Ubuntu.  

So here's my question:  Can I run Ubuntu 16.04.1 LTS with a SanDisk PLUS 120GB SSD (SATA III MLC)

My laptop is a: Toshiba Satellite.  Model #: C55D-B5310

Please let me know what you think.

---

### Post by oldfred on 2017-01-10
Some SSD comparisons:
[http://www.phoronix.com/scan.php?page=article&item=crucial-mx300-525&num=1](http://www.phoronix.com/scan.php?page=article&item=crucial-mx300-525&num=1)

I would think any SSD should work. Just make sure same physical connections, probably standard SATA.

       Toshiba Satellite C55-C5241  Windows vs. Ubuntu
[http://www.phoronix.com/scan.php?page=article&item=broadwell-lap-winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=broadwell-lap-winlin&num=1)
Some possibly similar Toshibas, newer Ubuntu should be easier than those with older Ubuntu

 Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba Satellite P55-A (UEFI) [SOLVED] Trouble installing Xubuntu 14.04 - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186) 
      
 Toshiba C55D-A5163 - Installation of Lubuntu on computer with Windows 8.1 Feb 2015
[http://ubuntuforums.org/showthread.php?t=2267268](http://ubuntuforums.org/showthread.php?t=2267268)
TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T - rEFInd
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)

While not wanting to promote Windows, but if Windows was installed in UEFI mode, you have a product key in your UEFI. You should be able to download the offical copy from Microsoft. Do not use any other site. But if then wanting to dual boot you should get a larger drive. Windows likes to use lots of space.
       
 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

---

### Post by TheFu on 2017-01-10
Regardless of what you choose, you'll want to have a backup.  With Linux, you are much more likely to screw things up and need a setting from last week or last month restored.  Versioned backups. That is mandatory for Linux systems. This isn't to say that you are the only person screwing things on their systems.  Everyone does.

Don't know anything about SSDs - don't trust them. Perhaps after they have 5 more yrs of real-world use? Maybe then?  Actually, I don't trust any single HDD and nobody should.

A few of my chromebooks have m2-SSDs.  Every once in a while, the disks lock up and go read-only.  It has happened on 2 different chromebooks with 3 different SSDs. No idea why. Generally happens after 2 weeks of uptime when there are 20 windows open and I'm in the middle of editing a presentation. I backup, automatically, daily. Can't risk this stuff.  The day before and of the presentation, any changes are immediately pushed to another system every few few minutes.  The first hint of any issue is that cmds start failing because they can't write temp-files anywhere.  Can't reboot. Can't shutdown. Both those things require write to the file system.  BRS is the only answer. Eventually, those disks won't come out of the read-only funk. That is my expectation.  All of the SSDs have under a year of use.  Hence, why I don't trust them.

---

### Post by sudodus on 2017-01-10
I have a few SSDs (one Sandisk Ultra Plus), and I've had them for some years now. They are all running well, I think they are as reliable as HDDs nowadays. At least if you take into account that SSDs are not sensitive to mechanical shock.

A friend of mine dropped his laptop to the floor a couple of months ago, and the HDD crashed (physically). He has an SSD now.

---

### Post by efflandt on 2017-01-11
I have tested both an ancient Intel 80 GB SSD and more recent 512 GB mSATA SSD card (Crucial M550) in a 2.5" SATA adapter and both worked fine running Ubuntu (as far back as 11.04 for the 80 GB) in an old Toshiba laptop from 2006 and a newer Toshiba laptop from around 2009-2011 (borrowed temporarily to update Win7 for the owner) without any issues running Ubuntu, and the old laptop uses a SATA1 controller (the mSATA is SATA3, but works fine on SATA1). So I would think that most any SATA SSD would work. I had no trouble running 64-bit Ubuntu 16.04 on either drive on either of those older Toshiba laptops.

---

