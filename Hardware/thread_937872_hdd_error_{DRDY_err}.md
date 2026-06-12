---
title: "hdd error {DRDY err}"
date: 2008-10-04
forum: Hardware
---

### Post by Asrael on 2008-10-04
My system has two identical Maxtor 200GB SATA drives.

Ubuntu is installed on the Primary, which runs perfectly.
However when the second hard drive is connected Ubuntu won't boot. I get an error screen which reads:

[272.854943] ata2.00: status: {DRDY err}
[xxx.xxxxxx] ata2.00: error: {UNC}
[xxx.xxxxxx]ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[xxx.xxxxxx] ata2.00: BMDMA stat 0x24
[xxx.xxxxxx] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in

the x's are all different numbers. The message repeats several times. Sometimes it says Buffer I/O error on device sdb1, logical block x         (where x is a changing number)

In the forum a similar question has been asked before by others, but not answered.

I have tried switching the cables, the result was the same as before. 

Since I can't get Ubuntu to boot with the second drive connected I can't use any tools to analyse or fix the disk as far as I know.

My guess is the disk is broken, am I correct?
If not how might I fix this?

Thanks in advance,

Asrael

---

### Post by docmarine on 2008-10-06
I am getting the same error my self when trying to install Xubuntu.

Previously I had Ubuntu running on this machine with no problems whatsoever. I have 2x 120 gb disks SATA running off a "pesudo-RAID" card configured with each disk in "striping mode"

Any help is appreciated....

---

### Post by mushroomcloudwarrior on 2008-10-12
I'm having the exact same problem. I'm on a dual booting Dell inspiron 1500, and Windows won't start either (which leads me to believe that it's a hardware problem). Googling 'DRDY' error gives a lot of links that says it's something to do with hardy. Are you running Hardy as well?

Here's a link that might help: [http://ge.ubuntuforums.com/showthread.php?t=812562](http://ge.ubuntuforums.com/showthread.php?t=812562)

I don't know how my laptop could be damaged, I'd left it in my room, and the power got drained off, and it wouldn't start normally anymore.

Please do let me know if you've had a similar problem.

---

### Post by ciyo65 on 2008-12-12
> **mushroomcloudwarrior said:**
> I'm having the exact same problem. I'm on a dual booting Dell inspiron 1500, and Windows won't start either (which leads me to believe that it's a hardware problem). Googling 'DRDY' error gives a lot of links that says it's something to do with hardy. Are you running Hardy as well?

Here's a link that might help: [http://ge.ubuntuforums.com/showthread.php?t=812562](http://ge.ubuntuforums.com/showthread.php?t=812562)

I don't know how my laptop could be damaged, I'd left it in my room, and the power got drained off, and it wouldn't start normally anymore.

Please do let me know if you've had a similar problem.

I have a similar error. The link you referred is  not working.

---

### Post by mushroomcloudwarrior on 2008-12-12
> **ciyo65 said:**
> I have a similar error. The link you referred is  not working.

I'm afraid I can't help you here, 

In my case, I managed to boot using Ubuntu (it took about 20 minutes to boot up) and then copy the files I needed. I then called Dell support and found out that the computer had crashed 2 days out of warranty, I don't know if it's standard procedure, but I managed to get a new HDD delivered the next day.

I'm convinced it's a hardware problem, although not aware if it can be fixed. I wish you luck!

---

### Post by chris-man on 2009-01-28
I had a similar problem so I'm not sure if this will help you.

I downloaded and burnt the live cd, SystemRescueCD although any live cd with the right tools should work.

Then run: 
e2fsck -f -c -v /dev/sda1

substituting /dev/sda1 with your device with the error.

This will force a check of the drive even if fsck believes the drive is ok.

For this and more tips see [http://linux.chrissweeney.co.uk/](http://linux.chrissweeney.co.uk/)

---

### Post by bobberJR65 on 2009-02-18
I too had a similar error. The last thing I had changed was with Firefox-Mozilla, and I suspected that was the cause. My trusty Ubuntu network guru insisted I need a new hard drive. This old laptop is 5 years old!

Until I have the chance for further investigation I have completely removed Firefox from the system.

Hmmmm. So far everything is working...
Maybe it wasn't the hard-drive after all.

---

### Post by bobberJR65 on 2009-03-07
I had some free time this morning, so I took another look at my hard-drive. Sure enough there were some bad-blocks.

Like Chris-man said in the previous post,  it's so much easier to fix than replace.

Boot from Live CD. Do not mount hard-drive!

ubuntu@ubuntu:/etc$ sudo e2fsck -c /dev/sda5
e2fsck 1.41.3 (12-Oct-2008 )
Checking for bad blocks (read-only test): done                               
/dev/sda5: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes

-----
-----

/dev/sda5: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda5: 234203/843648 files (2.6% non-contiguous), 1278754/1684809 blocks

I had to run it twice and deleted rather than fix a few files that I kept note of.  I think this is so much better than replacing the hard-drive right now!

---

### Post by BrianB2 on 2009-03-24
I have been suffering from a similar problem over the last year or so. I have a Maxtor 6V160E0 (150GB) drive in a (soft) raid1 array with a Maxtor 6Y160M0 (160GB) drive (leaving 10GB unallocated). Every month or so, the system would go progressively slower until the 6V160E0 dropped out of the array. I didn't worry too much, because the error was associated with a read operation, the active mirror was clean and I could add the bad drive back into the array fairly easily.

After upgrading to the 2.6.24-23 kernel, the system became less stable and the drive wouldn't stay active for more than a week, so I had to diagnose the problem properly.

I found [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/228540](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/228540), and added pci=nomsi to my boot kernel options, but (as expected) it made no difference because I was running a kernel that should have been fixed.

I then downloaded and ran the seagate/maxtor SeaTools linux diagnostics. Many of the options will not work with Maxtor disks, but "sudo ./st -G /dev/sg1" failed consistently in the last 10% of the drive. Of course, the drive is out of warranty...

I found a very useful tutorial:
[http://howtoforge.org/how-to-resize-lvm-software-raid1-partitions-shrink-and-grow-p4](http://howtoforge.org/how-to-resize-lvm-software-raid1-partitions-shrink-and-grow-p4), although some of the commands were out of date. I found another tutorial:
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724), which helped with the syntax of some of the commands. Given the danger involved, I was particularly worried about the inconsistent unit sizes and defaults of each kind of command.

I disconnected the faulty drive and worked on the good drive, which was already larger. I needed to remap the good drive so that when it was mirrored onto the bad drive, the faulty sectors would never be used.

First, I shrank the ext3 filesystem to 90% of its original size, thus leaving the bad sectors unallocated. (Note: I used gparted initially, but after shrinking the filesystem, it immediately re-grew it to fill the logical volume!). Next, I shrank the logical volume to slightly larger than the file system size (to be certain that I didn't truncate anything important). Then, I shrank the physical volume (to slightly larger again), and finally reduced the raid volume size.

My nerves gave out and so I did not delete and reallocate a smaller partition. My disk now had a raid volume that only filled the lower 90% of the physical partition, which seemed to be good enough to me.

I rebooted from the good drive, which worked fine. Then I added the faulty drive back into the raid array. After 5 days, the system is still running at full speed and there have been no more DRDY errors logged.

I conclude that my disk drive is faulty, but in a way that is difficult to predict. When reading one of the faulty sectors, a retryable error is reported. The disk seems to have tried to move the data to an alternate track because too many read errors occurred on the original sector, but a write error occured during the copy operation. The original data was still OK, but it would need many successive reads to obtain the data. Obviously, the impact to the system depended entirely on what kind of file had been written to the faulty sector.

---

### Post by dcajacob on 2009-03-26
I had the same problem.  It started to show the DRDY ERR messages during boot after my laptop took a 3 1/2 ft dive.  Things got progressively worse over a few days and yesterday I bought a new HDD to replace it.  I think that's your best bet if you're seeing this error.

---

### Post by thenewcrowd on 2009-03-30
Well, getting past the hdd check if there is enough left of your hdd you can hit enter to bring up the (initramfs) prompt, type exit to exit the check then it will attempt to boot, exit the check as many times as it takes till it attempts to boot... once getting past that people say if your a ubuntu pro you can use fsck but to be careful because because you can do ALOT of damage with it.

---

### Post by ricardisimo on 2011-01-01
Happy new year, everyone! I'm having the same error messages popping up during looooonnnngggggg boot-up sequences:
> status: {DRDY}
Error: {UNC}
irq_stat 0x40000008
I/O error...
exception Emask 0x0 Sact 0x3
Those aren't exact quotes, mind you, just what I could jot down by hand. My secondary drive has completely disappeared. It is a 1.5 TB internal SATA, two-thirds full of material, mostly work stuff. I'd really like to get it back.

I'm hoping that two years have come up with another solution other than the live CD disk check. Any way for me to check it with my regular session running? Thanks.

Uggh... Now I've gone and done it. Based on the suggestion in [this thread]("http://ubuntuforums.org/showthread.php?t=1034762"), I created a file in /etc/modprobe.d/ called "options.conf" with the line:
> options libata noacpi=1
Now neither drive works, and I can't get past the initramfs screen. By command line, I ran "ls /etc/modprobe.d" and discovered that the file I created no longer exists, so I can't even delete it to undo the damage. My hope is that the contents of that file were not absorbed into some other conf file.

Any ideas as to how and where to even begin approaching this problem? Mostly I just want to see if I can grab my work files, which are important and a lot of work to replace. The music and vids are neither here nor there.

Edit: I tried booting from an older kernel, and here I am. However, my secondary drive is still missing. At least lshw can still detect it:
```
*-disk:1
                description: EXT4 volume
                product: SAMSUNG HD203WI
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: 1.0
                serial: 9f997b4e-5234-4da0-a0ed-6c655babcc5f
                size: 1863GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: ansiversion=5 created=2010-07-06 13:05:31 filesystem=ext4 label=Storage lastmountpoint=/media/Storage&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;V&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;kY&#65533;P'&#65533;Dq!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;@'&#65533;P&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;V modified=2010-12-31 19:06:50 mounted=2010-12-31 16:10:41 state=unknown
```

I've deleted the options.conf file. It was certainly there... don't know why ls couldn't find it.

There is indeed some connection to the kernel from which I attempt to boot. Neither version 2.6.35-22.35 nor 2.6.35-24.42 will boot properly, both stalling on the initramfs screen. However, the version I have right smack in the middle of them - 2.6.35-23.41 - boots just fine.

Boot or no boot, the extra drive is still missing. Any ideas? Thanks.

> **chris-man said:**
> I had a similar problem so I'm not sure if this will help you.

I downloaded and burnt the live cd, SystemRescueCD although any live cd with the right tools should work.

Then run: 
e2fsck -f -c -v /dev/sda1

substituting /dev/sda1 with your device with the error.

This will force a check of the drive even if fsck believes the drive is ok.

For this and more tips see [http://linux.chrissweeney.co.uk/](http://linux.chrissweeney.co.uk/)

I tried this off the LiveCD, and got nowhere:
```
ubuntu@ubuntu:~$ sudo e2fsck -f -c -v /dev/sdb
e2fsck 1.41.12 (17-May-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Could this be a zero-length partition?
```
I'm trying gparted, hoping to reformat the entire drive (I don't even care about the music and vids on the disc any longer). But it just keeps scanning and scanning, without making any progress, at least not so far.

Any other tips or tricks I might try?

Edit: Hmmm... gparted says "Searching /dev/sdb partitions". Well, at least it's trying. Should I maybe stop it and run it as root instead (or alternately run off my system instead of the LiveCD)?

Sorry for the multiple posts, but gparted finally got me some information (some quotes below, full screenshot attached):
```
e2label: No such file or directory while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

dumpe2fs: No such file or
directory while trying to open /
dev/sdb1

Unable to read the contents of the file system!
Because of this, some operations may be unavailable.

The following list of software packages is required for ext4
file system support: e2fsprogs v1.41+.
```
So maybe, possibly I'm kind of sort of getting somewhere now...? I'm still at a loss to understand why my extra drive is ext4 instead of ext3, which I thought was always the default file system for such things. If ext4 is in any way related to the problem, why would it stop working one day? Some recent update?

Should I try deleting the existing partition and reformatting the entire drive? If so, what file system should I choose for such an extra storage drive? Is this a waste of time if I can't determine if there is something physically wrong with my hard drive?

Thanks in advance for any help you can give.

---

