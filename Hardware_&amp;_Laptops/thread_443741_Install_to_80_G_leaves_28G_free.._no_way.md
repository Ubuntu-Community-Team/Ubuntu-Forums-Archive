---
title: "Install to 80 G leaves 28G free.. no way"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by johnbl on 2007-05-14
After much bouncing around and little progress with 6.06 - semed to have a problem that restricted use - I did a full install of 7 fiesty.

It now appears that of 80 G I have around 28G free, two swap files and I'm not sure what the rest is.

Surely Ubuntu doesn't swallow 40G just to install itself?


Casn anyone throw a little light my way as I'm really stumped as to how I can get back use of some of the HDD or even if that's possible.

Thanks

John

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4717    37889271   83  Linux
/dev/sda2            9163        9729     4554427+   5  Extended
/dev/sda3   *        4718        9162    35704462+  83  Linux
/dev/sda5            9359        9729     2980026   82  Linux swap / Solaris
/dev/sda6            9163        9358     1574307   82  Linux swap / Solaris

---

### Post by taurus on 2007-05-14
What's the output of these commands from a terminal?

```
cat /etc/fstab
df -h
free
```

---

### Post by johnbl on 2007-05-15
> **taurus said:**
> What's the output of these commands from a terminal?

```
cat /etc/fstab
df -h
free
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=3df2c8e1-4e3e-49d0-af06-a7c8d3992257 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=01f25719-e07a-43c5-a042-7c68232bc4be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


john@interserve3:/$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda3              34G  2.1G   30G   7% /
varrun                498M  108K  498M   1% /var/run
varlock               498M     0  498M   0% /var/lock
procbususb            498M  156K  498M   1% /proc/bus/usb
udev                  498M  156K  498M   1% /dev
devshm                498M     0  498M   0% /dev/shm
lrm                   498M   33M  465M   7% /lib/modules/2.6.20-15-generic/volatile


john@interserve3:/$ free
             total       used       free     shared    buffers     cached
Mem:       1019400     500220     519180          0      53580     237492
-/+ buffers/cache:     209148     810252
Swap:      1574296          0    1574296

---

### Post by mikewhatever on 2007-05-15
Since you've only just installed, and you do not have Windows, I think you should reinstall once again, and only keep the partitions you need, deleting the others.
Also, where does it say around 28 Gb is free?

---

### Post by johnbl on 2007-05-16
Where.. Am on another machine and can't rightly remember to be honest. I CAN see there are multi partitions that donm't appear to be available however and agree that a reinstall, bugger all to loose afterall is the best.

Problem is I thought I WAS doing a clean install and that every thing on the the disk would go and the ' auto ' facility would take away the set up of partitions from my control. Clearly not it would appear!

Are you aware of how I can force a reinstall from a CD to set up so as to maximise space (a) and (b) what of having NTFS [ is that correct the WIN format ] partitions to be able to ' share ' windows data files as I seem to remember seeing mentioned in a post. I could  in Dapper, simply load copied from my WIN machine data files and copied them bach when completed, worked ok..

Any pointers most appreciated.

Thanks
John

---

### Post by mikewhatever on 2007-05-17
The partitions that do not appear in Ubuntu file manager are simply not mounted.
From the fact that you have two ext3 and two swap partitions, I'd guess that, somehow, you've done the installation twice. Not sure how that happened though.
The auto installation process should format the drive and create the partitions for Ubuntu (root, swap). I don't think you can control their sizes unless they are set up manually.
About the ntfs partition, I do not think you need one at all. You do not have Windows on that PC, so what do you want to share with?

---

### Post by johnbl on 2007-05-17
Thanks for that. Indeed I had attempted an install that failed with allsorts of errors and suggestions that same be reported as bugs. However as the system was faulted and zip would work... Bit of a logic flaw there!

I'd gritted the teeth - ok I swore - a bit, ok a lot. 

Then did the install bit again thinking that the disk would be wiped clean by the full ' fresh '  install accepting the default set up as offered. 
Apparently that's not the case.

So the question now on the cusp is how do I go about setting up the drive so as to be wholly available for a clean install?

As to the MS partition - In my other life I'm an accountant, the software I use is MS based though I am - make that was <g> - getting great results from '  wine '  for lotus spreadsheets and my accounting package. I like to spring the client files from the main office system to the notebook for onsite visits where updates of material is undertaken and then take the data files back to the main system on return to the office.
This for me is a tad mission critical as it were.

John

---

### Post by mikewhatever on 2007-05-17
You can simply try the auto installation once again, which, hopefully would do what you want, or go for the manual partitioning, delete all existing ones and create the new ones. Here are some guides  
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Let me clarify something about ntfs partition. Fist, if you think you need one, then manual partitions setup is the way. Second, imo, you only need an ntfs partition if planning to install Windows and dual boot. Ntfs is MS file system, so their OSs (XP, Vista) need it, but MS files, such as *.doc, do not. If you are going to use wine to work with those files, there is no need for ntfs.

---

### Post by johnbl on 2007-05-17
> **mikewhatever said:**
> You can simply try the auto installation once again, which, hopefully would do what you want, or go for the manual partitioning, delete all existing ones and create the new ones. Here are some guides  
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)


Thanks, that clarified the choices available in 7.04 install. I'd assumed first choice - default - reformatted the entire disk rather than found a bit to grab. The first install I'd taken choice two - do the lot - and when it failed I assumed it was me... Reading that it makes me look a tad flaky... Not usually that stupid!

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Let me clarify something about ntfs partition. Fist, if you think you need one, then manual partitions setup is the way. Second, imo, you only need an ntfs partition if planning to install Windows and dual boot. Ntfs is MS file system, so their OSs (XP, Vista) need it, but MS files, such as *.doc, do not. If you are going to use wine to work with those files, there is no need for ntfs.

Light turn on.. NO NTFS required, good one.

Thanks so much for the advice. I'll get back to the notebook on the weekend and have another shot with this  improved view. [ And in MS I can use FDISK ... never think it would you <VBG> ]

Cheers

John

---

