---
title: "Problems installing to SATA hard drives--related to several threads!"
date: 2006-01-17
forum: Hardware &amp; Laptops
---

### Post by gomaaa on 2006-01-17
I have a Sony VAIO VGN-S580 laptop with an 80GB Serial ATA (SATA) hard drive.  

Around Christmastime, I tried to install Ubuntu (actually Kubuntu) and the process seemed to run smoothly.  (Okay, I had a TERRIBLE time getting a good CD burned, but that's a separate issue.)  However, upon reboot from the installation phase, the computer seems to boot cleanly up to a point and then gives me a time out error and hangs.  Every subsequent attempt to boot, however, hangs EARLIER, just when the computer attempts to mount the / filesystem.

I have partitioned the disk thusly:

/boot -- 50MB
/windows -- 15GB
/            -- 15GB
swap      -- a little bit
/shared   -- the rest in a fat32 data partition

So while it seems to access the /boot partion fine, the / partition is not being accessed correctly.  While it could be that my odd partitioning scheme is the problem, I have managed to correctly install FC3 using the same setup.  

I was thoroughly confused by the whole problem until it was suggested to me that the hard drive may not be fully compatible with Ubuntu.  A search led me to this site which exlpains the problem nicely, but offers no practical solutions for my situation:

[http://linuxmafia.com/faq/Hardware/sata.html]("http://linuxmafia.com/faq/Hardware/sata.html")

Basically, the support for SATA hard drives varies widely and depends not only on how recent the distribution is, but also on whether the distribution attempts to make use of the full capabilities of the hard drive (remember that FC3 works when Ubuntu 5.10 doesn't!).  It will also vary widely depending on what precise SATA chipset you actually have.  

Further searches revealed that this may be the core of a variety of apparently unrelated problems all involving SATA hard drives, but resulting in different symptoms:

[]("http://www.ubuntuforums.org/showthread.php?t=117629&highlight=sata")

[http://ubuntuforums.org/showthread.php?t=75385]("http://ubuntuforums.org/showthread.php?t=75385")

[http://www.ubuntuforums.org/showthread.php?t=117412&highlight=sata]("http://www.ubuntuforums.org/showthread.php?t=117412&highlight=sata")


[http://www.ubuntuforums.org/showthread.php?t=75430&highlight=sata]("http://www.ubuntuforums.org/showthread.php?t=75430&highlight=sata")


I am trying to collect these problems in order to generate some interest and hopefully find some kind of general solution.

I am thinking to trying to install Debian, because I believe that will give me more control over the install procedure so that I can make SURE that I have the correct drivers for my hard drive.  However, this will be potentially very difficult and I the whole reason I chose Ubuntu was to try and avoid these issues!

Thanks!

gomaaa

---

### Post by Azion on 2006-01-17
There are no drivers for hard drives.
Are you using any RAID setups, or controllers not on your motherboard?

---

### Post by youngj on 2006-01-26
Hi,
I'm facing a similar problem. I use ASUS mother board with VIA drivers, the hard disk is Seagate 80 GB SATA enabled. Now the surprising thing is during installation I get an option "Manuall edit Partition Table" that is it. nothing else. So looks like no hard disk is recognized. Strange, I tried this with FC4 and Mandriva 2006 too, there it clearly says that no hard disk is found. I sometimes wonder is the Linux community really good. This problem has been there around for quite sometime, but no solution is given, whereas my Windows XP installation works perfectly, no glitch. So what motivates me to use Ubuntu(Linux as a whole) when I can't get it up and running.

---

### Post by timas on 2006-03-16
I have/had the same issues.. I have a Dell Dimension 5100 with a 140gb orso SATA drive and a DVD-RW connected to the PATA controller... After searching for info on the internet I found this forum and some suggestions to try noapic and nolapic.. I tried them out..  "install noapic" makes it not work at all.. "install noapic nolapic" makes the install work but I have absolutely no way to connect to my drive it seems.. I couldn't get past partitioning my drive, the partition list was empty..

The real tricky one appears when I do "install nolapic" the installer finds my SATA drive like this but it halts on a IRQ issue with my USB..

My final solution was to install with noapic nolapic and just connect a (older) 60gb ATA drive.. needless to say, this is not a fix :P    

Any ideas?

Edit: Forgot to mention I had to switch SATA modes to 'combined' to support "legacy OSes" as they put it in my BIOS, I haven't tried booting into XP after making that switch yet.. chances are the SATA controller has to run in 'normal' mode to work for XP.. Truth to be told, I'd prefer (K)ubuntu to be able to work with my SATA drive in normal mode..

---

