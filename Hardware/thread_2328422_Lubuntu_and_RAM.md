---
title: "Lubuntu and RAM"
date: 2016-06-21
forum: Hardware
---

### Post by marina6 on 2016-06-21
Hello, I'm on an old laptop that I want to dual-install Lubuntu onto. I have the install USB ready, but first I want to address two concerns I have about the RAM. I've been familiar with Linux for about 2 or 3 days, so bear with me if these are silly questions.

Here are my specs:
**Model:** HP 311 Mini
**OS**: Windows XP Home 2002, 32 bit
**Processor: **Intel Atom N270
**Graphics:** Nvidia ION GeForce series 
**Current RAM:** 1,024MB
**Hard drive**: Samsung HM160HI SCSI 149GB

First question: For the dual OS setup, I've read that there is a swap rate and that a setting of 10 or less helps prevent wear on both your HD and your RAM. If I were to install Lubuntu with my current RAM, should I set it to something like 5? Would setting it to around 5 or less greatly reduce risk of any overload-related failures?

And my second question: This week, I tested a dual install of Lubuntu on my other mostly dead desktop which has 2GB of RAM. It's responded beautifully despite a dying hard drive, so I wanted to check with my laptop's manual to see if I could add 1GB or 2GB of RAM to it. Here's a screenshot of the page:
[ATTACH=CONFIG]269686[/ATTACH]

If I've interpreted correctly, I can safely add 2GB of RAM to this thing to help the whole system run more smoothly. Would this one work? [https://www.amazon.com/Kingston-ValueRAM-1333MHz-KVR1333D3N9-2G/dp/B0019MI1CW](https://www.amazon.com/Kingston-ValueRAM-1333MHz-KVR1333D3N9-2G/dp/B0019MI1CW)

It seems I'll be stuck with this pc for a few more years and besides the low RAM and unsupported OS, its hardware is healthy. I don't have more than maybe two restore options so I want to make sure I do this properly.

Many thanks for any input!

---

### Post by sudodus on 2016-06-21
Welcome to the Ubuntu Forums :-)

I think Lubuntu will work well on that computer, but to be sure, please [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389). I'm not sure about the graphics.

Lubuntu works well with 1 GB RAM, but works better with more RAM. You can also try the medium light flavours Xubuntu and Ubuntu MATE, particularly if you have more than 1 GB RAM.

With a hard disk drive and 1 GB RAM (or more), you need not change the swappiness. I suggest that you keep the default value. Anyway, I would not recommend a value below 10.

I am not sure about the RAM (it is probably OK, but good if it can be confirmed by someone else). I suggest that you check what kind of RAM you have now, and get a similar kind (the same clock speed etc). You can check it from a live session (booted from your USB drive) with the following command

```
sudo bash -c 'lshw > lshw.txt'
```

or if you want to post the result within [noparse]```
tags
```[/noparse], it is a good idea to sanitize it, so use the following command

```
sudo bash -c 'lshw -sanitize > lshw.txt'
```

---

### Post by marina6 on 2016-06-21
Thanks for the welcome! I think I'll be sticking around as I'm writing from a very smooth live session. 

And thanks again for dispelling some of my worries.:KS I sent the lshw file to my email to keep it handy.

I've officially clicked and tried every app, and I also tried watching videos--all were just fine. I only have one issue: Abiword starts flickering when I type in it. Google says this is common and not a reflection of a deeper problem. It seems like a dual install is a good idea.

---

### Post by sudodus on 2016-06-21
With a hard disk drive you have drive space enough for a better word processor. I suggest that (after installation) you install ***LibreOfffice***, which can do a lot more than Abiword and Gnumeric. And I don't think you have problems with flickering.

> Hard drive: Samsung HM160HI SCSI 149GB

It is a very good idea to ***backup*** your current system before you start to edit the partition table and install Lubuntu, because these operations are risky, and you want to lose neither your personal files nor Windows. The best backup is to a separate hard disk drive, an external drive, or a 'naked' internal drive and a box for connecting it externally via USB. You can also create recovery disks for Windows.

-o-

How much drive space is Windows using? It will decide how to partition the hard disk drive. Windows need a fair share of free space, otherwise there will be big problems with fragmentation, so you should leave at least 25 % extra space (more than what is occupied by Windows).

You should ***shrink the Windows partition with Windows*** (when booted into Windows). Reboot into Windows and let it fix the partition table so that it is happy with the new situation.

After that you can ***boot into a live session of Lubuntu***, 'Try Lubuntu'. Use ***gparted*** to create an extended partiition of the unallocated space. In the extended partition you create a root partition and a swap partition. The swap partition can be 2 GB and the rest of the space should be the linux root partition.

The next step is to start the ***installer*** and install Lubuntu. At the partitioning window you should select ***Something else***, and select the partitions that you created with gparted.

---

### Post by weatherman2 on 2016-06-21
> **sudodus said:**
> You should ***shrink the Windows partition with Windows*** (when booted into Windows). Reboot into Windows and let it fix the partition table so that it is happy with the new situation.

Windows XP does not support shrinking partitions like that.

I would use Gparted to do it in a Linux Live session before trying to install Linux.  I've shrunk many XP partitions without issue, but it is again crucial to backup any important files in case something goes wrong.  The important thing to remember is: DO NOT INTERRUPT a partition shrink in progress.  It may take hours.  Let it go even overnight.

Personally, I would wipe XP (get rid of it) and just do a clean install of Ubuntu (or Lubuntu or whatever) unless there is really some great need to boot into an obsolete, unsecure version of Windows again.  One thing I WOULD do before getting rid of Windows: update the BIOS to the latest version, if there is one available from HP.[/QUOTE]

---

### Post by Yellow Pasque on 2016-06-21
> **marina6 said:**
> If I were to install Lubuntu with my current RAM, should I set it to something like 5?

No, I'd advise not to touch the vm.swappiness setting, and if you must, 10 is the minimum I would use. If you're limited on memory, then you definitely want unused pages swapped out to disk to have as much RAM available as possible at a given time. Otherwise, you may notice a performance hit if the system needs to do the swapping at an inopportune time when it could have done it in the background had vm.swappiness been higher.

> Would setting it to around 5 or less greatly reduce risk of any overload-related failures?

No.

> Would this one work? [https://www.amazon.com/Kingston-ValueRAM-1333MHz-KVR1333D3N9-2G/dp/B0019MI1CW](https://www.amazon.com/Kingston-ValueRAM-1333MHz-KVR1333D3N9-2G/dp/B0019MI1CW)

No. You need a 204-pin **SO-**DIMM (i.e. "laptop" memory as opposed to "desktop" memory)
[https://www.amazon.com/Kingston-Technology-ValueRAM-Notebook-KVR13S9S6/dp/B00HV6V5NC/](https://www.amazon.com/Kingston-Technology-ValueRAM-Notebook-KVR13S9S6/dp/B00HV6V5NC/)

---

### Post by yoshii on 2016-06-21
As far as the internet research shows (if you google it), Lubuntu and Xubuntu seem to be the best for low-memory requirements unless you do something alternative like Puppy Linux.  I wouldn't alter the swappiness either.  I pretty much agree with Sudodus's comments.

---

### Post by marina6 on 2016-06-21
I realized I didn't pick the right RAM chip and doubled back a few hours ago (I had everything right except the pins, but forgive me, it was 12am). I'll be getting a 204 pin from Crucial before I do anything with Linux. 

Trust me, all I ever do is back up my info. However, I'm still working on a way to make a restore option if Linux somehow fails on here, because in the sense of resources I'm practically working with tape and thumb tacks--I have* maybe *$30 to work with ($13 is going to the RAM chip) and no optical drive. All of this is an effort to make a bad/iffy situation decent so I don't have to rely on the tape and thumb tacks for a while. That's a mess for another thread I suppose.

Currently, I have 107GB available out of the entire drive of this laptop. 

We've only ever owned 3 low-grade computers with one OS at a time including my current 2 computers--I have never partitioned a hard drive before this week. I was only testing the Lubuntu install on my mostly-dead desktop pc, and I let the installer partition for me during the install. I gave Linux 19 or 20GB and Vista 59GB. That computer isn't having a single problem.

I thought it was perfectly safe to partition while you're installing?

Thanks to all of you for the help.

---

### Post by weatherman2 on 2016-06-21
> **marina6 said:**
> I thought it was perfectly safe to partition while you're installing?

Not 100% safe.  There is always a small risk whenever you resize a partition - and that's the same risk whether you do it yourself or do it via the installer.  It depends on what the resize is doing,  If you have a partition that is mostly full and are shrinking it a lot, the resize can take a very long time.  If power is lost or something in the middle of the resize, the partition could be left in an unusable state.

Some partition resizes are quick, though.  If you have a 160GB hard drive that uses only say 40GB, and the rest free, then resizing to create a new small partition should be very fast.  You can let the installer do it if you like. Doing it ahead of time is probably no faster or slower, but it should make your eventually installation smoother.  You can then choose the new partitions you made - or just resize your existing partition(s) ahead of time then tell the installer to use the free space to make whatever partition sizes it chooses.

---

### Post by marina6 on 2016-06-21
Alrighty--thank you all again. I'll get the RAM and while I'm waiting for its arrival, I'll figure out a restore method.

---

### Post by weatherman2 on 2016-06-21
With my Linux installs, I almost always use LVM which allows me to make "snapshots" of my booted Linux partitions and then safely backup the snapshots.  (With Ubuntu 16.04, you can also use the ZFS filesystem, which supports snapshots by default.)   So while I'm booted up, I can make a reliable backup of my OS partition.

I use the amazing rsync (a command-line tool) to make backups of all partitions and data.  rsync is like copy but only copies things that have changed between source and destination.  Say you have a folder with 10GB of files in it.  The first time you copy it to rsync, it copies everything; if you change only 1MB worth of files and rsync it again, only the 1MB that changed will be copied.  Very handy and efficient.

There are lots of ways to make backups in Linux.  You can find them with some web searching.

---

