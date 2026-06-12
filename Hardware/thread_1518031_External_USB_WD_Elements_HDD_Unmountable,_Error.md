---
title: "External USB WD Elements HDD Unmountable, Error"
date: 2010-06-25
forum: Hardware
---

### Post by Tiko on 2010-06-25
Hi all,

I'm using a 1 TB external HDD from Western Digital, Element series. Formatted as NTFS.

I was able to mount the drive and use it as normal in Karmic.

However, while creating folders within the drive recently, the drive unmounted itself silently. So after waiting for 2 mins, I unplugged the USB and replug it.
I have a VBOX windows XP running in background, not sure if the virtualized windows did anything to it...

And I got this error message and some instructions for windows system:

```
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```I can't even mount to check it.

Any one knows any software approach to handle this situation?

I really hope it's not a hardware fault, or I'll have to open up the casing, and prepare for the worst... :(

Edit:

Ok the HDD works fine with a Windows OS machine.
I'm just guessing a work around: Does anyone knows a way to reset the $MFT or MFTMirr records please?

Edit2:
Ok solved it using ntfsprogs package

Get package
```
sudo apt-get install ntfsprogs
```fix it
```
sudo ntfsfix /dev/sdb1
```Should fix immediately without reboot.
Replace the device path with your own error report's device path.

Reference:
[http://art.ubuntuforums.org/showthread.php?p=8627316](http://art.ubuntuforums.org/showthread.php?p=8627316)
[http://ubuntuforums.org/archive/index.php/t-1333205.html](http://ubuntuforums.org/archive/index.php/t-1333205.html)

Edit3:

Certain files that were being moved around before the silent unmounting event, now cannot be moved or deleted, but they can be copied and accessed.
```
Unable to trash file: Input/output error
Error removing file: No such file or directory
```Probably need a system restart... 

Edit4: There's still some inconsistency errors. My findings are the same with coffeecat: you need to plug it into the windows operating system to run checks for a proper fix. There are also some data corruption, though the exact number of files affected is unknown. Woe be me for NTFS...

---

### Post by viniciuscarvalho on 2010-07-27
Thought I lost everything... 1.2 TB of data, restored thanks to your post. ntfsfix did the trick. Thanks

---

### Post by ozPATT on 2010-10-15
saved me hours as well! Great post.

---

### Post by jaqian on 2010-10-30
after running **sudo ntfsfix /dev/sdb1**

I get this error...

**Refusing to operate on read-write mounted device /dev/sdb1**

any suggestion on how to fix this?

---

### Post by coffeecat on 2010-10-30
> **jaqian said:**
> any suggestion on how to fix this?

The ntfsfix manual (man ntfsfix) has this to say:

> ntfsfix is a utility that fixes some common NTFS problems. ntfsfix is NOT a Linux version of chkdsk.  It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows. You may run ntfsfix on an NTFS volume if you think it was damaged by Windows or some other way and it cannot be mounted.So you probably need to repair that filesystem with chkdsk from Windows. I'm surprised an earlier poster managed to fix the problem with ntfsfix alone.

One other thing to say: if what some posters in other threads are saying is correct, there are some WD Elements drives shipping with some oddity with the formatting which is causing problems. This can be solved by using Gparted to create a new partition table and then a new partition. This, of course, will lose you any data on the drive. Having said that I've used two Elements external drives formatted NTFS without problems, so I guess the issues in this thread are down to filesystem corruption caused by unclean unmounts. In which case, chksdk in Windows is your only definitive option.

---

### Post by jaqian on 2010-11-02
Thanks coffeecat, I have it fixed now. Very strange I kept repairing it with chkdsk /f in winXP but kept failing in Mint9. I eventually formatted it as ext3 then went into windows and reformatted as ntfs took literally _hours_ but is working fine now.

I think the problem may lie with gParted formatting as ntfs as once I got windows to do it, it seems ok.

Thanks

---

### Post by coffeecat on 2010-11-02
> **jaqian said:**
> Thanks coffeecat, I have it fixed now. Very strange I kept repairing it with chkdsk /f in winXP but kept failing in Mint9. I eventually formatted it as ext3 then went into windows and reformatted as ntfs took literally _hours_ but is working fine now.

You should have chosen the quick format option. That's if XP has the quick format option. Long time no see, you see. :wink:

> **jaqian said:**
> I think the problem may lie with gParted formatting as ntfs as once I got windows to do it, it seems ok.

I don't think the problem was necessarily with gparted because I've used Gparted to create NTFS partitions to be used as C: drives for XP, Vista and W7 as well as data drives and Windows has never demurred. But I'm glad you fixed it.

---

### Post by etraza on 2011-01-05
This was my first attempt at fixing a problem myself by researching online/reading posts... that u so much!!! I feel so proud now I could cry :cry: haha guess I can consider myself a real ubuntu user now :D Most importantly u really saved my life, was devastated at the thought of having possibly lost all the data on my xternal HD, would have been a disaster, seeing how it was my only backup and I've recently lost everything on my pc HD while installing ubuntu... thank u again, look forward to solving future problems and learning more with u guys!!! :KS ^_^

---

### Post by mabtifro2 on 2011-02-28
AMAZING fix!!! thanks so much, solution so simple, thank you x 1000000

---

### Post by Damascushead on 2011-06-15
Just got my WD elements drive yesterday and am having same mounting trouble as described. I'll have to try out these awesome suggestions.

ThankS!!!

:p

---

### Post by mon_r on 2011-08-08
Same thing here. WD 'My book' 1TB. Used to shut it down after use (unplug the adapter). But since I've moved to a new CPU, just had an error recently since I've kept it in standby and plugged. The old CPU scans USB devices and this would take forever so it was normally off. Luckily, it worked on my old Linux partition. Booted there and it can be read. I'll be unmounting this one again before shutdown from now on.

---

### Post by parastree on 2011-08-29
this worked like a knife through butter for me!  thanks!  worked for a seagate 250 gig external...

Eye hate macs!!!!!!!!  hooked my hard drive up to my nephews computer and suddenly my version of ub wont read my file system!  had to spend too long without my music before eye could sit down and find this thread!  any ideas why that mac locked me out?  how to prevent the same from happening again...

---

### Post by mon_r on 2011-09-15
@parastree: Not sure if this is true. It could be that the Mac also stores info on the hard drive like in Windows. And sometimes, if it was not ejected properly, still shows as in use and you can't use it until you plug it back to the machine that caused it and unmount it properly for safe removal. Plus Mac OS creates some hidden files in the drive. Open a file browser and look for hidden folders and files (Ctrl + h)

---

### Post by coffeecat on 2011-09-15
This is an old thread, and the OPs problem was solved long ago. No need for discussion and no need for going off-topic. I've marked the thread as solved and with that...

Thread closed.

---

