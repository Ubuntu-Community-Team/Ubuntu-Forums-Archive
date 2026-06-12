---
title: "RAID1 help"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by obley on 2007-05-20
I'm trying to get my head around making a RAID1 storage partition for my server and I feel like i keep missing the mark. I might be just to timid about it, but this will house all my critical data for my home LAN. I need either some reassurance that I am going about this the right way, or slapped straight.

IDE devices in use:
boot from a 30gb disk
cdrom
100MB ZIP
2 maxtor 250GB  drives on a promise controller

// back story, skip if you care not for the details
> I have been running an SBS server for several years but in the past year or so switched all my activities to a LAMP setup (Debian sarge). Now the SBS is just a whore of a file server heating up my tiny home office and wasting energy. I've backed up all my data that was on a fast track "hardware" mirror on windows to a USB drive and installed Ubuntu Server. Now I'm trying to get the mirror set up again to get back to my life.

// on with the questions

First, I thought I would use the hardware raid on my fast track 100 tx2, but fdisk still sees the individual disks. I scanned around the net and think its because its not really a "hardware" raid setup? At any rate, I pulled out that controller and put in my old Ultra100TX2 deciding to use a software raid setup

1) Is there a fix to make the hardware mirror detected and ignore the actual drives, or should I continue with the software raid plan?

2) Now, I think this is what I need to do, corrections?
create matching partitions on the two drives, type = Linux raid autodetect using the whole disk
sudo mdadm --create /dev/md0 --auto=yes -l 1 -n 2 /dev/sdc1 /dev/sdd1
cat /proc/mdstat, wait for it to sync

now what? create a partition? I'm all confused now.

What file system is most recommended? ext3?
should I use lvm? might be nice if I change out the drives with bigger ones in a year or so.

thanks for the help

---

### Post by kidders on 2007-05-21
Hi there,

> **obley said:**
> 1) Is there a fix to make the hardware mirror detected and ignore the actual drives, or should I continue with the software raid plan?There may well be a way to get your hardware RAID working as expected ... and it might very well be quite simple. To be perfectly honest though, if it's anything like the kind of "hardware" RAID that's becoming more and more commonplace these days, I would avoid it like the plague.

What I'm *imagining* you've got (so do correct me if I'm wrong) is one of those awful RAID controllers (like the ones that get burned onto motherboards) that is really just software RAID in disguise, except that it's buggy, poorly supported by most OSs, and impossible to update (without flashing your ROM). If that's the kind of thing you're talking about, true software RAID is (in my opinion) the most desirable option, for a variety of reasons.

I'll stop there though, because I may be waaaay off base about your hardware ... and I wouldn't want to influence your final decision unless I was sure.

> **obley said:**
> 2) Now, I think this is what I need to do, corrections?
create matching partitions on the two drives, type = Linux raid autodetect using the whole disk
sudo mdadm --create /dev/md0 --auto=yes -l 1 -n 2 /dev/sdc1 /dev/sdd1
cat /proc/mdstat, wait for it to sync

now what?There are lots of variations on how to go about actually creating a RAID array. If what you posted seems to be doing what you intended, then that's perfect. :-) I would suggest thinking of what you've created (/dev/md0) as though it were called /dev/hde1 or something ... a low-level block device that you can put a filesystem on top of, as you rightly suggested.

What filesystem to choose is entirely up to you:
[LIST]
[*]Ext3 is a strong, realiable, general purpose filesystem. It's neither particularly good nor particularly bad at anything (except perhaps that routine self-checks can get very time-consuming). Do bear in mind that it has special performance tuning features for use in conjunction with RAID arrays that you should take a look at, to avoid a major performance penalty, although this is less relevant to RAID1 than some alternatives. (Once you've created the filesystem it'll be too late.)
[*]For larger filesystems, it is often worth taking a look at some of the other major choices available, such as XFS, JFS & ReiserFS. These tend to have very specific strengths, and (when applied correctly) can very significantly outperform Ext3.
[/LIST]

Just a couple of other random things...

[LIST]
[*]You mentioned the possibility of expanding your array later. For you, the easiest way to do that will probably be to simply create a new array from scratch, so there's no need to worry about that now, imo.
[*]Don't forget to run a basic performance test on your array, just to make sure it's as quick as you think it *should* be. Once you start putting data on it, you may not be able to do very much fine-tuning.
[*]Another recommendation I would make is to check your config files, and weed out any explicit references to things in /dev. There may not be any, but if there are, you could find yourself running into daft problems if device node names were ever to change for some reason.
[*]One final suggestion: Play around with intentionally making your array fail. When (if?!) something goes badly wrong, I'm pretty sure you'll have enough to worry about without tying yourself up in knots, wondering if the next **mdadm** command you type will screw up your filesystem. Hopefully, you'll be pleasantly surprised by how tolerant Linux's software RAID management is.
[/LIST]

Anyhow, sorry for rambling... I hope that's of some help.

---

### Post by obley on 2007-05-21
brilliant, I'm grateful for the help, dont worry about rambling. I think I waited to long to start asking questions and now I'm all flustered :(

-----------------------------------------------------------

about my hardware:
its actually a Promise FastTrack100 Tx2 PCI card.
[http://www.promise.com/support/download/download2_eng.asp?category=all&os=100&productID=8](http://www.promise.com/support/download/download2_eng.asp?category=all&os=100&productID=8)

My first concern with it was that even thought I had the card set up for the mirror, fdisk still saw the individual drives. I'm not sure if I should have been able to. Unless you see benefit here, I'm dropping it. The Promise Ultra 100 I have in there now will work fine for the software mirror. I think I'll have more monitoring control over a software mirror anyway.

-----------------------------------------------------------
setting up the mirror:
I've gone and created the mirror as I previously posted
sudo mdadm --create /dev/md0 --auto=yes -l 1 -n 2 /dev/sdc1 /dev/sdd1
While I wait on it to sync, I do create this new partition on md0 with fdisk, yea? When I did that in the past it showed a larger number of cylinders then the drives do themselves. is this normal behavior or a symptom of a  screwed up setup? I'm sorry, I should have said that to begin with.

-----------------------------------------------------------

file system:
I'm off to read about these and choose one. I assumed ext3 since it seems to be the common file system for the auto pilot installs.

-----------------------------------------------------------

What is suggested for a performance test? Just writing to it with various file sizes and make sure its to my likings? or is there a test I can run with some results to compare with.

-----------------------------------------------------------

What do you mean dev names changing, like sda suddenly becomes sdc? are there specific files (like mdadm.conf or something) that I need to look in? If they are referenced, what should I use instead? 


thanks again

---

### Post by kidders on 2007-05-21
Hey again,

> **obley said:**
> I think I waited to long to start asking questions and now I'm all flusteredHehe.

> **obley said:**
> its actually a Promise FastTrack100 Tx2 PCI card.Hmm... interesting. I suppose the major differences between hardware & software RAID are...
[LIST]
[*]Hardware RAID is often (if it's expensive) faster, especially when arrays get extremely large. On most modern PCs, software RAID that extends over more than about two devices per bus won't perform well, because of bandwidth constraints.
[*]Software RAID is easier to update (making it less inclined to be buggy). **apt-get update && apt-get upgrade** certainly beats the hell out of flash & pray!
[*]Hardware RAID is platform independent. This often doesn't matter, since using a universally readable filesystem (eg FAT) with RAID would be daft, but can be important on multi-boot computers.
[*]Software RAID is hardware independent, so you don't get tied down to a particular I/O controller. That can be handy if your RAID controller breaks, or if you need to move the array to another machine.
[/LIST]

For a small setup like yours (ie still in the gigabyte range), switching from one to the other shouldn't be *too* complicated, so the choice isn't critical. I'd be happy to help you configure either ... although I have to say Promise controllers (afaik) are not highly regarded. Hopefully, that short comparison will help you pick the right option for you.

> **obley said:**
> My first concern with it was that even thought I had the card set up for the mirror, fdisk still saw the individual drives.Many RAID controllers have two "modes" ... perhaps the wrong one was selected. I don't _think_ Linux should have been able to see the individual component devices if the controller was doing its job properly.

> **obley said:**
> While I wait on it to sync, I do create this new partition on md0 with fdisk, yea?I wouldn't have bothered. I'm sure you *can* (theoretically) write a partition table onto a RAID array, but it's not normally done. That's the distinction I was trying (in my own strange way) to make in my last post, when I suggested thinking of /dev/md0 as /dev/hd[a-z]**1**, rather than /dev/hd[a-z]. It is most usual to create one filesystem per array, simply by running **mkfs** on it. You would then presumably add an entry to /etc/fstab along the lines of...```
/dev/md0 /mnt/raid xfs ...
```...or perhaps you could use the array's UUID instead, to avoid confusion in the event you create more arrays in the future.

> **obley said:**
> I assumed ext3 since it seems to be the common file system for the auto pilot installs.I could be wrong, but I imagine that Ext3 is not commonly used over RAID. Having said that, the three main reasons for this may not apply to you though...
[LIST=1]
[*]The Extended filesystems won't work well (or at all) on extremely large arrays. The caps on the maximum numbers of files, filesystem & file sizes just don't cut it in the RAID world. Take a look at XFS's numbers for comparison!!
[*]In practice, RAID arrays tend to be used for highly application-specific purposes (eg email, databases, multimedia, and so on). The Extended filesystems are too generic, and fail to take full advantage of the properties of the data *actually* being stored.
[*]There are several schools of thought on how mission critical filesystems should do their housekeeping, for disaster recovery purposes. Many of the alternatives to Ext3 take very different approaches to risk management.
[/LIST]

> **obley said:**
> What is suggested for a performance test?Something nice and basic should do the job ... perhaps you could let something like **cat /dev/urandom > /mnt/raid/crap** run for 10 seconds, to see how fast you can write to your array. There are plenty of proper benchmarking apps around, but I was really only thinking of a quick spot-check, just to make sure your array doesn't go 10 times slower than it ought to, or something hehe. It happened to me once (with RAID 5), because the filesystem & the underlying array weren't quite on the same wavelength (which was my fault).

> **obley said:**
> What do you mean dev names changing, like sda suddenly becomes sdc?Exactly. It's nice to be able to do simple little things (eg unplug your array without having to remember what order the disks were in) and not have to deal with Linux being fussy hehe. Many RAID arrays are configurationless (ie there is no reference to their component parts in mdadm.conf, or elsewhere). If you do find a place the component devices are mentioned though, it is (in my opinion) advisable to use UUID references instead. That also eliminates the possibility that you might accidentally force devices onto an array that shouldn't be there.

Anyhow, there are two things that I meant to say about your first post...

[LIST]
[*]You needn't worry too much about "missing the mark" :-) Dealing with RAID is easy enough (once you get the hang of it). Generally, the worst that might happen is failing to squeeze the maximum possible performance out of your array ... it's quite difficult to break one!
[*]Something I do with RAID from time to time involves using ATA over Ethernet to spread RAID1 over multiple computers. I thought you might be interested, since you mentioned the word "critical" in your o/p. Although it obviously doesn't protect against things like accidental deletions, using AoE does protect against major failures (eg a faulty PSU blowing up an entire machine), by saving enough data on a second machine to reconstruct the original array.
[/LIST]

**Edit:** You *did* give me license to ramble ... but jeez! (Sorry!)

---

### Post by obley on 2007-05-22
ok I think I'm getting it. Thanks for your time.

for the sake of others, I'm going to retrace the steps I took now. 
```
sudo mdadm --create /dev/md0 --auto=yes -l 1 -n 2 /dev/sda /dev/sdb
```

run this to monitor the mirror building:
```
cat /proc/mdstat
```

after the mirror synced, I did this:

```
:~$ sudo mkfs.xfs -L storage /dev/md0
mkfs.xfs: /dev/md0 appears to contain a partition table (DOS).
mkfs.xfs: Use the -f option to force overwrite.
:~$ sudo mkfs.xfs -L storage -f /dev/md0
meta-data=/dev/md0               isize=256    agcount=16, agsize=3829958 blks
         =                       sectsz=512   attr=0
data     =                       bsize=4096   blocks=61279328, imaxpct=25
         =                       sunit=0      swidth=0 blks, unwritten=1
naming   =version 2              bsize=4096
log      =internal log           bsize=4096   blocks=29921, version=1
         =                       sectsz=512   sunit=0 blks
realtime =none                   extsz=4096   blocks=0, rtextents=0
:~$
```

What was the partition table? *shrug* fdisk showed nothing.

now parted detects the filesystem:
```
GNU Parted 1.7.1
Using /dev/md0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print

Disk /dev/md0: 251GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start   End    Size   File system  Flags
 1      0.00kB  251GB  251GB  xfs

(parted)

```

w00t!

I should be able to just mount this now right?
```
sudo mount -t xfs /dev/md0 /storage
```
I get nothing returned, but 

```
:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              27G  505M   25G   2% /
varrun                252M   40K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M   84K  252M   1% /proc/bus/usb
udev                  252M   84K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
/dev/md0              234G  544K  234G   1% /storage

```

That is great. Everything looks simple from the experienced side of the fence.

except, I can't use the mount. that output shows 544k used, I copied some scripts over as a test, but I can't see them.

hmm...

---

### Post by kidders on 2007-05-22
> **obley said:**
> ok I think I'm getting it. Thanks for your time.:-)

> **obley said:**
> What was the partition table? *shrug* fdisk showed nothing.It's probably something you'd previously created on one of the disks. Nothing to worry about, now that it's gone.

> **obley said:**
> I can't use the mount. that output shows 544k used, I copied some scripts over as a test, but I can't see them.Odd :-( So **touch /storage/crap** (or maybe **cp ~/* /storage**) does nothing?!

---

### Post by obley on 2007-05-22
I think it was a permissions issue. I changed owner and group of /storage (after mounted) to myself and now I can create, copy, touch, and all that jazz.


can I get a w00t!? 


cat /dev/urandom > /storage/raidTest created a 15MB file in ~15 seconds.

tomorrow I'll install and config samba, copy my data back over and see how it goes. I still don't think I'm going to format that USB drive for a while ;)



Thanks again for your energy and being  patient.

..oh, and teaching me new cool things. That is most important I think.

:KS

---

### Post by kidders on 2007-05-22
Glad everything's gone well. :-)

**Edit:** Does 1 MiB/s seem a little slow to you? (How does that figure compare to other devices?) My machine seems to be able for many multiples of it. :-(

---

### Post by obley on 2007-05-23
well.. in ~/ I got 17MB in about the same time (15 Mississippi)

seems a little slower, it is on an ata100 controller, and they are older drives.

---

### Post by kidders on 2007-05-23
That's perfect. :-) As long as you're RAID array is in the same performance ballpark as the rest of your system, all is well.

---

### Post by obley on 2007-05-23
w00t diggity


that leaves me with one last question, I assume so, but is this mirror OS indepentent then? Say, I format my boot drive and install Debian, or just reinstall Ubuntu because I've mucked it all up. Once the OS is up, and I've reinstalled mdadm, xfsprogs, and remounted all should be well right?

---

### Post by kidders on 2007-05-23
> **obley said:**
> w00t diggityYay!

> **obley said:**
> is this mirror OS indepentent then?It's tied to the kernel, so technically you can use any OS built on the official Linux kernel that hasn't had RAID support explicitly removed from it. In practice, that covers virtually everything that calls itself "Linux", except embedded systems (eg mobile phones).

You wouldn't be able to use Windows, but I'm not 100% sure about OSX. (For all I know, Darwin may happily support Linux RAID!)

The answer you're looking for though is yes ... your array will work indefinitely with everything from Mandriva to Debian, without any messing around.

---

### Post by obley on 2007-05-28
buggers :(

I rebooted

my samba share emptied.. I found that after I rebooted, or some reason, my /dev/sd assignment's changed up.

when I created the mirror it was:
/dev/sda -- primary master on pci ide controller -- drive 0 in mirror
/dev/sdb -- secondary master on pci ide controller -- drive 1 in mirror
/dev/sdc -- primary master on onboard ide -- boot, root, swap
/dev/sdd -- secondary master on onboard ide -- zip drive

when I rebooted the shuffle became:
sda ==> sdc
sdb ==> sdd
sdc ==> sda
sdd ==> sdb

1)  I never opened the case, what would cause these to shift?

2) earlier I was told to make sure I was not referencing "/dev/sdx" in any of my config files, I didn't think I was. fstab is using the uuid to mount. but the mirror just broke, that data is still there but the mirror isn't. Should I be creating the mirror with uuid's to begin with?

---

### Post by kidders on 2007-05-28
> **obley said:**
> I found that after I rebooted, or some reason, my /dev/sd assignment's changed up.Hmmm... The only things I can think of that would cause that are:
[LIST]
[*]A significant kernel update that affects the way Ubuntu interacts with your particular hardware.
[*]Changes to your BIOS configuration.[/LIST] In any case, oddness like that shouldn't be affecting your RAID, even if you created it using /dev node names (which are a lot easier to type!). If I were you, I would go through my dmesg & other system logs for some sort of explanation.

Just to be certain something bad isn't happening, could you post an **mdadm --detail** for your array, and an **mdadm --query** for each device that's supposed to be in it (I'm not quite sure what these are any more hehe!).

In general terms, RAID component devices will go missing if they are unavailable for some reason, when the array is being reconstructed during boot. Your system logs will give you clues, if that's what's happening. The way to correct the problem goes like this, but unless we can pin down what caused it in the first place, it'll probably just keep happening :-( ...

**1. Make certain the array isn't damaged**
An **mdadm --detail /dev/md0** (or whatever) should spit something like this at you:```
State : clean, degraded
```The word "clean" _absolutely must_ be there. If it's not, you need to dismount and stop using the array immediately.

**2. Re-add the missing device**
Treat the missing component device as though you just bought it. If you like, you can erase it (to prevent mdadm spitting warnings at you). Add the device back into the array, and give it a few moments to start the reconstruction process.

---

### Post by snobel on 2007-05-28
This may help: When you have reassembled your array(s), and checked that everything is OK, run
```
/usr/share/mdadm/mkconf > /etc/mdadm/mdadm.conf
```
That should regenerate your config file using the UUIDs of the devices...

---

### Post by obley on 2007-05-28
hello again kidders, your becoming my personal hero

no kernel updates, or BIOS config changes. and another reboot and they are back to that order again.

as requested:

```
mmoser@darcy:~$ sudo mdadm --detail /dev/md0
mdadm: cannot open /dev/md0: No such file or directory
mmoser@darcy:~$ sudo mdadm --query /dev/sda
/dev/sda: is not an md array
/dev/sda: device 0 in 2 device undetected raid1 /dev/.static/dev/md0.  Use mdadm --examine for more detail.
mmoser@darcy:~$ sudo mdadm --query /dev/sdb
/dev/sdb: is not an md array
/dev/sdb: device 1 in 2 device undetected raid1 /dev/md0.  Use mdadm --examine for more detail.

```

and more info as suggested:
```
mmoser@darcy:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              27G  708M   25G   3% /
varrun                252M  172K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M   88K  252M   1% /proc/bus/usb
udev                  252M   88K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
/dev/sdd4              96M  216K   96M   1% /media/zip
mmoser@darcy:~$ sudo mdadm --examine /dev/sdb
/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c7039661:3778aeb3:0e5fc3b5:00397e74
  Creation Time : Tue May 22 12:07:24 2007
     Raid Level : raid1
    Device Size : 245117312 (233.76 GiB 251.00 GB)
     Array Size : 245117312 (233.76 GiB 251.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sun May 27 15:04:25 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 518a101e - correct
         Events : 0.14


      Number   Major   Minor   RaidDevice State
this     1       8       16        1      active sync   /dev/sdb

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
mmoser@darcy:~$ sudo mdadm --examine /dev/sda
/dev/sda:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c7039661:3778aeb3:0e5fc3b5:00397e74
  Creation Time : Tue May 22 12:07:24 2007
     Raid Level : raid1
    Device Size : 245117312 (233.76 GiB 251.00 GB)
     Array Size : 245117312 (233.76 GiB 251.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sun May 27 15:04:25 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 518a100c - correct
         Events : 0.14


      Number   Major   Minor   RaidDevice State
this     0       8        0        0      active sync   /dev/sda

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
mmoser@darcy:~$

```

attached is the dmesg, I grepped for fail and the rest is greek :(

---

### Post by obley on 2007-05-28
thank you much! I will once I figure out why the devices are switching around on reboots.

---

### Post by obley on 2007-05-28
> **obley said:**
> attached is the dmesg, I grepped for fail and the rest is greek :(

I *thought* I attached it...  trying again


(the txt file was to big and I missed the error msg)

---

### Post by kidders on 2007-05-28
> **obley said:**
> hello again kidders, your becoming my personal heroLol!

This is all very confusing. One thing seems to say /dev/md0 is away with the faries, but another claims it's active. :confused: The dmesg you posted doesn't seem to want to help. :-( It's 02:30 here, so I might just be half asleep, and missing something obvious. Hmmmm...

---

### Post by obley on 2007-05-28
confusing indeed.

get this, Looking into snobel's suggestion I ran /usr/share/mdadm/mkconf and it displayed a device, so I added that line into the mdadm.conf (didn't actually have any devices listed in it to begin with)

and now everything is back up and running.

I even rebooted a second time and pinched my arm.

---

### Post by kidders on 2007-05-29
> **obley said:**
> Looking into snobel's suggestion I ran /usr/share/mdadm/mkconf and it displayed a device, so I added that line into the mdadm.conf (didn't actually have any devices listed in it to begin with)

and now everything is back up and running.Excellent. :-) When I saw snobel's suggestion, my first thought was "Huh? An mdadm.conf is not required for RAID to work." ... I, for instance, never bother to create one (at least not very precisely). Now that I'm awake though, I can think of quite a few situations where a system might find it handy to have everything spelled out. Thanks snobel!

---

### Post by obley on 2007-05-29
the mdadm.conf was on my list of things to research and figure out how to properly configure. mkconf is extreemly useful.

Now I want to figure out why my dev assignments are flopping around between the onboard IDE and promise card. I think I'll start a new post since it seems to not be specifically related to my RAID

---

### Post by kidders on 2007-05-29
> **obley said:**
> I want to figure out why my dev assignments are flopping around between the onboard IDE and promise card. I think I'll start a new post since it seems to not be specifically related to my RAIDIt's certainly odd hehe. Ordinarily, all things being equal, assigned /dev names will stay the same from one boot to the next. From time to time though, various things can crop up that can introduce an element of apparent randomness. For instance, I installed Dapper on a server a couple of weeks ago. I've only rebooted the machine once since then, but what *was* eth1 (immediately after installation), is now eth2 (after the reboot). I have no idea what it'll be called the next time!

xorg.conf, RAID & /etc/fstab are good examples of places where this unpredictability can be irritating.

In Windows terms, if you plug in a USB hard disk or something, you won't necessarily be sure what drive letter(s) it'll get assigned. /dev works in a similar way. You can however...[LIST]
[*]Force its hand (with udev rules).
[*]Find ways around the issue (with UUIDs).[/LIST]/dev names are still handy, because they're quick & easy to type, but you have to be wary ... just like you would if you created a batch script in Windows with something like **del H:\*.*** in it.

Anyhow, like you said, this is really a discussion for another thread.

[SIZE=1][COLOR=Silver][*[UAResolved]*]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR][/SIZE]

---

