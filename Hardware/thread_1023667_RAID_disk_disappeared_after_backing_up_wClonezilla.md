---
title: "RAID disk disappeared after backing up w/Clonezilla and (un)plugging external drive"
date: 2008-12-28
forum: Hardware
---

### Post by kaleman on 2008-12-28
I have been running Ubuntu linux on my desktop computer for months without any problem. Until today. Today, when I turn on my computer, all GRUB gives me is

GRUB: error 17

What I have been doing yesterday is:

1) Boot from a clonezilla live CD, and make a backup image of the hard drive to an external drive. I did NOT tell clonezilla to write to my desktop PC, just to the external drive.

2) Plug and unplug the external drive a few times. Which buggered me a little bit, because my BIOS thought it had to boot from the  external drive when I plugged it in to early. But I don't see how that should worry GRUB.

I do not see how any of those two actions caused any problems. I have been making clonezilla backups on my other computer a few times without any problems. But still, on my desktop computer I do get the GRUB: error 17.

What I tried to do to solve the problem:

1) Download the "super grub disk" utility and run it. This gives me the following output:

error 15: file not found

This is the same output I get when I run find /boot/grub/stage1 from a live CD manually.

2) Run the Ubuntu Ibex live CD and see if it can find the hard disk. It cannot. The hard disk is just not there. On the internet I found people having trouble installing Ubuntu from a live CD on a RAID disk. However, my original install a few months ago was from a Kubuntu live CD. It ran without any problems. Unfortunately, I threw away the Kubuntu live CD after downloading the (newer) Ibex live CD. I would be surprised though if an older Ubuntu CDs had better disk finding capabilities than a newer one.

3) Look into my BIOS settings. It only lists my CD and DVD drives. Next to "Primary Master" and "Primary Slave" it says "none". "Automatically detecting" the hard disk does not change this. I'm not sure what my BIOS settings used to say there however, since I never really bothered about them ever before.

4) On startup run the RAID utility. It lists a 0 PM WDC WD.... 114473 MB disk. Which is exactly the disk I am missing. I don't know if it's still there because the utility actually finds the disk, or because it still "remembers" it was there. The RAID utility gives me options like "Create RAID set", "Delete RAID set", "Resolve conflicts" (which just says there aren't any) and "Low Level Format". I don't think these options solve my problem right now.

5) Rerun Clonezilla. Fortunately, Clonezilla actually finds the missing hard disk. Which gives me the possibility to restore the complete disk from the image. However, the problem seems to be that the hard disk could not be found, NOT that any data is missing. Restoring the data would take some hours, and would most probably NOT solve anything.

I'm stuck here. I do not have any idea on how to make my computer find the hard disk again. Any hint in the right direction would be highly appreciated. Thank you very much!

---

### Post by albinootje on 2008-12-28
> **kaleman said:**
>  Restoring the data would take some hours, and would most probably NOT solve anything.


Clonezilla will also take care of the MBR if you did a whole disk cloning.

[http://www.mepis.org/node/9283](http://www.mepis.org/node/9283)
> 
"I've seen this when the" :
I've seen this when the boot sector of the partition that holds menu.lst gets corrupted and poor grub just can't deal with it.


So, it could be that you only have one corrupted file.
And maybe some temporary flaky power connection to your hard disk ?

---

### Post by kaleman on 2008-12-28
Not sure if I did "whole disk" cloning or just the data on one partition. I actually just ran clonezilla to go through the whole procedure of cloning and restoring once, so I would know how it worked, might I ever REALLY need it. After that, I was going to reinstall the whole PC and give it to someone else. However, that will be hard without a hard disk to be found.

I still don't understand why the MBR should be the problem though. My live CD (that does not use the MBR) can not find the hard disk either. So more likely, the MBR is still fine, but just cannot be found. (Apart from that, I really do not see what would have caused the MBR to get corrupted).

Edit: and the super grub disk could not fix the MBR either.


If I get no other ideas, I might get into the trouble of restoring the whole disk, but I have my doubts if it will solve anything. Don't get me wrong, I DO really appreciate your feedback (I did not know about the MBR being restored for example), but I would like to try a simpler solution first).

So, if anybody has other ideas I might try first, I will be happy.

---

### Post by albinootje on 2008-12-28
> **kaleman said:**
> 
Edit: and the super grub disk could not fix the MBR either.


The link I gave was about a possible corrupted /boot/grub/menu.lst which is on your Linux partition, not in the MBR.

You write that Clonezilla finds your disk, and that the RAID controller in your BIOS finds your disk, but the Intrepid install cd doesn't.

Why don't you try with a copy of an older Kubuntu install cd you mentioned.
Even when it's very old, I assume you can still find it on the net.

You can also try gparted (from a terminal) in the Intrepid install cd, and see whether gparted gives errors and/or sees your disk.

---

### Post by caljohnsmith on 2008-12-28
In order to get a clearer picture of your setup, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by kaleman on 2008-12-28
Thanks. Seems I'm getting closer.

When I run GParted from the live CD, it shows me three partitions:

/dev/sda1    !  unknown
/dev/sda2       extended
   /dev/sda5    linux-swap

Where it says "unknown" it is supposed to say ext3. Seems my partition really got lost there somehow. Which worries me about what I did wrong. The whole idea of running clonezilla was to get a copy of my disk. Instead, somehow I managed to mess things up.

Running the boot_info_script gives me this RESULT:

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for its boot files.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  No Boot Loader
    Mounting failed:  
mount: you must specify the filesystem type

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x09760975

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   231416324   115708131   83  Linux
/dev/sda2       231416325   234436544     1510110    5  Extended
/dev/sda5       231416388   234436544     1510078+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda5: UUID="f7750213-8af4-4560-a9ef-ad6f96725c32" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=============================== StdErr Messages: ===============================

/dev/sda1: unknown volume type
```

What do you think? Is there a way to tell my computer that the partition is actually ext3? Or is trying to restore with clonezilla the only option left?

---

### Post by caljohnsmith on 2008-12-28
I'm not sure what happened, but as you say it looks like something must have gone wrong with clonezilla or something; your sda1 Ubuntu partition is now unrecognized. You could try:
```
sudo mount -t ext3 /dev/sda1 /mnt && ls -l /mnt
```
I really doubt that will work, but that would be the first thing I would try. If that gives you an error, you could try:
```
sudo fsck -yCM /dev/sda1
```
And see if fsck can do anything with the partition, and please post the output. If that doesn't work though, I think you will probably have to try and restore your clonezilla image, assuming it isn't corrupt either. Let me know how it goes.

---

### Post by albinootje on 2008-12-28
> **kaleman said:**
> 
/dev/sda1    !  unknown
/dev/sda2       extended
   /dev/sda5    linux-swap


How did you use CloneZilla ? On a usb-disk or over the network ?

The tricky thing unfortunately is that the Linux kernel started to use /dev/sd* for IDE hard disks, where before it would only use that for usb-disks and SCSI disks..

However.. CloneZilla normally needs to mount a partition where it can store it's images.
Afaik CloneZilla does by default not use any "raw" methods to make the backups.
-----------------

You can see what testdisk does.
Install it in the live session with :
```

sudo apt-get install testdisk

```
Documentation is here : [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
and : man testdisk
and : testdisk -h

---

### Post by kaleman on 2008-12-28
fsck saved me! It told me the disk hadn't been properly unmounted, it started repairing, and now I'm able to boot normally again.

I'm still not sure what exactly happened. After running Clonezilla (that must have mounted the disk to read it), probably I've done something wrong which caused the disk not to get unmounted. Still, I did not know that an improper unmount could cause THIS much trouble. Getting wiser every day...

I used the Mozilla live CD. In case you have any idea on what I did wrong, please tell me. The fsck output is attached below.

Meanwhile, thanks both for your help! It saved me some trouble, and it will help me definitely next time something like this happens!


```
<skipping lots of similar messages...>

Free inodes count wrong for group #881 (8192, counted=8122).
Fix? yes

Directories count wrong for group #881 (0, counted=1).
Fix? yes

Free inodes count wrong for group #882 (8192, counted=8186).
Fix? yes

Directories count wrong for group #882 (0, counted=5).
Fix? yes

Free inodes count wrong (7233525, counted=6925857).
Fix? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 307679/7233536 files (3.0% non-contiguous), 22269462/28927032
blocks
```

---

### Post by albinootje on 2008-12-28
> **kaleman said:**
> fsck saved me! It told me the disk hadn't been properly unmounted, it started repairing, and now I'm able to boot normally again.
--cut--
Directories count wrong for group #882 (0, counted=5).
Fix? yes
[/CODE]

Can you check your /lost+found directory to see whether some files ended up in there ?

And, if you like, you can also describe what happened on the CloneZilla mailinglist.

And, again, it's possible that you got grub error 17 because grub could not read a file properly on your Linux partition.
This might not have to do with CloneZilla, even ext3 partitions should be checked from time to time, according to the tune2fs manual page.

---

### Post by kaleman on 2008-12-29
I did some more testing with clonezilla. I had no further problems. Just bad luck with a damaged grub-file I guess. Case closed :)

---

### Post by albinootje on 2008-12-29
> **kaleman said:**
> I did some more testing with clonezilla. I had no further problems. Just bad luck with a damaged grub-file I guess. Case closed :)

OK :) Can you mark this thread as SOLVED ?

---

