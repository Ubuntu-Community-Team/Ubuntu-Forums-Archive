---
title: "trying to recover data from external hard drive"
date: 2011-06-15
forum: Hardware
---

### Post by piedrafina on 2011-06-15
hi all! this is my first post here, so i apologize if this has been answered somewhere else or if the question is overly simple. i am a linux noob as well. :D i have posted on a few other forums, but have made no progress, so i'm hoping someone here can help me.
 
i have a western digital external hard drive that started giving me an i/o error, then progressed to asking me to format in order to be able to use it. i was always able to disconnect and reconnec the drive and have access to my files. i bought a replacement drive as i realized the old one was on its last leg. as luck would have it, the old one died before i could get the new one installed. it doesn't show up on my computer, so i am just trying to get the files off of it at this point. i am hoping i can do this using ubuntu as windows programs and utilities have been of no help. i saw several posts on the western digital forums where people were able to save their data using ubuntu, so i'm keeping my fingers crossed.
 
in windows, it shows in the safely remove hardware area, but with no drive letter (just shows as My Book). it shows also in disk management as unallocated with a capacity of 0.0. it also shows as not initialized, but i can't initialize it. (i get an i/o error). none of the data recovery, partition recovery, etc software are able to do anything with the drive at all. some can't even see it.
 
this is how far i have gotten in linux:
i downloaded ubuntu, burned it to a dvd and booted to that. i went into the disk utility section and i can see my old drive. it shows as /dev/sdc, but shows as not partitioned. 
 
i opened the terminal window and entered the mkdir command (i created /media/mybook) and then tried to mount it, but i get an error. when i enter fdisk -l, my external drive doesn't show up. i only see sba and sbb.
 
is my old drive totally borked? i am hoping it isn't. there are some priceless memories on there. :( (i have other info, but i don't wanna make this post too long, so if you need some info to help answer my question, please ask.)

---

### Post by piedrafina on 2011-06-16
***bump***

can anyone help?

---

### Post by doas777 on 2011-06-16
well the first thing you want to determine is whether the issue is a hardware problem with your disk, or a filesystem issue that can be repaired with software.

in ubuntu, use Disk Utility to check the SMART data for the drive. are any of the metrics in failing or pre-fail state?

if the issue is hardware, then your best bet is to use [ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html") to take an image of the drive. then you can write that image out to a new location, and if it still exibits issues, you can use data recovery tools like photorec and testdisk. 
to do this you will need another drive with at least the same amount of space as the drive you are imaging. 

the last failing drive i worked with was only partially recoverable, becuse the user didn't bring it to me soon enough. by the time i got half an image off it, the drive had irreparably failed. 

here is the ubuntu documentation for data recovery. if you have any questions, please let us know
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by doas777 on 2011-06-16
any luck?

---

### Post by piedrafina on 2011-06-16
nothing in the disk utility window say anything about failing.  the smart status says not supported, it says capacity 0.0 and also says it is not partitioned.

i am going to read the data rescue info and look at ddrescue now.

thanks for the advice!  i will post back with results.

---

### Post by piedrafina on 2011-06-17
ok, i clicked on the links you provided, but i still have made no progress.  i am a total linux noob, so i don't know how to acquire or install testdisk or gparted.  i am booting from a cd and i know that i have a gparted option under administration.  however, my dying drive doesn't show up there at all.

could you maybe give me simplistic instructions?  i am fairly computer savvy, just not in linux.

thanks so much!

---

### Post by doas777 on 2011-06-17
> **piedrafina said:**
> nothing in the disk utility window say anything about failing.  the smart status says not supported, it says capacity 0.0 and also says it is not partitioned.

i am going to read the data rescue info and look at ddrescue now.

thanks for the advice!  i will post back with results.

well that is not a good sign. what kind of filesystem was on the drive? linux ext4 or windows ntfs?

also please keep in mind, data recovery is very very complicated stuff. it is not for the n00b or for the faint of heart, so don't feel  bad if it is confusing. we'll do our best to help, but be aware, when dealing with data recovery, you need to be prepared to accept the loss of data at some point. there are absolutely no guarantees. 

when doing data recovery you need a second hard disk that is at least the size of the one you are attempting to recover. do you have one? if not see if you can borrow one from a friend. make sure they are aware that any data they had on it will be erased.

ddrescue is a tool that will make a perfect copy of your hard disk bit-by-bit, but unlike dd, it will attempt to recover data from damaged sectors of your disk. 

so, the goal is to use ddrescue to make a perfect copy of your hdd, on another disk. 
then you can either use the new disk if it is sufficiently repaired, or you can use tools like photorec to recover files off it if the filesystem cannot be repaired.

we'll get to recovering data after we have an image of your disk. 

1) install or plug in the new drive, that you will be copying your data to. 

2) download the ubuntu live CD or another liveCD that has ddrescue installed,  and boot off it. if you are using the ubuntu live cd, then install ddrescue via software center.

3) determine the /dev name of the drive/partition of the bad disk (/dev/sdc1 for instance) and the name of the new drive that you want to copy too.

4) run 'mount' to make sure that neither of the disks identified in #3 are mounted. you cannot use dd on a mounted volume. 

5)mount your internal disk to somewhere in media, or plug in a thumb drive. you need a place to store your logfile, that is not on either of the drives mentioned in #3/4.

6) run these commands one at a time, filling in the names of your source and dest devices, and your log file path (first /dev is the failing drive, the second is your new destination drive):
```

ddrescue -f -n /dev/hdS /dev/hdD <path/to/logfile>
ddrescue -d -f -r3 /dev/hdS /dev/hdD logfile

```

note, these command will take hours or even days to complete. be patient. 

6) once you have your new disk filled with recovered data, we want to perform a filesystem integrity scan using fsck/e2fsck for ext2/3/4 or windows chkdsk for ntfs partitions. 
for fsck, run this command:
```
sudo fsck -f /dev/hdD1 
```
if the disk is ntfs, then scan it for errors within windows. 

7) reboot and see if the new disk appears to the liveCD. if it does, mount it and check to see if your files are intact.

if not, then post back and we'll walk you through photorec. note that since your disk is failing, photorec woudl push it over the edge past the point of recovery, so tahts why we need to image it to the new disk first. 

good luck.

---

### Post by piedrafina on 2011-06-18
first of all, thank you SO VERY MUCH for the detailed explanation.  this was awesome!  i can't tell you how much i appreciate the time you took to do that.


i got part of the way through this but hit a snag, so i'll use your instructions to explain.

> **doas777 said:**
> well that is not a good sign. what kind of filesystem was on the drive? linux ext4 or windows ntfs?

i am not really sure.  i was using windows before, so i'm going to guess ntfs.  although one of the data recovery programs i tried showed it as fat12.


> when doing data recovery you need a second hard disk that is at least the size of the one you are attempting to recover. do you have one? yes i do


> 1) install or plug in the new drive, that you will be copying your data to. 

2) download the ubuntu live CD or another liveCD that has ddrescue installed,  and boot off it. if you are using the ubuntu live cd, then install ddrescue via software center.

3) determine the /dev name of the drive/partition of the bad disk (/dev/sdc1 for instance) and the name of the new drive that you want to copy too.

4) run 'mount' to make sure that neither of the disks identified in #3 are mounted. you cannot use dd on a mounted volume. 

5)mount your internal disk to somewhere in media, or plug in a thumb drive. you need a place to store your logfile, that is not on either of the drives mentioned in #3/4.done.  
i created a directory (/media/internaldrive) and mounted my internal drive (/dev/sda1) to it.  
the failing drive is /dev/sdc and the new drive is /dev/sdb 


> 6) run these commands one at a time, filling in the names of your source and dest devices, and your log file path (first /dev is the failing drive, the second is your new destination drive):
```

ddrescue -f -n /dev/hdS /dev/hdD <path/to/logfile>
ddrescue -d -f -r3 /dev/hdS /dev/hdD logfile

```note, these command will take hours or even days to complete. be patient. here is where i hit the snag.  after typing the first line, i get:
```
ubuntu@ubuntu:~$ ddrescue -f -n /dev/sdc /dev/sdb /media/internaldrive
ddrescue: invalid option -- f
Try `ddrescue --help' for more information.
```when i looked at the help information, i don't see a lowercase f.  only an uppercase.  since i don't want to mess anything up, i thought i'd post back before making assumptions.

---

### Post by doas777 on 2011-06-18
ok, I was going off gnu documentation so there have probably been changes over the years. I also forgot sudo :(

so then lets try these slight variations:
```

sudo ddrescue -n /dev/sdc /dev/sdb /media/internaldrive/logfile 
sudo ddrescue -d -r3 /dev/sdc /dev/sdb /media/internaldrive/logfile 

```

---

### Post by piedrafina on 2011-06-18
here is what i got for both:

```
Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:         0 B,  errsize:       0 B,  current rate:        0 B/s
   ipos:         0 B,   errors:       0,    average rate:        0 B/s
   opos:         0 B,     time from last successful read:       0 s
Finished 
```:eek: that scares me. :confused:  please tell me that doesn't mean that there is nothing left on that drive. :cry:

i did a google search and read a little about ddrescue and some of the documentation i read showed the logfile with a .log extension.  i tried that as well and still got the same results as above.

what do i do now?

---

### Post by doas777 on 2011-06-19
> **piedrafina said:**
>  that scares me. :confused:  please tell me that doesn't mean that there is nothing left on that drive. :cry:


well, I hate to say it, but that is not good at all. I think it's not saying that it sees no data. ddrescue would gladly copy 20GB of data off a blank 20GB drive. it sees raw bits, not data per se. what that output is saying is that the total capacity of the disk is 0b. 

the only reasonable user-servicable recommendation I can make is to remove the disk from its enclosure and plug it directly into your motherboard, on the off chance that the problem is with the ide/sata => usb circuitry, but that is a longshot.

There may still be things that can be done, but they also involve hardware, and go beyond what most users would do to recover personal files. 

My first hunch is that this is a controller failure. if you can find an identical hard disk, you may be able to swap the controller circuitry on the bottom of the hdd module (if it is exposed) but that may require some soldering. if you are successful, you could then check to see if the drive itself still contains data. Note: when tinkering with hdd internals, do not break the vaccum seal around the disk enclosure. here is some practical advice on swapping controller boards on hdds: [http://www.wikihow.com/Swap-a-Hard-Drive-Controller-Circuit](http://www.wikihow.com/Swap-a-Hard-Drive-Controller-Circuit)

unfortunately, until the actual disk contents can be accessed, there is nothing software can do to fix it. 

I'm Sorry mate. unless you catch it early, hardware failure is hard to recover from.

---

