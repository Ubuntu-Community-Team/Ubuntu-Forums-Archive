---
title: "SSD read benchmark performance degrading / worsening"
date: 2014-03-13
forum: Hardware
---

### Post by sgarman on 2014-03-13
Hello,

I have an SSD that's only a few months old, and after getting an intuitive sense that the disk was acting slow (e.g, Firefox was taking a lot longer to start), I ran the Disks benchmarking utility. 

Sure enough, I'm seeing very inconsistent read speeds from this device:

[ATTACH=CONFIG]251089[/ATTACH]

I'm very certain that when I first installed Ubuntu onto this drive this same benchmark ran at a very consistent 530-540 MB/sec. I have other SSDs which I've been using for years which have very consistent read benchmark graphs - there's barely a ripple in them. 

What could be the cause for this? The SSD is a Samsung 840 EVO 750 GB running the latest firmware. I am running / on one big partition as ext4 with discard,noatime,nodiratime in my /etc/fstab. The disk is only 30% full and I don't believe has ever been more than 50% full. SMART data looks fine, and it passed a short self-test without issues. 

Suggestions on further tests to try or possible causes for this behavior are appreciated.

Thanks,

Scott

---

### Post by tgalati4 on 2014-03-13
Because of the large size, it probably has a caching controller that has a fast SSD and slower flash storage.  Under most workloads, you will get fast speeds.  Some workloads will cause it to hit the slower flash.  It's possible that your disk has developed a problem and might be due for a warranty replacement.  Does Samsung have a diagnostic utility that you can burn to CD?  If it passes that, then you might not be able to get a warranty return.

Slow firefox could simply be a profile problem.  Delete your cache or delete your entire firefox profile and start fresh.

---

### Post by sgarman on 2014-03-13
tgalati4, thanks for the quick reply. Samsung does have a "Magician" app that is used for diagnostics and tweaking performance, but it only runs under Windows (and I'm not dual-booting). I suppose around the time that 14.04 comes out I could reinstall Windows and run this tool to see what it says. 

The disk is definitely feeling slower all around - I use several profiles for firefox and they're all acting more sluggish than usual. The system overall feels like it's not nearly as snappy as before. 

To compare, here is the same read benchmark run on a (slower) Intel SSD on another system I use:

[ATTACH=CONFIG]251090[/ATTACH]

The performance is very consistent, and has been like this for more than a year. 

Scott

---

### Post by tgalati4 on 2014-03-13
Do a web search on your specific Samsung model.  Perhaps others are having similar issues.  I think it is a controller/wear-leveler issue, it works until it hits a "degraded" area and that slows it down.  I'm not sure what technology is used in the larger capacity SSD's, but I would guess that a large disk has a greater chance of bad sectors and that would cause the controller to work extra hard.

Without the ability to run Samsung's diagnostics, you will not know if it passes Samsung's basic tests.  If it fails, then you can get an RMA pretty easily.  Because, you know when you call them, that is the first hoop they will make you jump through.

---

### Post by sgarman on 2014-03-14
On the advice of a sysadmin friend of mine, I backed up all my files, issued an ATA secure erase command to the drive, and restored my data and bootloader. Now things are back to normal:

[ATTACH=CONFIG]251156[/ATTACH]

I have the feeling that what caused the degradation in performance were a handful of very long builds of embedded Linux images I had been doing with the Yocto Project. I'm going to keep a close eye on performance from now on and note when it starts to degrade to be certain. 

FWIW, here is a guide on issuing the ATA secure erase command using an Ubuntu install image:

[https://mackonsti.wordpress.com/2011/11/22/ssd-secure-erase-ata-command/](https://mackonsti.wordpress.com/2011/11/22/ssd-secure-erase-ata-command/)

I'll mark this thread as solved. 

Scott

---

### Post by sgarman on 2014-11-04
I just wanted to follow-up here and note that the cause of the problem was actually a highly publicized bug in Samsung's firmware for the 840 EVO series drives. Samsung has since released a fix for it that permanently resolves the problem. 

[http://techreport.com/review/27212/samsung-840-evo-update-fixes-slow-reads-with-old-data](http://techreport.com/review/27212/samsung-840-evo-update-fixes-slow-reads-with-old-data)

Scott

---

