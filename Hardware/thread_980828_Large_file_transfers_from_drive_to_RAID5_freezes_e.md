---
title: "Large file transfers from drive to RAID5 freezes everytime"
date: 2008-11-13
forum: Hardware
---

### Post by panfist on 2008-11-13
edit4: I have repeated the bug on ext2. It has nothing to do with XFS I guess.

I built two systems to backup data. They are identical. It's an AMD X2 on a Biostar 780G motherboard, 2GB RAM, 6x Seagate SATA hard drives and 1x PATA hard drive I had laying around. I installed Ubuntu server on one, and imaged that installation to the second machine.

The RAID array performs flawlessly on the first machine. I cannot get the RAID array to work on the second machine. I get the same problem over and over, where file transfers will spontaneously stop and I do not know how to recover from this. Every single time I start a large transfer, this happens. And every single time this happens, I have to re-synchronize the RAID array which takes about 8 hours.

I would like to get to the root of the problem. But I would also like to figure out how to cleanly recover from the problem. I do not know a method to cleanly cancel the borked file transfer and unmount the drive. I cannot unmount because it says it is busy, even after I have exhausted my options trying to close down any process related to the transfer.


*thread history*
-------------------

edit3: it appears that this is a bug in the XFS file system. see the last post.

edit2: I would also like to add that several times over the last couple of days I have tried to disable power management on my hard drives with the following command: "sudo hdparm -B 255." For each of the drives in the array, I got something like:
HDIO_DRIVE_CMD failed: Input/output error. I'll get the exact error message later today.

The last few weeks I have been experimenting with raid 5 unsuccessfully. I have a 4 disk level 5 array that I have built and re-built using various options and file systems. 

Every time I initiate a large transfer it works fine at first, but then after it has transferred about 10GB or more the transfer rate starts to decline until it just freezes. 

Last night I initiated a 150GB transfer that got to 145GB in 1.5 hours, then stayed there for 8 hours. When I tried to cancel the transfer nothing happened. I had to force quit nautilus.

I tried to unmount the array and I can't because it's busy, but it's not doing anything. 

Can I get some more verbose feedback by initiating the file transfer from the command line?

There is nothing in dmesg--the last line in dmesg is the clean mount of the RAID array file system.

---

### Post by iponeverything on 2008-11-13
> **panfist said:**
> The last few weeks I have been experimenting with raid 5 unsuccessfully. I have a 4 disk level 5 array that I have built and re-built using various options and file systems. 

Every time I initiate a large transfer it works fine at first, but then after it has transferred about 10GB or more the transfer rate starts to decline until it just freezes. 

Last night I initiated a 150GB transfer that got to 145GB in 1.5 hours, then stayed there for 8 hours. When I tried to cancel the transfer nothing happened. I had to force quit nautilus.

I tried to unmount the array and I can't because it's busy, but it's not doing anything. 

Can I get some more verbose feedback by initiating the file transfer from the command line?

There is nothing in dmesg--the last line in dmesg is the clean mount of the RAID array file system.

Yes, there is a good possibility that you can get get some extra feedback if you initiate the transfer from the command line.

I would also open another terminal "cd /var/log" and have this running
"tail -vf debug messages syslog daemon.log kern.log user.log"

open another terminal and when it starts to bog down, maybe before it locks up -- run "strace -p <pid>" where <pid> is the pid of the copy process.

---

### Post by panfist on 2008-11-13
> **iponeverything said:**
> Yes, there is a good possibility that you can get get some extra feedback if you initiate the transfer from the command line.

I would also open another terminal "cd /var/log" and have this running
"tail -vf debug messages syslog daemon.log kern.log user.log"

open another terminal and when it starts to bog down, maybe before it locks up -- run "strace -p <pid>" where <pid> is the pid of the copy process.

Thanks for the information. I will try it later tonight when I get home.

---

### Post by panfist on 2008-11-17
Ok I tried a few things and I'm still not sure what's going on.

Firstly I rebuilt the array from scratch, and even though I had a totally fresh array, /proc/mdstat tells me that it's resyncing because one of my disks is gone and it's rebuilding onto a spare. I don't know how that happened, but I let it resync (took like 4 hours). I had more problems with resyncing later.

The tail -vf didn't tell me anything useful. The last thing I saw in there about the array was the clean mount. 

watch -n 1 cat /proc/mdstat showed that the array was OK even after the transfer to it had stopped.

I didn't use mv from the command line, instead I moved the drive to another machine because ubuntu would no longer read it. Details are here: [http://ubuntuforums.org/showthread.php?t=981450](http://ubuntuforums.org/showthread.php?t=981450).

I started vsftpd on the ubuntu machine and initiated a transfer from my windows machine with an ftp client. I observed a transfer rate of 30-70MB/s, depending on individual file size, which I guess is an acceptable speed over an untweaked gigabit link.

Then I saw that the speed went down to zero. I ran strace on vsftpd and I saw a bunch of reads and write flying by. It seemed that the very action of attaching to the process made it start going again. 

About 15 minutes later the transfer speed again went to zero. I looked at system monitor, did strace, looked at /proc/mdstat...and it randomly went back up again. At this point I had to go to bed, and now I see that the transfer stopped about 15 minutes later and timed out for the entire night.

I was unable to get another transfer going at all. I tried restarting vsftpd but that didn't work. I tried rebooting, but for some reason when I send a "sudo shutdown -r now" remotely, the system never shuts down all the way. When I connect a monitor to it after waiting 10 minutes for it to shutdown, I get nothing, not even a blank screen, just absolutely no output. Is this a bug with VNC, or is there something wrong with the raid array that's causing an incomplete shutdown? I hit the reset button, connected again via VNC and see that /proc/mdstat tells me the RAID array is resyncing!! Last time I rebooted, the raid array looked like sda[3] sdb[2] sdc[1] sdd[0]. Now, mdstat says sda[3] sdb[0] sdc[1] sdd[2].

-----

I really wish I had some idea of what is going on. I've been reading any material about mdadm that I can get my hands on and nothing mentions any problems like this.

---

### Post by iponeverything on 2008-11-17
> About 15 minutes later the transfer speed again went to zero. I looked at system monitor, did strace, looked at /proc/mdstat...and it randomly went back up again. At this point I had to go to bed, and now I see that the transfer stopped about 15 minutes later and timed out for the entire night.


Attaching a strace makes start going again! Man that is strange.

Does the issue appear moving data around on the array?  i.e. copy 200 Gigs from one directory in to another? How about Copying or moving data off of the array onto a local disk? The system is not giving you much feedback -- thats for sure.  Maybe we can try messing with DMA..

---

### Post by IndieRockSteve on 2008-11-17
If I read your posts correctly, you've been using ftp to transfer the files. I'm going to recommend using rsync instead. Two reasons, while ftp in theory should be fine for such large files, there may be issues going on that have nothing to to do with RAID and everything to do with ftp. The second is that rsync will allow you to leave a partial file so that if the initial transfer still fails you can run the command again and it will continue to write the file from the point it left off, AND allow for some level of verification that the file is an equal match.


As for the other issues.... I've got two computers running mdadm RAID5 arrays and both have no issues shutting down cleanly, so it seems something is amiss there. I would highly suggest sitting at the actual computer with a monitor connected during a shutdown to see what is going on. When I first started playing with RAID and had a similar shutdown issue, this is the only thing that helped me figure out what was wrong.
From what I remember, the drive order doesn't matter, I think it has something to do with which drive gets "found" or "initialized" into the array which determines the order.

---

### Post by panfist on 2008-11-17
> **IndieRockSteve said:**
> 
From what I remember, the drive order doesn't matter, I think it has something to do with which drive gets "found" or "initialized" into the array which determines the order.

I can't answer anything else in your post now because I am at work, but I'd like to address this point. I will definitely try out rsync.

I can't find the citation, but I remember reading in the linux raid wiki that when an array sync is complete the drive numbers are swapped to the correct numbers. Why would they bother swapping the numbers if the numbers had no effect on the structure of the array?

Also, I can think of no other explanation as to why the array would need to be synced except for these numbers being different.

As far as shutting down remotely, isn't there a way to save the output that's written during shutdown to a file for later review? I will definitely have a monitor plugged in tonight when I am working on the array, but for future reference, I would like to keep a permanent record of booting up and shutting down, at least for 7 to 30 days or so.

edit: I would also like to add that several times over the last couple of days I have tried to disable power management on my hard drives with the following command: "sudo hdparm -B 255." For each of the drives in the array, I got something like:
HDIO_DRIVE_CMD failed: Input/output error. I'll get the exact error message later today.

---

### Post by panfist on 2008-11-17
I just now initiated a file transfer with rsync. Things seem to be going well except that my performance isn't as good as it was with vsftpd...so far. If the transfer completes, I'll be happy, but the max transfer speed is very low.

With vsftpd running on the server, and an ftp client on another machine pushing files into the server, I was getting 30-60MB/s depending on the file size...large files would transfer at a steady 60MB/s but smaller files of around 100MB or less would transfer at a more inconsistent rate.

With rsync, I'm getting a steady 20MB/s. That is with the files mounted as a samba share on the ubuntu box with the array. I'm guessing the crappy performance of rsync has to do with the way I mounted the files. I only did this because I was too lazy to configure an ssh server on the windows machine and connect rsync with it via shell.

This performance is pretty crappy so far. While something is transferring I will probably try to figure out how to get ssh server running on my windows machine.

---

### Post by panfist on 2008-11-17
well I am happy to reply that so far no transfers have borked using rsync.

My performance is still a steady 15-20MB/s. I will experiment with rsync some more. If anyone can recommend any performance tuning guides that would be awesome.

---

### Post by IndieRockSteve on 2008-11-18
> **panfist said:**
> I can't answer anything else in your post now because I am at work, but I'd like to address this point. I will definitely try out rsync.

I can't find the citation, but I remember reading in the linux raid wiki that when an array sync is complete the drive numbers are swapped to the correct numbers. Why would they bother swapping the numbers if the numbers had no effect on the structure of the array?

Also, I can think of no other explanation as to why the array would need to be synced except for these numbers being different.

As far as shutting down remotely, isn't there a way to save the output that's written during shutdown to a file for later review? I will definitely have a monitor plugged in tonight when I am working on the array, but for future reference, I would like to keep a permanent record of booting up and shutting down, at least for 7 to 30 days or so.

edit: I would also like to add that several times over the last couple of days I have tried to disable power management on my hard drives with the following command: "sudo hdparm -B 255." For each of the drives in the array, I got something like:
HDIO_DRIVE_CMD failed: Input/output error. I'll get the exact error message later today.

Right, the order is written in the array, but is just a random ordering (my arrays don't go a,b,c,d,e,f either). Once the array is written and mdadm puts the array together on next boot it will look for all those drives and assemble the array as appropriate.

I think why your having to resync is that the partition on the array is not unmounting properly so the array can not safely be stopped before poweroff. It is similar to what happens on one of my systems without a UPS that loses power, it spends the next ~4hrs rebuilding the array.

From what I've noticed, at a certain point in the shutdown (after the drive capable of writing logs is unmounted) no log information is shown. It was exactly this issue that caused me to  sit at the computer with a monitor when I was having shutdown issues. There very well may be a way to get around this, but I don't know what it is. Otherwise the normal system logs will contain all that information.

*<edit>*Oh, as for the hdparm issue, perhaps your drives don't allow APM to be disabled? the only thing I know is that mdadm changes how sleep management works, i forget if it completely disables it or what exactly though.

---

### Post by IndieRockSteve on 2008-11-18
> **panfist said:**
> I just now initiated a file transfer with rsync. Things seem to be going well except that my performance isn't as good as it was with vsftpd...so far. If the transfer completes, I'll be happy, but the max transfer speed is very low.

With vsftpd running on the server, and an ftp client on another machine pushing files into the server, I was getting 30-60MB/s depending on the file size...large files would transfer at a steady 60MB/s but smaller files of around 100MB or less would transfer at a more inconsistent rate.

With rsync, I'm getting a steady 20MB/s. That is with the files mounted as a samba share on the ubuntu box with the array. I'm guessing the crappy performance of rsync has to do with the way I mounted the files. I only did this because I was too lazy to configure an ssh server on the windows machine and connect rsync with it via shell.

This performance is pretty crappy so far. While something is transferring I will probably try to figure out how to get ssh server running on my windows machine.

It could be the remote mounting. SAMBA/NFS can have their own speed issues. You can run an rsync daemon on the receiving machine and do the transfer completely via rsync over the network instead of as a local transfer over a network mount.

---

### Post by panfist on 2008-11-19
The problem happened again. I was using rsync and the progress of the file transfer just stopped. I could not kill rsync, and I couldn't think of anything else to do. Unmounting wouldn't work because rsync had a file open on the array. I tried to reboot and I don't think that worked cleanly because it never actually powered down, it left me at a blank screen with a blinking cursor.

When I did a hard reset, the array began resyncing when the system came up.

---

### Post by panfist on 2008-12-05
I think I have found the root of the problem finally.

It appears to be a bug in the XFS file system. I have been experimenting with RAID arrays on three physical systems using a total of 16 different disks, and this problem comes up exclusively when using the XFS file system; ext2 never chokes in this way.

I would like to file a bug report, but I've never done that before. I'll do some research and try my best.

---

### Post by iponeverything on 2008-12-05
Cool, I am glad that you managed to narrow it down.

---

### Post by IndieRockSteve on 2008-12-07
> **panfist said:**
> I think I have found the root of the problem finally.

It appears to be a bug in the XFS file system. I have been experimenting with RAID arrays on three physical systems using a total of 16 different disks, and this problem comes up exclusively when using the XFS file system; ext2 never chokes in this way.

I would like to file a bug report, but I've never done that before. I'll do some research and try my best.


very interesting.there is a known issue with XFS on large file systems where if you use more than something like 95% of the file space it has problems. I wonder if this is the issue your running into. Because XFS has some definite advantages for large file systems I use it for my two large RAID5 arrays I just make sure to steer clear of using up all the file system.

You can also try JFS, its also good with large file systems, though has some disadvantages with large files.

---

### Post by panfist on 2008-12-08
> **IndieRockSteve said:**
> very interesting.there is a known issue with XFS on large file systems where if you use more than something like 95% of the file space it has problems. I wonder if this is the issue your running into. Because XFS has some definite advantages for large file systems I use it for my two large RAID5 arrays I just make sure to steer clear of using up all the file system.

You can also try JFS, its also good with large file systems, though has some disadvantages with large files.

I don't think I had this problem because I had initiated these file transfer on newly formatted file systems. The error occurred less than 100GB into a 5TB file system.

---

### Post by panfist on 2008-12-11
Please see the OP. I put the update on top.

---

### Post by panfist on 2008-12-15
I'm still perplexed by this problem.

---

### Post by blackoper on 2008-12-19
hmm I kind of have the exact same problem. I have a 5 disk raid 5 array using 500GB drives. It's half full and I can't complete large transfers either (usually dies around 5gb in).I then have to reboot to get the drives to work again. No messages that I can find in the logs.
 I have a 2nd raid0 that has no problems. Anytime I do large transfers of HD video between the two the raid5 freezes (does the same thing with samba to other pcs) The raid 5 and the raid 0 are running XFS but the raid0 works with no problems.

---

### Post by panfist on 2008-12-22
Hi blackoper, welcome to the thread. I'm continuing to experiment, and if I learn anything new I'll come back with info.

---

### Post by blackoper on 2008-12-22
I'm going to put some time into tracking this down on wednesday or thursday. I have enough storage available that I may just try to wipe the whole thing/format/remove superblocks and start over.

Possible things causing mine: 
1. drives are in a hot-swap enclosure that appears to be working ok but who knows there. I'll pull them out and hook directly up to the sata ports
2. I use a tool called spindown to turn these drives off after 2 hours ( i don't think it's causing it)
3. I had a drive go bad and had to replace it about a month ago. maybe it messed with the file structure because it was corrupting data instead of being removed from array but the vidoe files seem ok and xfs_check doesn't find anything wrong.
4. maybe the motherboard's sata interfaces are bad. I have a pci-e card and a port multiplier that I'll try out as well.
5. I'll be upgrading to ubuntu 8.10 64 bit anyway so maybe the kernel change will help.

---

### Post by panfist on 2008-12-23
> **blackoper said:**
> 
Possible things causing mine: 
1. drives are in a hot-swap enclosure that appears to be working ok but who knows there. I'll pull them out and hook directly up to the sata ports
2. I use a tool called spindown to turn these drives off after 2 hours ( i don't think it's causing it)
3. I had a drive go bad and had to replace it about a month ago. maybe it messed with the file structure because it was corrupting data instead of being removed from array but the vidoe files seem ok and xfs_check doesn't find anything wrong.
4. maybe the motherboard's sata interfaces are bad. I have a pci-e card and a port multiplier that I'll try out as well.
5. I'll be upgrading to ubuntu 8.10 64 bit anyway so maybe the kernel change will help.


1.) This wasn't the problem in my case. When I unplugged a drive, it showed up in /proc/mdstat
**2.) I thought this might be the case. I don't know if my drives support it or not, but I could not set their power management with hdparm**
3.) I don't think a bad drive could have messed with the file structure because I have started from scratch dozens of times and I get this error.
4.) I doubt this because I have two setups on identical hardware and one works...one doesn't. Another setup on different hardware just works.
5.) I have tried on 8.04 32/64 bit, and 8.10 32/64 bit. All four did not work.

---

### Post by TrinitronX on 2009-01-25
I'm having this same problem with Mythbuntu 8.10 on an AMD 64bit system (and kernel).

Here's why it seems to be the same **exact** problem:
I am using three 750GB SATA drives in a RAID-5 array.
I am using mdadm for the software raid.
I see the same problem after a certain amount of time for LARGE file transfers. (happened both of last 2 times transferring 28GB from an external USB drive to the raid array)

I also noticed that both times it has done it after the screen blanks (for powersave)

After I move the mouse, the program (no matter which of: thunar, dolphin) that is doing the file transfer has a completely white window.  I just tried running htop to investigate this, but the program won't even open... the terminal has hung.  I switch over to another desktop to see if I can do things in mythtv's frontend, and it works until I do something that tries to access the drive.  Then this is hung, and I cannot even move to another desktop.

[s]Apparently ubuntu's kernel does not have the CONFIG_MAGIC_SYSRQ option enabled[/s], or the kernel simply does not respond to the Alt+SysRq+[REISUB] key sequence during this freeze.  (See [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key))

Edit: Looking in my /var/log/syslog, I see some interesting lines before the hard reboot.  I have attached these in: [http://pastebin.com/f5fec8a6b](http://pastebin.com/f5fec8a6b)
After reboot, a `cat /proc/sys/kernel/sysrq` returns 1.  So it appears that Magic SysRq key commands **are** enabled, but the kernel is too frozen to even respond to them.
The program used to transfer files in this syslog was kde's "dolphin".  Lockups & beginning of what looks like stack traces are hilighted.  Within stack traces, you can see it's definitely XFS related.

---

### Post by TrinitronX on 2009-01-29
I have just successfully transferred the same 28.9GiB of data that I had attempted before!!

Beforehand, I opened up gconf-editor, went to "apps -> gnome-screensaver", and unchecked "idle_activation_enabled".   This turned off the screensaver function for me, and avoids this problem it seems (so far).

From the results of these 3 tests I have done, signs are pointing towards the gnome-screensaver triggering some sort of problem with XFS+RAID5.

Any of you submitted a bug report on this yet?

---

### Post by panfist on 2009-03-01
> **TrinitronX said:**
> I have just successfully transferred the same 28.9GiB of data that I had attempted before!!

Beforehand, I opened up gconf-editor, went to "apps -> gnome-screensaver", and unchecked "idle_activation_enabled".   This turned off the screensaver function for me, and avoids this problem it seems (so far).

From the results of these 3 tests I have done, signs are pointing towards the gnome-screensaver triggering some sort of problem with XFS+RAID5.

Any of you submitted a bug report on this yet?

I have not because I was never confident it was a bug...and if it was a bug, a bug in which software?

I get the problem with XFS and ext2/ext3.

---

### Post by dbenc on 2009-05-17
I am also having this problem on a fresh install of Ubuntu jaunty x64 ... I am using rsync to restore about 600gb of files off of an external hard drive, and it freezes consistently before completing, requiring a hard reboot ... it then starts to rebuild the array ...

This is on a 4-disk md raid 5 with an encrypted LVM and EXT4 (though it seems the problem in at the MD layer) ... I did not see anything useful in my log files ... 

any suggestions? has a bug report been filed?

---

### Post by panfist on 2009-05-22
I have not filed a bug report. I've never filed a bug report before. Honestly I'm kind of afraid of doing it incorrectly.

It's quite a scary bug. Part of me thinks that it must be something to do with our unique hardware configurations because Linux raid is used all over the place in critical installations, and a bug like this wouldn't last long...I don't know...

---

### Post by dbenc on 2009-05-22
The problem is not knowing what to report ... I havent been able to reproduce the freezing consistently, and after a reboot there isnt anything in the log files ... 

ive tried leaving "tail -vf messagese kern.log dmesg syslog" in /var/log running fullscreen when I am away, to see if the error is at least printed to the screen before everything crashes ...

does anyone have any advice on isolating this kind of bug?

---

### Post by panfist on 2009-05-22
> **dbenc said:**
> The problem is not knowing what to report ... I havent been able to reproduce the freezing consistently, and after a reboot there isnt anything in the log files ... 

ive tried leaving "tail -vf messagese kern.log dmesg syslog" in /var/log running fullscreen when I am away, to see if the error is at least printed to the screen before everything crashes ...

does anyone have any advice on isolating this kind of bug?

That is the exact same problem I had! I could find NO indication that anything wrong was happening...the transfer would just hang. The most information I found out was when I did a trace of a copy command (or maybe it was rsync?), the trace output just stopped coming.

---

### Post by dbenc on 2009-05-23
I have been using rsync to copy off of an external drive ... are you using LVM or encryption? maybe that is a factor ...

---

### Post by panfist on 2009-05-25
No LVM, no encryption.

Also, this has happened when I assembled the array from partitions on my drives or when I assembled the array from the raw drives.

---

