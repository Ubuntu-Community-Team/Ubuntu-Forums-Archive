---
title: "Hard Drive Error : ata3.00: status: { DRDY ERR }"
date: 2009-01-09
forum: Hardware
---

### Post by hobong on 2009-01-09
Hi all 
I have problem with my System the log always spam with these messages :

```
..........
68489.756311] ata3.00: status: { DRDY ERR }
[68489.756314] ata3.00: error: { UNC }
[68489.951583] ata3.00: configured for UDMA/133
[68489.951604] ata3: EH complete
[68492.671124] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[68492.671133] ata3.00: BMDMA stat 0x24
[68492.671140] ata3.00: cmd c8/00:08:55:e8:8d/00:00:00:00:00/e2 tag 0 dma 4096 in
[68492.671142]          res 51/40:00:56:e8:8d/00:00:00:00:00/02 Emask 0x9 (media error)
[68492.671145] ata3.00: status: { DRDY ERR }
[68492.671148] ata3.00: error: { UNC }
[68492.899657] ata3.00: configured for UDMA/133
[68492.899678] ata3: EH complete
[68495.610841] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[68495.610851] ata3.00: BMDMA stat 0x24
[68495.610857] ata3.00: cmd c8/00:08:55:e8:8d/00:00:00:00:00/e2 tag 0 dma 4096 in
[68495.610859]          res 51/40:00:56:e8:8d/00:00:00:00:00/02 Emask 0x9 (media error)
[68495.610863] ata3.00: status: { DRDY ERR }
[68495.610865] ata3.00: error: { UNC }
[68495.799599] ata3.00: configured for UDMA/133
[68495.799620] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[68495.799626] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[68495.799631] Descriptor sense data with sense descriptors (in hex):
[68495.799633]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[68495.799643]         02 8d e8 56 
[68495.799647] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[68495.799653] end_request: I/O error, dev sda, sector 42854486
[68495.799675] ata3: EH complete
[68495.800096] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[68495.817023] sd 2:0:0:0: [sda] Write Protect is off
[68495.817030] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[68495.819042] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[68495.826120] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
.....

```
I Have just replace the Hard Drive but the messages are still spaming my system. Any one could please help me ? I also attach the log from dmesg command output.

Thank You

U'm using Ubuntu 8.10 II 
Proc 3.1 Ghz
Hard Drive 320 GB 
Mem 2 GB

It's Kernel bug on ata acpi 
Put "options libata noacpi=1" on /etc/modprobe.d/options 
solved the problem

---

### Post by reya276 on 2009-01-18
I'm also having the same issue with my xps m1330 from dell the same exact error. I even tried installing Intrepid. The funny thing is that the OS install just fine is at boot time that the error occurs, which leaves me to believe that it might be a faulty drive, but now how the hell do I tell dell you hardware is faulty when I removed the OS(hardy 8.04) that it came with. OH BOY.

You know my laptop was working just fine last night, this happen right after new updates were installed. Do they not test these updates?

---

### Post by RJARRRPCGP on 2009-01-18
Still could be a bad HDD and you could have a bad cable connection, if any cables have any obstruction even microscopic, prepare for disk errors galore!

---

### Post by hobong on 2009-01-19
In my case I suspect to cable or even the mainboard but i'm not sure. I have replace the harddrive and cable too ...:(

---

### Post by reya276 on 2009-01-19
I don't think this is the case for me as I was working on this laptop minutes before this happen. I had an update prompt through update manager, the system updated. The I decided to step out and take the laptop with me so I shut it down. When I arrive to my destination which was like maybe 10 minutes I started up again and bam, no system. all I kept getting was this error so I took my Live CD of 8.10 and ran it installed it.

After it installed I logged in and the system prompted for some updates and the system asked me to reboot when it started again the same error again. Now the differences is that it ends like this

[   59.517457] ata3.00: status: { DRDY ERR }
[   59.517504] ata3.00: error: { UNC }
[   59.702599] end_request:  I/O error, dev sda, sector 106645428
/etc/init.d/rc: 327: Syntax error: end of file expected code flow.
init: rc2 main process (2237) terminated with status 2

---

### Post by RJARRRPCGP on 2009-01-19
> **reya276 said:**
> 

[   59.517457] ata3.00: status: { DRDY ERR }
[   59.517504] ata3.00: error: { UNC }


Looks like a bad HDD.

---

### Post by fatmystic on 2009-03-01
I get the simmilar error when the ubuntu8.10 is booted for evaluation (like live CD). I know the drive and connection are working when I boot on windows.

---

### Post by hobong on 2009-03-26
It's Kernel Bug on ata ACPI. I put "options libata noacpi=1" on /etc/modprobe.d/options and the ERROR is gone.

---

### Post by JS_Prom on 2009-04-20
I have had similar errors leading to server (HP Compaq Proliant ML110) crashes since Hardy Heron. The server had 2 sata hard drives then. It would freeze while running, with the hard disk light showing heavy activity. Once it snarled up the grub drive map.

I got two new SATA hard drives converted the 4 drives into 3 raid 1 arrays. md0 for boot and md1 and md2 as LVM2 physical volumes. I loaded Ubuntu Intrepid (Linux Kernel 2.6.27-11-server). After about a month of running without a hitch, the same error has surfaced again. I saw this post and changed the acpi option but to no avail. The system has frozen about 4 times in the last 2 hours. 

*************
Syslog says that the kernel has "kicked out" one of the disks from md2. cat /proc/mdstat reports that one of the disks is missing. 

Syslog entry re missing disk from md2:
Apr 20 11:56:51 backup-server kernel: [ 9295.681203] raid1: Disk failure on sdd1, disabling device.

Apr 20 14:25:24 backup-server kernel: [   10.874178] md: kicking non-fresh sdd1 from array!
Apr 20 14:42:59 backup-server kernel: [   10.614323] md: kicking non-fresh sdd1 from array!
Apr 20 15:32:51 backup-server kernel: [   10.423436] md: kicking non-fresh sdd1 from array!
Apr 20 15:49:01 backup-server kernel: [   11.280233] md: kicking non-fresh sdd1 from array!
**************

Libata related messages:

****************

Apr 20 11:47:48 backup-server kernel: [ 8752.473876] ata4: exception Emask 0x10 SAct 0x0 SErr 0x10000 action 0xe frozen
Apr 20 11:47:48 backup-server kernel: [ 8752.473886] ata4: irq_stat 0x00400000, PHY RDY changed
Apr 20 11:47:48 backup-server kernel: [ 8752.473893] ata4: SError: { PHYRdyChg }
Apr 20 11:47:48 backup-server kernel: [ 8752.473905] ata4: hard resetting link
Apr 20 11:47:55 backup-server kernel: [ 8759.470034] ata4: link is slow to respond, please be patient (ready=0)
Apr 20 11:48:04 backup-server kernel: [ 8762.522533] ata4: softreset failed (device not ready)
Apr 20 11:48:04 backup-server kernel: [ 8762.522552] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 20 11:48:04 backup-server kernel: [ 8762.522557] ata4: illegal qc_active transition (00000000->00000001)
Apr 20 11:48:04 backup-server kernel: [ 8766.068337] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x100)
Apr 20 11:48:04 backup-server kernel: [ 8766.068346] ata4.00: revalidation failed (errno=-5)
Apr 20 11:48:04 backup-server kernel: [ 8767.530038] ata4: hard resetting link
Apr 20 11:48:04 backup-server kernel: [ 8768.832540] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 20 11:48:04 backup-server kernel: [ 8768.926991] ata4.00: configured for UDMA/133
Apr 20 11:48:04 backup-server kernel: [ 8768.927012] ata4: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
Apr 20 11:48:04 backup-server kernel: [ 8768.927021] ata4: irq_stat 0x04400000, PHY RDY changed
************************************

More libata related messages:

Apr 20 14:18:51 backup-server kernel: [   30.273045] ata3.00: status: { DRDY ERR }
Apr 20 14:18:51 backup-server kernel: [   30.273089] ata3.00: error: { UNC }
Apr 20 14:18:51 backup-server kernel: [   30.363192] ata3.00: configured for UDMA/133
Apr 20 14:18:51 backup-server kernel: [   30.363203] ata3: EH complete
Apr 20 14:18:51 backup-server kernel: [   30.363278] sd 2:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
Apr 20 14:18:51 backup-server kernel: [   30.363316] sd 2:0:0:0: [sdc] Write Protect is off
Apr 20 14:18:51 backup-server kernel: [   30.363321] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Apr 20 14:18:51 backup-server kernel: [   30.363382] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 20 14:18:51 backup-server kernel: [   33.288290] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Apr 20 14:18:51 backup-server kernel: [   33.288340] ata3.00: irq_stat 0x40000008
Apr 20 14:18:51 backup-server kernel: [   33.288386] ata3.00: cmd 60/00:00:c7:c3:fc/01:00:02:00:00/40 tag 0 ncq 131072 in
Apr 20 14:18:51 backup-server kernel: [   33.288388]          res 41/40:00:12:c4:fc/94:01:02:00:00/40 Emask 0x409 (media error) <F>
Apr 20 14:18:51 backup-server kernel: [   33.288485] ata3.00: status: { DRDY ERR }
Apr 20 14:18:51 backup-server kernel: [   33.288529] ata3.00: error: { UNC }
Apr 20 14:18:51 backup-server kernel: [   33.378590] ata3.00: configured for UDMA/133
Apr 20 14:18:51 backup-server kernel: [   33.378599] ata3: EH complete

**************************

Finally, this error seems to surface sporadically - the server runs when it does and freezes when it does. But does not seem to head permanently in any one direction!

Will be grateful for help on this.

Regards
JS_Prom

Is this a software problem or is it a hardware problem? Searching on the web has not yielded any clinching answer to this. Yes the system is old but that is not reason enough for the drive to fail.

---

### Post by anjohnso on 2009-05-22
I get the same error, yet it's only when I do a hard shutdown, as with power loss.

---

### Post by z987k on 2009-08-24
> **hobong said:**
> It's Kernel Bug on ata ACPI. I put "options libata noacpi=1" on /etc/modprobe.d/options and the ERROR is gone.

This solved it for me.

---

### Post by fatmystic on 2009-11-17
I agree that noapic is required as additional boot parameter to resolve the disk error. If using CD or other means, use following:

ubuntu  acpi=off noapic

and all the kernel will boot.

---

### Post by anjohnso on 2009-12-03
> **hobong said:**
> It's Kernel Bug on ata ACPI. I put "options libata noacpi=1" on /etc/modprobe.d/options and the ERROR is gone.


I realize I may be showing what a noob I am, but how exactly do I do this?  /etc/modprobe.d/options does not exist.

---

### Post by thatmattbone on 2009-12-07
> **anjohnso said:**
> I realize I may be showing what a noob I am, but how exactly do I do this?  /etc/modprobe.d/options does not exist.
I think in 9.10, any file ending in ".conf" in /etc/modprobe.d is parsed.  I created a new file, /etc/modprobe.d/options.conf and put the "options libata noacpi=1" in there.  Seemed to fix the problem.

---

### Post by sau_sage114 on 2010-02-09
I just got this on ubuntu 9.10.

was playing pokemon sapphire on gvba, then restarted to install the update.  all I can get to is the kernel, but I can't put in a command without it just repeating the same error over and over again for about 3 minutes before going back to the command line.

I also get the error 'module' object has no attribute 'normalize_encoding'

EDIT: also, I know this isn't a hard drive error because I loaded a second version of ubuntu on a different partition and it works fine.

---

### Post by tubezninja on 2010-03-11
For what it's worth: I'm being driven mad by the same issue.  Attempted to add "options libata noacpi=1" but the errors STILL popped up, and it even got to the point where one of my drives stopped reading with sector read errors.

There are two ahrd drives in this box.  I've replaced both of them thinking it was hardware issues, and then had to do a fresh ubuntu OS install.  And the error STILL pops up:

```
[ 1089.724114] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[ 1089.724163] ata3.00: BMDMA stat 0x66
[ 1089.724192] ata3.00: cmd 35/00:00:ef:3c:ff/00:04:00:00:00/e0 tag 0 dma 524288 out
[ 1089.724194]          res 51/84:31:be:3d:ff/84:03:00:00:00/e0 Emask 0x30 (host bus error)
[ 1089.724284] ata3.00: status: { DRDY ERR }
[ 1089.724309] ata3.00: error: { ICRC ABRT }
[ 1089.724342] ata3: soft resetting link
[ 1089.981561] ata3.00: configured for UDMA/133
[ 1090.048905] ata3.01: configured for UDMA/133
[ 1090.048924] ata3: EH complete

```

Over and over again!

---

### Post by jaycakep on 2010-03-23
> **scaredpoet said:**
> For what it's worth: I'm being driven mad by the same issue.  Attempted to add "options libata noacpi=1" but the errors STILL popped up, and it even got to the point where one of my drives stopped reading with sector read errors.

There are two ahrd drives in this box.  I've replaced both of them thinking it was hardware issues, and then had to do a fresh ubuntu OS install.  And the error STILL pops up:

```
[ 1089.724114] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[ 1089.724163] ata3.00: BMDMA stat 0x66
[ 1089.724192] ata3.00: cmd 35/00:00:ef:3c:ff/00:04:00:00:00/e0 tag 0 dma 524288 out
[ 1089.724194]          res 51/84:31:be:3d:ff/84:03:00:00:00/e0 Emask 0x30 (host bus error)
[ 1089.724284] ata3.00: status: { DRDY ERR }
[ 1089.724309] ata3.00: error: { ICRC ABRT }
[ 1089.724342] ata3: soft resetting link
[ 1089.981561] ata3.00: configured for UDMA/133
[ 1090.048905] ata3.01: configured for UDMA/133
[ 1090.048924] ata3: EH complete

```

Over and over again!
sir have you try to restart udev, it's work on my laptop
sudo /etc/init.d/udev stop
sudo /etc/init.d/udev start

here the reference [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/383632](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/383632)

---

### Post by The Spy on 2010-03-24
I can verify that this fix works, though, of course the command will have to be run again after a system reboot.

---

### Post by startling on 2010-11-30
I have the same error with Ubuntu 10.04 on my new laptop:

```

[   88.981845] ata1.00: irq_stat 0x40000008
[   88.981849] ata1.00: failed command: READ FPDMA QUEUED
[   88.981855] ata1.00: cmd 60/20:08:e0:63:87/00:00:18:00:00/40 tag 1 ncq 16384 in
[   88.981856]          res 41/40:00:ec:63:87/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   88.981859] ata1.00: status: { DRDY ERR }
[   88.981862] ata1.00: error: { UNC }
[   89.001502] ata1.00: configured for UDMA/133
[   89.001514] ata1: EH complete
[   89.796094] pwrdown, 0x6(BIT6)=71
[   90.947153] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[   90.947158] ata1.00: irq_stat 0x40000008
[   90.947162] ata1.00: failed command: READ FPDMA QUEUED
[   90.947168] ata1.00: cmd 60/20:00:e0:63:87/00:00:18:00:00/40 tag 0 ncq 16384 in
[   90.947169]          res 41/40:00:ec:63:87/00:00:18:00:00/40 Emask 0x409 (media error) <F>
```

Ubuntu 10.04, after some errors for a while, eventually would not start at all on this new Advent laptop, so I re-installed from a live cd to a new partition. That worked fine for a week or so but now this is also throwing errors all the time and failing to boot. 

I cannot believe it's a hard drive problem. A while ago, When I installed Ubuntu 8.10, on my then new Toshiba laptop, the hard drive died within a few months and needed replacement. Now I've installed Ubuntu 10.04 on a new hard drive and that is showing problems. Is this just bad luck? Or is there a problem with Ubuntu / Linux and laptop drives?

Over the past few days to get Ubuntu to boot, from Grub I have to choose the older version of the kernel (wireless doesn't work with that kernel version or I'd stay with that) which then runs a disk check and fix, and then reboot with the new kernel.

---

### Post by diazjavier on 2010-12-18
I think in 9.10, any file ending in ".conf" in /etc/modprobe.d is parsed. I created a new file, /etc/modprobe.d/options.conf and put the "options libata noacpi=1" in there. Seemed to fix the problem.

Works in Ubuntu 10.04
Thank you

---

### Post by ricardisimo on 2011-01-01
My secondary drive disappeared, and I was getting the same status error, so I tried hobong's fix... and now I have no drives at all, and cannot get past the initramfs command line screen. Curiously, when I run "ls /etc/modprobe.d" the file I created does not appear any longer. Has it been auto-deleted? Were its contents absorbed into some other conf file?

Any help undoing this would be greatly appreciated. Music files and stuff like that can be replaced, but my work files are way too much work to replace. [-o<

---

### Post by azeam on 2011-02-15
Long post with no solutions but here are some of my experiences with this problem (ata3.00 DRDY...) on a Fujitsu Siemens Esprimo v5535 laptop, I assume this doesn't apply to everyone having these problems but perhaps it can keep some of you from throwing the hard drive out of the window thinking that it's dead at least. 

The story starts with the original hard drive (120gb sata), Ubuntu crashed during installation (while writing the MBR) and I haven't been able to boot the drive since then. Makes sense. 

Bought an ssd drive and started getting strange errors, sometimes it booted fine, sometimes BIOS couldn't find it, sometimes these DRDY errors appeared etc. I did some research and came to the conclusion that the laptop simply doesn't support ssd drives and no BIOS updates are ever going to come for this old laptop. Sold the ssd drive and the drive works fine in another computer.

Bought a used 60gb drive which made a bit of "old hard drive" noise already when I got it but it has been working with the exception of two crashes in about two months, works again after formatting it though. 

Got a new laptop, installed an ssd drive in that and put the unused drive (500gb) that came with the new laptop in my old laptop (the Fujitsu). Installed Ubuntu (Maverick) without problems, rebooted and got ata3.00 DRDY errors. Tried basically everything I could think of and reformatted/installed a couple of times but they kept coming (somewhat randomly) during boot. Fsck from live cd gave the message that the superblock was bad and backup superblock couldn't be used. Even tried installing Windows XP, installation went fine but I got a blue screen during the first boot. Under normal circumstances I would probably have given up on the drive but because of the previous problems and the fact that the drive was completely new I figured that it was very unlikely for the drive to be "DOA". So I put this 500gb drive back in to my new laptop and it works fine. 

I'm not sure what causes these errors in the Fujitsu laptop but as far as I can understand it *could* be because of a bad power supply to the hard drive. It makes sense because the ssd and the 500gb should need more power than the smaller 60gb which works (a lot better at least). It could also be because of the lack of AHCI support in BIOS, perhaps the newer drives require AHCI to function properly? Or simply a crap motherboard/IDE controller? The last option (as I see it) would be a connection issue, I've tried cleaning the sata connection and it makes no difference, and to me it doesn't make sense that the 60gb works and the others don't. Still, I don't understand why the OS installations work...

---

### Post by M4rotku on 2011-02-15
Ok, I tried the recommended solution, but it still does the same thing.  It doesn't start up, and when I brought up the command prompt with alt + ctrl + f1, it gave me the same error message as everyone has been getting.

Is anyone else still getting this problem after the added 'options' file?  and are there any other potential solutions/updates coming?

---

### Post by Ddorda on 2011-06-29
That error appears to me on a fresh installation of Ubuntu 11.04.
Tried the suggested solution but it didn't helped and it seems like i still get the same errors.

Ideas? Thanks!

---

### Post by hkenneth on 2011-07-15
I have exactly the same issue as you do. This is my new rig, and Windows works perfectly fine. Mac OS X 10.7 GM (osx86) works too. So this could not be a hardware problem.

Actually, when I install my Ubuntu without Internet connection (to avoid it download updates), the system worked well. But after I updated the system today, the annoying DRDY ERR appeared again. If I use the old kernel, I can boot into the system, but the system frequently got freeze when reading/writing files, and finally dead so I had to do a cold reboot.

---

### Post by tech_ninja on 2011-07-26
I had the exact same error too, but plugging the HDD on to a different port on the motherboard seems to work. It's been running 2 days without any errors.

---

### Post by OCedHrt on 2011-08-03
Not intending to thread hijack, so let me know if I should create a new one. But it seems all the experts are already here.

I have been trying to recover data off of a failing HD using ddrescue and all that remains is about 9000KB of affected earlier. ddrescue has yet to confirm weather all of this is bad and is now reading through it sector by sector.

9071 KB&#12288;/ 512 byte/sector = 18142 sectors. That doesn't sound so bad until you find out it's going very slowly. Checking /var/log/syslog indicates that each sector read attempt is being retried **6** times!

My ddrescue command: ddrescue -d -f -v /dev/sdb /dev/sdc ./dd.log 

I can include syslog if that is useful but what I can confirm is that leading up to each "end_request: I/O error, dev sdb, sector xxxxxxxxx" there are 6 "ata3.00: failed command: READ DMA" entries, each with it's own "ata3: EH complete"

When you do the math, at 18142 sectors * 30 seconds/sector we get 6.3 days!!

I tried setting the block device timeout to 5 seconds from 30 seconds but this just causes each READ DMA to timeout and the ahci driver does the 6 retries anyways, but this time each cycling the ATA link resulting in even longer reads per sector.

Is there a way to turn off the libata/ahci retry completely? I tried searching and read about several experiences but the closest I got was the command timeout and a dismissive response that libata does not retry. Btw, the code for libata seems to mention that there is indeed retry on command failure.

---

### Post by josuelopes on 2012-12-23
> **hobong said:**
> It's Kernel bug on ata acpi 
Put "options libata noacpi=1" on /etc/modprobe.d/options 
solved the problem

I have the same problem and its annoying please tell me what do i have to input in the terminal (the exact words) to solve thi thing? I dont know if it matters but i tried to find the "options" file with command ls and it doesn't find it...

---

### Post by overdrank on 2012-12-23
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

