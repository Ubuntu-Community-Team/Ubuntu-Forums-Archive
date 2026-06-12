---
title: "I want to do a dangerous low-level format. How do I go about doing so?"
date: 2009-03-08
forum: Hardware
---

### Post by Neo_The_User on 2009-03-08
Hello. I ran e2fsck -c about 10 times, several HDD checks (tune2fs -c 1 && tune2fs -C 1 and rebooted and did that command again like 500 times) and I still have 0.1% non-contiguous files. I managed to clean it up from 0.2% to 0.1% but eventually it just goes back to 0.2% non-contiguous files. I have tried every single "safe" way to format it and my HDD is still screwed up. After about a day of normal usage (creating files and directories on the hard drive, launching everyday applications) my entire operating system gets all screwed up and it keeps saying filesystem not clean, check forced, blah blah blah. I know that dangerous low-level formats can lead to permanent damage and severe data corruption but I need to make my HDD act as if it were a brand new hard drive before the release of Ubuntu 9.04 so I can do 9.04 development on my hard drive rather than on a CD (yes I have a problem doing software development on a CD) so any help would be greatly appreciated for my side of the bargain and for all the future 9.04 users as well. You scratch my back, I scratch yours. Now... How do I erase every single block of data on my HDD as dangerous as it may be? I tried everything, still no dice. A new HDD is not an option because I only have 2 HDDs. 1 for my Playstation 3 and one for my computer. I need my HDD fixed. How do I wipe out all data? I erased all the partitions with fdisk, cfdisk, slackware slow format, still having problems. I tried everything. I need something more powerful and dangerous to wipe my HDD out because it is ***MY LAST RESORT.*** Thank you so much in advance.

---

### Post by Neo_The_User on 2009-03-08
Help? I've been using a LiveCD assisting others for 4 hours. Oh no wonder... Can a mod please move this to hardware & laptops?

---

### Post by Neo_The_User on 2009-03-08
OK I'm getting annoyed using this slow LiveCD for 6 hours. Please help.

---

### Post by Rallg on 2009-03-08
You say you want to nuke your hard drive? Try this:

First, if necessary using the partition editor from the live CD, ensure that the hard drive has only one partition.

Second, observe what the hard drive is called, as seen from the live CD. I will suppose it is sdX, where X is probably a or b.

Then, take a deep breath. From the live CD, launch Terminal, then:

sudo dd if=/dev/zero of=/dev/sdX bs=512

where X is whatever it is. Then sit back and wait.

In theory, that will write 0 everywhere on the hard drive, including its MBR (meaning that it will no longer have an MBR). Others tell me that there is some metadata left behind somewhere. I don't know.

Then, install a new file system. I suggest that you also give the hard drive a new disk label. This is a menu choice somewhere in the partition editor.

---

### Post by Neo_The_User on 2009-03-08
> **Rallg said:**
> You say you want to nuke your hard drive? Try this:

First, if necessary using the partition editor from the live CD, ensure that the hard drive has only one partition.

Second, observe what the hard drive is called, as seen from the live CD. I will suppose it is sdX, where X is probably a or b.

Then, take a deep breath. From the live CD, launch Terminal, then:

sudo dd if=/dev/zero of=/dev/sdX bs=512

where X is whatever it is. Then sit back and wait.

In theory, that will write 0 everywhere on the hard drive, including its MBR (meaning that it will no longer have an MBR). Others tell me that there is some metadata left behind somewhere. I don't know.

Then, install a new file system. I suggest that you also give the hard drive a new disk label. This is a menu choice somewhere in the partition editor.

Thank you so much. So my root filesystem  is /dev/sda1 and my swap is /dev/sda5. So I would do 

```

sudo dd if=/dev/zero of=/dev/sda bs=512

```

right? btw you are my hero! Thanks a million for helping me. It means so much to me. Now I can hopefully use my HDD again when I'm done with this. Can I use any kind of rescue disk? I really like the arch linux minimal cd. Could I use that?

---

### Post by Rallg on 2009-03-08
Yes, in your case you would use sda. In the past, I have first used partition manager to make the hard drive into a single partition, then applied the code. I don't know if it works just as well when the drive has more than one partition. You can try it!

I believe that in your situation, there is nothing magical about the number 512. However, there is another usage of the code that does require 512 rather than some other number, so I use it out of force of habit.

I have no familiarity with Linux rescue methods. On my system, I have 2 nearly identical partitions of Ubuntu, plus a common home directory (same user name). I only change one Ubuntu at a time, and wait a couple of days before updating or installing something in the other. Once a system is working properly, it seems that most problems are caused by imperfect updates. If I mung one of the systems, I just boot to the other until someone solves the problem for me. I don't use swap (having a solid-state drive), but if I did, only 1 swap would be needed in common for several Linux partitions of any kind.

---

### Post by Neo_The_User on 2009-03-09
RallG, this thing has been running forever. btw I removed all the numbered sda partitions. Is that what you mean by 1 partition? Or do you mean one /dev/sda1? Because right now its all blanked (no partitions) and its been running for an hour. How much longer do you think? I use an AMD Athlon XP 2000+ clocked at 1.5 GHz (1533 MHz) and a gig of RAM.

---

### Post by Gramps on 2009-03-09
Probably depends on how big the drive is, might take a while.

---

### Post by yther on 2009-03-09
I don't believe you ever stated the size of your HDD, but it's going to take a long time.  I've been using **shred** to securely erase some 40 GB laptop drives lately, and for 10 passes it takes around 20 hours, so for one pass it would take about two hours; that's on a 5400 RPM drive with max speed of 1.5 Gb/sec speed.  You're writing all zeroes, not random data, but it's still got to write to every sector on the disk, so expect it to take a while.

I do remember older computers having BIOS tools for low-level formats, but I think modern ones don't seem to have that.  I believe you'd have to get diagnostic tools from the HDD manufacturer to do it now.  Remember that this is still not that kind of format; you're using the operating system to write to the drive, so it's still a "higher" level operation.

"sudo hdparm -I /dev/xxx" will get you a ton of info on the drive, and the manufacturer should be in the first few lines of this.  For example:

```
ATA device, with non-removable media
        Model Number:       WDC WD1001FALS-00J7B0                   
        Serial Number:      WD-WMATV0558653                         
        Firmware Revision:  05.00K05                                
        Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
```

I know "WDC" is Western Digital (and I built this machine, so I know it's right ;)), but if you're not sure about yours just throw that model info into Google.

Then I throw "low level format" and the manufacturer at Google, and shortly I find this:

[Western Digital's software download page](http://support.wdc.com/download/index.asp).  You can search for your drive by model number, and they are kind enough to provide a bootable ISO image, meaning it's no problem that I'm not running a MS operating system here.  :)

If you think you are having problems that require a low-level format to resolve, I strongly suggest you find some diagnostic software for your disk, and run it.  It should be able to tell you if your drive is on the verge of failure, and help you fix it up if it can be fixed by software.

---

### Post by lavinog on 2009-03-09
0.1% non-contiguous files doesn't seem all that bad...isn't that just the fragmentation? I thought it had nothing to do with errors.

You may want to look at the hd manufacturers site for a disk utility program.
Segate, Western digital...etc They all have some sort of bootable cd that performs all sorts of actions on your drive...including a complete wipe to brand new. More importantly, they have tools to test each sector on the drive for defects. I had to use this on a laptop last week because a windows system file was on a bad sector, and was preventing it from booting up...ran the utility disk from IBM, scanned the disk (took about 2 hrs), it found the errors, fixed them, and windows booted up perfectly, with all the data.

---

### Post by Rallg on 2009-03-09
Indeed, it can take awhile. You will know it is done when the Terminal reports thus-and-such bytes written, then returns you to an ordinary prompt.

If you need to shut off your computer, or for any reason stop the process, you can do it. What you are doing is writing zeroes to the hard drive, starting from its beginning. If you stop the process before it completes, then the remaining part of the hard drive will not have the zeroes. So, you could-re-start the process some other time, and once again it will begin at the beginning. Incidentally, as soon as the process starts, you nuke the boot record and partition table.

You can continue to use the live CD for Internet, or whatever, while the hard drive gets its zeroes. Might be VERY slow, though.

EDIT: As others have noted, writing zeroes does not diagnose the drive, or find bad sectors, or get down to the lowest level. All it does is write zeroes. I suggested using this method because (from posts elsewhere on this forum) some users have had problems from messed-up partition tables, it seems; writing all zeroes can be helpful, in that case.

FURTHER EDIT: Here is a quotation from the Wikipedia article about Disk Formatting:

"While it's impossible to perform an LLF [low-level format] on most modern hard drives (since the mid-1990s) outside the factory, the term "low-level format" is still being used (erroneously) for what should be called the reinitialization of a hard drive to its factory configuration (and even these terms may be misunderstood). Reinitialization should include identifying (and sparing out if possible) any sectors which cannot be written to and read back from the drive, correctly. The term has, however, been used by some to refer to only a portion of that process, in which every sector of the drive is written to; usually by writing a zero byte to every addressable location on the disk; sometimes called zero-filling."

---

### Post by Neo_The_User on 2009-03-09
Oh ok. Yeah the dd command you gave me seemed to have fixed my hard drive. 100% Nuked. Thank you so much. Now I can continue contributing to the Ubuntu project and the dri freedesktop projects. :D

My hard drive is an 80GB SATA (usb like cable). All my other hard drives are much bigger but they use PATA (big ribbon cable)

---

