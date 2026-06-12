---
title: "jetway j7f5 with cx700 chipset doesn't recognize ide hard drive after install"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by zarbon on 2008-03-20
I just got a new Jetway J7F5 motherboard with a VIA C7 1200 Ghz processor and a CX700M chipset.  I tried to use the 7.10 (Gutsy) live CD to install Ubuntu but that fails into a BusyBox shell.  I've turned off the splash and quiet in the boot options but don't seen anything in particular about the IDE hard drive but it goes by very fast and I can't read it all.  At the BusyBox shell there is no /dev/disk directory.

I then successfully installed Ubuntu from the mini CD onto a 2 GB Samsung hard drive.  (I had originally installled on a compact flash card through an ide to CF converter from a memory stick but had the same problem of no hard disk recognized after install and reboot)  The problem is that when I reboot I get a "ALERT! /dev/disk/by-uuid/XXXXXXX does not exist.  Dropping to a shell!"  I've looked into the /dev directory and there is no "disk" directory much less a "by-uuid" directory.  This leads me to believe that Ubuntu for some reason can't recognize the hard drive, which seems odd to me since it did during the install.  The BIOS has no problem recognizing the hard drive either. 

I've seen a bunch of other posts rewlated to the can't find hard disk by-uuid but they don't seem to apply.

 I checked into [http://ubuntuforums.org/showthread.php?t=483579](http://ubuntuforums.org/showthread.php?t=483579) which said that the problem was a master/slave jumper in the wrong position.  I even tried changing the position of the drive on the cable (it's the only device on the cable right now) with no luck.

I've been going crazy trying to get something to work and found this at VIA's site
[http://www.viaarena.com/default.aspx?PageID=22&DSCat=187&DCatType=3](http://www.viaarena.com/default.aspx?PageID=22&DSCat=187&DCatType=3)
which basically says that some versions of linux don't recognize the via cx700m ide controller and will result in not recognizing the hard drive after booting or having no DMA support.


 I checked into [http://ubuntuforums.org/showthread.php?t=483579](http://ubuntuforums.org/showthread.php?t=483579) which said that the problem was a master/slave jumper in the wrong position.  I even tried changing the position of the drive on the cable (it's the only device on the cable right now) with no luck.

I've been going crazy trying to get something to work and found this at VIA's site
[http://www.viaarena.com/default.aspx?PageID=22&DSCat=187&DCatType=3](http://www.viaarena.com/default.aspx?PageID=22&DSCat=187&DCatType=3)
which basically says that some versions of linux don't recognize the via cx700m ide controller and will result in not recognizing the hard drive after booting or having no DMA support.

Can anyone offer any advice or tell me if the CX700M southbridge chipset is supported on Ubuntu 7.1?  Do I really need to recompile the kernel with VIA's drivers?  How can I do that when I can't even install Ubuntu?

I just tried installing Windows XP and it seemed to work fine on that.

More info can be found out about Jetway J7F5 mother board hardware at [http://www.jetwaycomputer.com/VIA.html](http://www.jetwaycomputer.com/VIA.html).

I am not trying to use the onboard SATA, this is a PATA IDE drive.

---

### Post by fredless on 2008-04-01
I had exactly the same problem trying to install 7.10 server on a Jetway J7F5 with SATA drives

The multiple tips from "line72" in this post: [http://ubuntuforums.org/showthread.php?t=414903](http://ubuntuforums.org/showthread.php?t=414903) got me booting and restarting successfully.

I do have a new problem that I am now struggling through, my SATA drive performance is *very* poor (dd measures file writes at 6 MBs) and DMA does indeed seem to be off.  So the system is working, but as a samba server the performance blows currently.

I'm working with some of the VIA technotes ( [http://www.viaarena.com/default.aspx?PageID=22&DSCat=187&DCatType=3](http://www.viaarena.com/default.aspx?PageID=22&DSCat=187&DCatType=3) ) on how to recompile the kernel to properly recognize the south bridge, but they aren't super good nor specific to Ubuntu, and I'm pretty much a make noob, so it's taking me a while to get through.  In addition some of the suggested additions in the technote already exist in the kernel source, so I am confused on whether the chipset is supported or not with DMA by edgy out of the box.

lspci shows a unknown IDE interface:
```
$ lspci | grep IDE
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 0581
```

Tips from anyone appreciated.

---

### Post by zarbon on 2008-04-01
Yes, I found the same thing through another post...  It turned out that all I needed to do was:
```
modprobe ide-disk
modprobe ide-generic
```

I also have the DMA problem.  You might also look at the [http://www.tkarena.com/forums/](http://www.tkarena.com/forums/) and see if they have any advice.  I actually tried the "zen" kernel from [https://wiki.ubuntu.com/ZenKernel](https://wiki.ubuntu.com/ZenKernel).  It is a newer version of the kernel which according to the lklm seems to be fixed: [http://www.google.com/search?hl=en&safe=active&q=+site%3Alkml.org+cx700&btnG=Search](http://www.google.com/search?hl=en&safe=active&q=+site%3Alkml.org+cx700&btnG=Search).  It didn't fix the problem for me.  I was on my way to building a new kernel using [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) but ran out of disk space doing the build.  I was using the instructions from via technotes that you pointed out with the modification to the device location of 0x0581, not 0x5324 as the directions say.  You have already figured this out by using lspci.

So to answer your question.  I am confused too, and have no idea if the cx700m southbridge is supported, but everything I have seen in forums indicates that it is, while everything I have seen on my system indicates that it isn't.  I'm not sure if there is someway to force the use of the via8200 dirvers or not.  I tried:
```
/$ more /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

via82cxxx
ata-piix
loop
lp
sbp2
fuse
```
in my /etc/modules but it didn't seem to work.  If you figure it out, please post to this thread so I can fix the problem also.  I had to take a break from dealing with it but if I figure it out, I will post the results in this thread.

---

### Post by fredless on 2008-04-02
Okay I'm (slowly) getting smarter about this.  I started thinking about things, and so I:
```
/usr/src/linux/drivers# find . -name "*.c" -exec grep -i -H -n '0x0581' {} \

./ata/pata_via.c:625:   { PCI_VDEVICE(VIA, 0x0581), },
```

Ahem.  Note that this search was run on original source before I did any of the mods suggested by the VIA note.  It looks as if 0x0581 is already defined in another driver.

Another search yielding that pata_via was defined in the ATA Kconfig file as well, which makes sense I guess.
```
usr/src/linux/drivers# find . -name "Kconfig" -exec grep -i -H -n 'pata_via' {} \;

./ata/Kconfig:530:config PATA_VIA
```

So I went into 'make menuconfig' found sure enough found the referenced driver under "Device Drivers... Serial ATA and Parallel ATA drivers..." towards the bottom: "VIA PATA Support".  It was excluded, so I tried to mark it as included, but I got a dependency error on the parent, so I went and marked it included and then went back and was able to include the VIA PATA support.  I'm not totally hip with the implications of what this means, but I did it anyway.

So at this point I am in the hours-long process of building the package based on the instructions in the Master Kernel Thread.  I have essentially thrown out the VIA instructions for the time being.

I will keep you posted.

---

### Post by fredless on 2008-04-03
Okay, so a brief update.

After recompiling the kernel and installing (new kernel size was like 44 MB, whew), I am getting the following error at boot

```
ata1.01: failed to set xfer mode error mask 0x1
```

It eventually drops to busy box.  Interestingly, there is now a /dev/sda I see there.  This wasn't here before, ever.  My disks always showed up as /dev/hda and /dev/hdb (I have two).  But there is no /dev/sdb.  I am also unable to mount any partitions on the disk that does show up, although their corresponding devs are present (sda1/sda2).  I get a device or resource busy error returned.

"mod-probe ide-generic" returns IRQ busy errors for both disks, which kinda makes sense since they are already covered inside another driver I'm assuming.

Removing quiet and splash from the boot options, I can see where it finds both disks and identifies their size properly.  Scratching my head on this new problem.  Searching reveals a number of people who have encountered this trying to boot from the install CD, but nothing quite like what I am running into.

I'm very curious if the above will work for you since you are using PATA drives and not SATA.

---

### Post by zarbon on 2008-04-03
I know that some of the drivers make drives scsi (/dev/sda rather than /dev/hda) but I couldn't tell you why or what it means.  It seems like a good sign to me.  At least it means that you are not using ide-generic anymore.  You can try and run "lsof" to see what is using the /dev/sda file.  If you can figure out what is using /dev/sda1 you might be able to mount it.  Are you running a raid configuration?

Out of curiosity, were you able to boot up from a live CD?  Or how did you install?  I was unable to boot from a live CD and ended up using the minimal install CD to boot and install.  I was using a very old IDE CD drive though.  

Now, I am actually using 2 SATA drives and booting from an IDE-flash card drive.  The SATA drives are in a fakeraid configuration.  I was planning on messing around with that soon, I'm not sure if I will have time today, but probably this weekend  I can take a look at it.  Incidentally, this is why I ran out of disk space when trying to build the kernel, the flash card is only 2 gb. 

This is pretty exciting.  Who knew that using a Jetway board would be such a pain?  I though I could just install ubuntu and everything would just work...

---

### Post by fredless on 2008-04-03
Is lsof available in busybox?  I tried it and the command was not found.  And even though I see the drives being identified as the kernel inits, I can't seem to mount the partitions at all, nor get the second drive to (sdb) to show.

So I do have two identifical SATA laptop drives, configured in software RAID1 (md0).  I did this via the live CD install.  And yes, the live CD seemed to work fine for me, I actually installed twice, once without software RAID and again once I figured out how to do the RAID stuff.  I was using an external USB DVDROM of fairly new make.  The RAID works fine too, it's just makes the whole thing even slower (3 MBs to the partition on the RAID).  In fact at first I was troubleshooting the heck out of the RAID, thinking my problem was there, until I noticed that performance sucked on regular partitions too.

Still somewhat at my wits end here.  So while in make menuconfig I noticed an entry for VIA SATA in the default kernel as a module.  I just tried to boot to the unmodded kernel and issue a modprobe sata_via, but nothing was found.  Not unexpected, as the .c file for this driver doesn't match any of the PCI device IDs.

Interestly though, this same .c file does have an entry for 0x0591... awfully close.  So tempting to change :)

So next I'm either going to do that, or return to the VIA technote and follow their instructions to the end, and also make sure the VIA PATA driver in the source is not included in my next kernel build, since it seems to have an overlapping PCI ID.  I'm worried about the viability of the VIA technote though, since it doesn't show our PCI ID either.

Like you, I have limited time for futzing with this right now.  Not to mention that kernel builds are taking about 4 hours each go.

---

### Post by fredless on 2008-04-03
Okay, here it what I decided to do.  After googling about for "0x0581" and finding this: [http://fixunix.com/kernel/347043-problem-corruption-problems-pata_via-via-nanobook-owners-cloudbook-easynote-xs-etc.html](http://fixunix.com/kernel/347043-problem-corruption-problems-pata_via-via-nanobook-owners-cloudbook-easynote-xs-etc.html)

I've decided to implement the changes mentioned there, which are similar to what you and I were originally thinking about doing by modifying the stuff in the VIA technote.  Kernel is compiling now, so I'll let you know how it goes in 6 hours or so when I have a chance to come back to it.

---

### Post by zarbon on 2008-04-03
I've seen part of that post before, but I don't think it had the last responses.  I believe the via technotes are for 2.6.18.  Things were different and looked partially fixed in the kernel code when I was starting the rebuild for 2.6.24, but that post pretty much explains that some things were missed.  I think that just might do it. 

 It's hard for me to believe that no one else is having this problem.  There can't be so few jetway MB's running linux.  Either that or nobody noticed the slow hard disks.

---

### Post by fredless on 2008-04-04
Okay, here's the deal.  I think.

After rebuilding the kernel following those instructions (roughly, the line numbers for the .c file are slightly different) and rebuilding the kernel, I rebooted.  The kernel found the drives right away (no need to drop into busybox and do a modprobe via82cxxx or anything like that).

However, the boot time for the kernel was quite a bit slower, in particular on the "Loading hardware drivers" step.  Guessing, I would say my previous yaird generated kernel (with no DMA support) booted in about 25 seconds, this new kernel took 3-4 minutes to get booted.  Even once everything was started, I noticed it took the system several minutes to really start responding well.

Looking at the size of the generated kernel might explain this, although I'm totally guessing.  The original 7.10 kernal was ~7MB, the yaird generated one was ~2 MB, but this new one was ~45 MB.  I'm assuming driver bloat, probably because I don't know what I'm doing with "make menuconfig".

Once the system settled down, I tried a few things:
```
# lspci | grep IDE
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 0581
```
Bummer.  Note that I also put via82cxxx in my /etc/modules, but this didn't seem to make a difference.  

Disheartened and ready to give up:
```
# hdparm -d /dev/hda

/dev/hda:
 using_dma     =  1 (on)
```

Say what?  Okay, now for the real deal
```
# dd if=/dev/zero of=test.img count=80 bs=10M
80+0 records in
80+0 records out
838860800 bytes (839 MB) copied, 27.5961 seconds, 30.4 MB/s

# dd if=/dev/zero of=test.img count=80 bs=10M
80+0 records in
80+0 records out
838860800 bytes (839 MB) copied, 31.6076 seconds, 26.5 MB/s
```

Whoa momma.  Note that the first test was done on my non-raid partition, and the second was done on my md0 RAID1 partition.  This is a 5 factor increase on my non-RAID partition and I about a 10 factor performance increase on my RAID partition.

So while the system boot time kinda blew, run time performance once stable seemed pretty decent.  Definitely better file system performance.

I was about to button this message up and send to you, when one more thing occurred to me: use yaird again.  I did, it yielded an ~4 MB kernel.  Booting this kernel was much better, similar to previous good boot times.  And I still have DMA.  Woot!

So.. not really sure what I have done here, but I now have DMA support.  I suspect that most of what I did in the via82cxxx.c file didn't really make much difference, and that some other driver selected in the kernel build is responsible here, but I don't know.  Do you how to tell what driver is behind /dev/hda for example?  I don't.

But thinking... at least at this point, that I may have arrived somewhere.

---

### Post by fredless on 2008-04-04
One other item I hadn't mentioned before.  Prior to all of this, when I was doing a large file copy, my CPU cycles would totally spike, and just the processing of opening another terminal session would take quite a few seconds.  That condition seems to be gone as well... large copies do impact the CPU somewhat (~5%), but nothing like before.

Also, my drive light used to be on solid during operations, now it flickers more like a file server should, it's probably more off than on during file copies now, I'm assuming that the delay source is now more apt to be my wireless network than the drive.

<giddy>

---

### Post by zarbon on 2008-04-04
I am pretty sure that /proc/ide/drivers and /proc/ide/hdX/driver contain the information about what driver is running.  Just cat or more those files and it lists a driver version, for me:

```
/proc/ide$ more drivers
ide-disk version 1.18
```

Thats fantastic that you were able to get DMA working.  This weekend I am going to try and rebuild my system, removing my flash ide drive and using only a raid 1.  I think I am going to try the fakeRAID rather than software raid, although I'm not sure at this point.  I'll keep you posted on when/how I get DMA enabled after my rebuild.  I think your CPU spike is due to the software raid, which has to do some work when you access the raid drives.

I would be interested to see the results of your /proc/ide/drivers file to see if you are using a different driver now.  If I could figure out how to force the via82cxxx driver, I think that is all that would be required to enable DMA, but I don't know how to do that other than including it at the top of my /etc/modules.

Good work!

---

### Post by fredless on 2008-04-04
*>> but I don't know how to do that other than including it at the top of my /etc/modules.*

So that is what I did.. but still doesn't seem to be there.

Even more interesting:
```
/proc/ide$ cat drivers
ide-disk version 1.18
```

---

### Post by zarbon on 2008-04-04
So it looks as if you have the same configuration as before, but somehow you have DMA now.  That is strange.  I'm working on rebuilding my box today, I'll let you know what I come up with.

BTW, I got a live cd to boot by adding break=top to the options then running modprobe ide-disk, modprobe ide-generic, and modprobe ata_piix.  The CD wasn't recognized.  Same problem as happened with the hard drives.  I also was able to boot off of a USB flash drive early on when I couldn't boot off of the live cd.  It makes sense that a USB CD drive would work ok.

---

### Post by zarbon on 2008-04-07
Alright, so I finally got my box rebuilt.  I had tons of problems with the software raid trying to sync/rebuild during the install.  Then the alternate cd that I was using to install crapped out even though it checked out ok according to the cd check.

I found a bit more detail on the fix here: [http://readlist.com/lists/vger.kernel.org/linux-kernel/90/453613.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/90/453613.html).  It looks like this fix is in the 2.6.25-rc2 kernel.  I'm sure it will be awhile before we see it in an installable Ubuntu release.  But I'll cut to the chase.  The build was completely successful to solve the DMA issue.  My previous hdparm -t was bout 4 mb/sec and now it is 77 mb/sec!

From dmesg I get:
```
[   49.128354] VP_IDE: IDE controller (0x1106:0x0581 rev 0x00) at  PCI slot 0000
:00:0f.0
[   49.128479] VP_IDE: not 100% native mode: will probe irqs later
[   49.128546] VP_IDE: VIA cx700 (rev 00) IDE UDMA133 controller on pci0000:00:0
f.0
```

From lspci I still get:
```
00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 0581

```

Also, even with a 43 MB kernel, my boot time was at least 2x faster than before.  I think I'm going to dig up yaird and give it a try.  I am pretty much a linux noob so I don't really know what it does, but if it can reduce my kernel size from 43 MB to 4 MB it seems like a good thing.

---

### Post by fredless on 2008-04-07
Sweet.  Interesting that your large kernel boots quickly while mine does not.  But I'm not overly concerned over it, perhaps a difference in the fact that you are using PATA and I SATA.

From what I can gather of yaird, it takes the current kernel in memory and generates a bare bones kernel, with just enough driver support to boot the system.  I have a feeling for a workstation it might cause some issue since it seems to knock off additional video drivers and whatnot.  Doesn't concern me, as I intend to principally use my system headless most of the time.

In any event, my outputs all look the same as your outputs now.  My hdparm -t rates are at ~48 MBs, so I'm happy.  I am using some of the lowest power 2.5 laptop drives I could find, so not surprised that we have a performance difference.  By the way, my total power draw on this system when idle is 16 watts, and 20 watts under load.  I'm happy with that too :)

Glad that your kernel build fixed DMA for you too.  Wish it wasn't this hard, but oh well.  Hopefully our experience will help someone else at some point.

---

### Post by zarbon on 2008-04-07
I tried to run yaird last night after I posted.  I got a fatal error complaining about a bad link device.  I found a reference to how to fix it by removing the "INPUT" line in the /etc/yaird/Default.cfg file.  I did that and it build a initrd image for me ok.  When I tried to boot from it I had no luck though.  It went into a kernel panic.  I'm not going to mess with it too much since my kernel seems to boot quickly.  It also isn't a concern for me since I intend to use the box as an always on print/file server.  Anyway, it is interesiting that mine boots quickly while yours did not.

The reason for my rebuild was to remove the PATA flash card ide since this really didn't seem to make much sense.  I am no running off of the 3.5 SATA drives in software raid 1.

How are you finding out your power consumption?  I would love to know what mine is using.  What processor do you have?  I have the 1.2 ghz c7.  I opted for the dvi rather than hdmi board also.  I am using a g.skill 1 gig 533 mhz ram stick.  I am still using a standard power supply but the plan is to get a pico-psu and run it completely silently, except for the disk drives.  I might look into putting laptop drives in mine also if it makes  a big difference in power consumption.

Yeah, via and jetway sure don't make it easy to get your system running well on linux.  From what I read via's linux support is horrible.

---

