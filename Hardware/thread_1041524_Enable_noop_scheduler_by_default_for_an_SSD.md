---
title: "Enable noop scheduler by default for an SSD"
date: 2009-01-16
forum: Hardware
---

### Post by chmac on 2009-01-16
I was reading [this]("http://www.nabble.com/Set-up-for-an-x301--td21289307.html") which suggests using the noop scheduler for SSDs. I've just got an X301 with a 128Gb SSD so I'd like to try this.

I found two ways to enable the noop scheduler.

[Firstly]("http://ubuntuforums.org/showthread.php?t=119546#post1305177"), adding elevator=noop to grub. I believe "elevator=noop" can be prepended to both the existing entries in /boot/grub/menu.lst and the "defoptions = " line to add it automatically to new kernels.

[Secondly]("http://www.thinkwiki.org/wiki/Ericsson_F3507g_Mobile_Broadband_Module#Scripting_everything"), by installing sysfsutils and adding "block/sda/queue/scheduler = noop" to /etc/sysfs.conf.

Can anyone recommend which option would be better? Do they achieve the same thing?

I guess if it caused problems I could more easily revert it in the grub options. I'll try that first and see how I get on. Any advice would be appreciated.

---

### Post by chmac on 2009-02-11
Bump. Any suggestions?

---

### Post by Yashiro on 2009-02-11
You should be able to change which scheduler by echoing to 
/sys/block/sda/queue/scheduler. [http://www.linuxhowtos.org/System/iosched.htm](http://www.linuxhowtos.org/System/iosched.htm)

I'd just use the grub option myself. If it's a clean install using JFS as disk format might also help. Or just ext2 unless you really need the journalling.

---

### Post by chmac on 2009-02-12
Awesome, thanks for the link Yashiro, I just changed my scheduler! :)

I think I'll use the grub approach, seems the easiest.

---

### Post by Blazeix on 2009-03-05
As this thread is one of the top results for "ssd scheduler" I figured I'd add a bit of info to this thread. There is a small difference between the method where you modify menu.lst and the method where you modify sysfs.conf. The menu.lst method sets it for all drives, and the sysfs method changes it only for the drives you specify. For example the line

```
block/sda/queue/scheduler = noop
```

only changes the scheduler for the drive "sda". The two methods do the same thing only if you have one drive. If you have a mix of actual hard drives and SSDs, you'll want to use the sysfs method to enable it only on the SSDs. If you only have SSDs, it's easiest to use the menu.lst method.

---

### Post by chmac on 2009-03-14
Thanks Blazeix, I've just updated to the sysfs.conf method. I occassionally plug in USB spinning disks, so I think it makes sense to set the noop schedulere just for sda.

---

### Post by Captain_Bodge on 2009-03-14
Does it make any difference? Have you compared performance with noop to performance with cfq? I've read some conflicting results.

---

### Post by chmac on 2009-03-14
To be honest, I haven't noticed any performance difference, but I haven't run any tests. I think there's a chance it puts slightly less wear on the drive, so I'm happy to switch for that reason. My laptop is usually under fairly low load so I don't really notice disk performance.

---

### Post by magicfab on 2010-11-09
I've summarized current information about SSD configuration in Ubuntu 10.10, including the information in this thread, here:

[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

Thanks for any comments/suggestions.

---

### Post by csarlee on 2010-12-25
@MagicFab

Thanks for the link, it is awfully complete and good guide!!!

---

### Post by Skip Da Shu on 2011-01-25
This might make you rethink using "noop"... the other good ssd option is "deadline".

[noop vs deadline]("http://ubuntuforums.org/showthread.php?t=1464706")


My Mushkin 40GB SSD in my Lenovo netbook with "EXT4, noatime, discard and /tmp mounted to tmpfs" gives me:

Using "deadline" -
 buffered 548MB in 3.01 = 182.71 MB/sec
 cached 1518MB in 2.00 = 759.52 MB/sec

Using "noop" -
 buffered 552MB in 3.01 = 183.14 MB/sec
 cached 1492MB in 2.00 = 746.73  MB/sec

Not much of a difference either way. A <1MB buffered adv to noop and 13MB cached adv to deadline.  What does a netbook do more of "buffered" or "cached" reading?  Not sure I really know the diff.  So for now I'm leaving it on deadline which is what it's been since the install of the SSD.


I'll be replacing my SATA-I 74GB 10K WD boot drive next week with an OCZ Vertex 2 64MB so I'll have to run these on that and see the diff.

---

### Post by dlzerocool on 2011-09-15
*A little test and review of the OCZ AGILITY 3 120GO.*

I've run several tests on the SSD and excuted them at least five times, the ones that I put here are the ones
that represent the most the average speed of the SSD.

On some tests I added the max speed reach just as an indication,
I didn't do it for the min values because I was writing stuff, having firefox open and so on.
And as soon as my text editor tool auto saved my work the tests speed easily fell down by 50-100MB/s

The drive is connected to an EliteBook 8560w using SATA III.

## Simple read test
$ hdparm -t /dev/sda
/dev/sda:
Timing buffered disk reads: 1554 MB in 3.00 seconds = 517.47 MB/sec
---------------------------------------------------------------------

## Simple read test on disk and buffer test.
$ hdparm -Tt /dev/sda
/dev/sda:
Timing cached reads: 16070 MB in 2.00 seconds = 8046.52 MB/sec (Buffer speed)
Timing buffered disk reads: 1560 MB in 3.00 seconds = 519.52 MB/sec
---------------------------------------------------------------------

## Here I wrote a 8.6GB file to the SSD.
$ dd if=/dev/zero of=tempfile bs=2M count=4096
4096+0 records in
4096+0 records out
8589934592 bytes (8.6 GB) copied, 13.3059 s, 646 MB/s (Max was 720MB/s)
---------------------------------------------------------------------

## Here I read the file created just above.
$ dd if=tempfile of=/dev/null bs=2M count=4096
4096+0 records in
4096+0 records out
8589934592 bytes (8.6 GB) copied, 12.7617 s, 673 MB/s (Max was 698MB/s)
---------------------------------------------------------------------

## Here I clear the buffer-cache to accurately measure read speeds directly from the device
$ echo 3 > /proc/sys/vm/drop_caches
$ dd if=tempfile of=/dev/null bs=2M count=4096
4096+0 records in
4096+0 records out
8589934592 bytes (8.6 GB) copied, 17.5188 s, 490 MB/s (Max was 499MB/s clearing the cache each time)
---------------------------------------------------------------------

So OCZ seems to keep their promises, at least at more than 90%.

Here is the my fstab params I used to my ext 4 partitions (ext4 defaults,noatime,discard) (discard means TRIM feature)
*(Warning: It is critically important that users switch the controller driving the SSD to AHCI mode (not IDE mode) to ensure that the kernel is able to use the TRIM command.)*
*(Warning: Users need to be certain that kernel version 2.6.33 or above is being used AND that their SSD supports TRIM before attempting to mount a partition with the discard flag. Data loss can occur otherwise!)*
/ (ext4)
/home (ext4)
/boot (ext2)

And I also compile and use tmp directly in RAM because I've 8G available.
none /tmp tmpfs nodev,nosuid,noatime,size=3G,mode=1777 0 0
shm /dev/shm tmpfs nodev,nosuid,size=6G 0 0

And voilà !
You can find a lot of information in Archlinux wiki, just write in Google "Archlinux SSD".

I'm using noop scheduler

---

### Post by listerdl on 2011-10-22
Would enabling noop stop my constant error in the log viewer wiht my SSD:

[CODE][limiting SATA link speed to 1.5 Gbps
ata4: hard resetting link
/CODE]

My machine being a toughbook does not allow SATA 2 b/c the system doesn't have a fan and the increased heat would cause problems....sorry to be Off Topic but - is there a way to stop or rather "fix" the SATA speed, i.e. tell ubuntu and the kernel to not bother trying to get faster speeds because it simply wont win this one?

Maybe this noop would help? thanks!

---

### Post by chmac on 2011-10-23
As far as I'm aware, the noop scheduler won't make any difference to the speed of the SATA link. I believe the scheduler controls when data is written from cache to disk, I'm pretty sure it doesn't affect the speed with which that data is written.

---

### Post by dlzerocool on 2011-11-06
"Consider switching from the default scheduler, which under Arch is cfq (completely fair queuing), to the noop or deadline scheduler for an SSD. Using the noop scheduler, for example, simply processes requests in the order they are received, without giving any consideration to where the data physically resides on the disk. This option is thought to be advantageous for SSDs since seek times are identical for all sectors on the SSD."
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by listerdl on 2011-11-08
> **dlzerocool said:**
> "Consider switching from the default scheduler, which under Arch is cfq (completely fair queuing), to the noop or deadline scheduler for an SSD. Using the noop scheduler, for example, simply processes requests in the order they are received, without giving any consideration to where the data physically resides on the disk. This option is thought to be advantageous for SSDs since seek times are identical for all sectors on the SSD."
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

thanks. @dlzerocool just to be sure, does the above relate to my problem thanks!!!

---

