---
title: "Main Partition unaccessible after update -- is there hope?"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by g2devi on 2009-02-22
I'm hoping someone can provide direction on what I can do since at this stage it appears I've lost my partition and my last backup is 5 months old.

I recently updated Ubuntu 8.10 with the most recent update. It failed part way (updated KDE4) and when I retried, it asked for a dist-upgrade. No problem I did and it succeeded. 

However, when I rebooted I was greeted with this **GRUB error 17**.

I tried booting from an Ubuntu 8.10 live CD. It took over 15 minutes to start up but it finally did. I couldn't mount /dev/sda2 (the partition where my OS is installed) using ext3. I looked at "dmesg | tail" as instructed and found that it reported several copies of lines like the following:
[INDENT][B][   14.436979] ata1: EH complete
[   14.437073] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   14.437090] sd 0:0:0:0: [sda] Write Protect is off
[   14.437093] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.437119] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.834392] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   22.834397] ata1.00: irq_stat 0x40000008
[   22.834406] ata1.00: cmd 60/20:00:cd:2f:03/00:00:00:00:00/40 tag 0 ncq 16384 in
[   22.834408]          res 51/40:00:cd:2f:03/95:00:00:00:00/40 Emask 0x409 (media error) <F>
[   22.834413] ata1.00: status: { DRDY ERR }
[   22.834417] ata1.00: error: { UNC }
[   22.848839] ata1.00: configured for UDMA/133
[/B][/INDENT]

I don't know how to interpret this, but it looks bad. Does anyone have any ideas what it means or what could cause it?

When I run gparted it freezes.

I used "sudo fdisk /dev/sda" and after a minute, it reported:
[INDENT][B]Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391    6  FAT16
/dev/sda2    *         14       38149   306327420   83  Linux
/dev/sda3           38150       38913     6136830    f  W95 Ext'd (LBA)
/dev/sda5           38907       38913       56196   dd  Unknown
/dev/sda6           38150       38906     6080539+  82  Linux swap / Solaris
[/B][/INDENT]

I was able to mount /dev/sda1.

I don't know what more I can do to diagnose what's wrong.

If I had to take a guess, I think that since I can see that partition table and can read partition 1, the disk has not malfunctioned. This leaves three possible options:
(1) there is a bad sector in my OS file system
(2) the start of sda2 moved so it's no longer pointing to the start of the OS file system.
(3) somehow my file system got scrambled

I have no idea which happened. Can someone help point me to a solution? I've been struggling this for two days and I really need my PC.

If there's no hope but to try and re-install:(, I'd greatly appreciate if there is some way to recover my files to an external hard drive.

I'll welcome any and all suggestions since I have no idea what to do next.
Thanks in advance.

---

### Post by pytheas22 on 2009-02-22
What is on /dev/sda1?  If it's /home, then your simplest solution would probably be to grab your personal files from there, then reinstall Ubuntu.  I can provide specific instructions on that if you need.

Otherwise, some quick googling (check out this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920")) suggested that an older version of Ubuntu might boot, because in some cases the lines you're seeing in dmesg seem to be related to issues with SATA drivers introduced in more recent kernels.  Could you burn a live CD of Ubuntu 6.06 and see if it works, at least to let you save your files?  Some people also reported having better luck with Red Hat or Debian; you may want to consider that.

It may also help to open up your computer (if it's a desktop) and reseat the hard drive cables, or try plugging it into a different port on the motherboard (if you have more than one).

If you have another computer available, it may work to stick the hard drive in there in order to rescue your files, because from what I gather this error message has to do with your motherboard more than the drive itself--so you may have luck in a different machine.

In a worst case, it's possible to use something like testdisk to recover most of your files, but hopefully it won't come to that.  For the time being, please try the suggestions above and let us know.

---

### Post by g2devi on 2009-02-23
Thanks for your thorough reply. I looked at the bug report and it does seem similar. I tried the suggested fix of adding "all_generic_ide hpet=disable" to the kernel but it doesn't seem to have an effect. Unfortunately, the thread was closed off prematurely.

What google search did you use? I couldn't find this entry when I looked and if there is a better search criteria, I might be able to dig through them to find a fix.

> What is on /dev/sda1?
Unfortunately, it's only the "Dell Utility partition" which comes standard on their 1720 laptops. It contains diagnostic tools which I can't access since GRUB dies with "error 17". But I'm not too concerned about booting to it since from previous use it seems to provide useless diagnosis tools.

> If it's /home, then your simplest solution would probably be to grab your personal files from there, then reinstall Ubuntu.

That's my goal at the moment. I'd be overjoyed if I could restore my system back to the way it was, but I've all but given up trying to fix the problem and am more focused on recovering what I've lost. Unfortunately, everything is on /dev/sda2 which I can't access. At the moment, I wish I kept my boot, OS, and home on different partitions since that would give me a better chance of either recovering something or booting my computer. But I consciously kept one partition since I can only have one disk on this laptop and since experience tells me that either my OS partition will be too small or too large and I'll run out of space in /home. I'm new to laptops and haven't yet found the best ways to deal with and work around the constraints that don't exist on a desktop.

Anyway, I tried booting several live CDs, such as Ubuntu, Ubuntu recovery remix, system recovery live cd, fedora, gentoo, knoppix, debian live cd, and a few others. Of these, only Ubuntu, Gentoo and Knoppix seem to be able to boot up at all (likely due to the Dell laptop hardware) and only Ubuntu seems to be able to view the partition table. Ubuntu, however takes about 20 minutes to boot due to the ata1 errors described above. It would be nice if there were a way to skip ubuntu checking for ata1 errors so I could reboot faster so I could test more things.

I have an external 10GB USB drive as well as my backup drive (which is several months out of date). I installed Ubuntu on the external drive and am able to use that to aid my diagnosis.
Unfortunately, since I'm dealing with a laptop, I can't open it up and do the hardware checks you suggested. I don't even seem to be able to find the hard disk mentioned at all in the BIOS -- it must be a Dell tech support only "feature".

I've tried using testdisk (it takes several minutes to get from the initial prompt question to the next screen), but it appears but gave up after it appeared to only report partition information.

I looked again at online documentation and it appears that it should provide a way of listing the files on the disk, so I might have stopped too soon. I'll look at it again when I get back home and see how far it get me. In the mean time, this appears to be my only hope, unless you or someone else has other ideas.

Thanks again for your help. You've given me at least a little hope that I might be able to at least recover something.

---

### Post by pytheas22 on 2009-02-23
Sorry to hear that you're still not having much luck.

testdisk shouldn't be hanging between screens.  In this situation, it might make more sense to use [ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html"), which will make a copy of your current partition and try to fix any disk-read errors automatically.  There's a decent guide on using ddrescue [here]("http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html").  It's pretty straight-forward as long as you're comfortable with the command line, but if not, let me know.

I would boot to a live CD or your external drive, install ddrescue (apt-get install ddrescue) and use it to copy /dev/sda2 over to your external backup drive.  After the copy is finished, try to mount the image file.  Hopefully it will mount no problem, and you'll be able to recover your data (and even ghost the image back onto a working hard drive if you want, in order to get your old system back).

Please let me know if this helps.  If not, we can try some other things, although the fact that even testdisk won't run has me worried.

> 
What google search did you use? I couldn't find this entry when I looked and if there is a better search criteria, I might be able to dig through them to find a fix.

I just googled some of the lines from the dmesg output that you posted in your first post.  But I didn't search exhaustively; you would probably find more useful stuff if you spent more time on it.

---

### Post by g2devi on 2009-03-04
Thanks for all your help.

Just a followup. ddrescue succeeded in making a copy. There were only 3 errors, a total of 700K size. I tried using foremost and testdisk but neither were able to extract anything. I tried photorec. It seemed like it was suceeding, but all it succeeded in doing was creating several randomly named MP3 files which seemed to be split into many parts. It wasn't too useful. In the end, it seemed like the 3 errors were in the most critical part of the file system, so that no tool would either recognize the partition as an ext3 partition nor be able to see the directory tree.

I finally gave up and reinstalled and copied back my last backup information (which was before my last OS upgrade) and information on my IPod (which captured some newer information, but it wasn't complete since it couldn't hold all my audio books). It'll take a while to organize things back to the way things were and try to rebuild all that was lost, but at least I've moved on. When I've finished setting things up, I'll make another backup.

The only upside in all of this is that I've now partitioned my install into separate: /boot, / (root), and /home directories. This should greatly reduce the risk that a single disk error can mess everything up.

Anyone reading this message, take heed to make regular backups (more frequent than once every 6 months), and if possible, break you disk up into several partitions. Getting an external USB bootable drive with Ubuntu is also a life-saver. A boot able CD is nice, but not enough if you need to do anything fancy or need to try out tools like foremost, ddrescue, and friends.

---

### Post by pytheas22 on 2009-03-04
Thanks for the follow-up.  Sorry to hear you weren't able to recover your data...

---

