---
title: "GRUB Problems Immediatley After Upgrade"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by Fermanagh on 2009-07-29
I am running Ubuntu 8.04 LTS on an IBM T42 Notebook using the entire hard drive for ubuntu (NO DUAL BOOT)

Today I received a major update that included kernel components.

After the update completed I got the following messages during the initial reboot:

GRUB Loading stage 1.5.
GRUB loading, please wait...
Error 25

I then tried to repair the problem using previous posts:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.[COLOR="Red"](I used a version 8.04.2 Ubuntu CD burned on 6/16/09)[/COLOR]

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

[B][COLOR="Red"]When I typed the command: find /boot/grub/stage1
it returned the message : file not found[/B][/COLOR]

I was using the live CD Version 8.04.2 downloaded 6/19/09 as my tool to get to a terminal screen to enter the commands.

[COLOR="Red"]All previous upgrades (since 6/19/09) were installed, so I was rather surprised when this problem surfaced.[/COLOR]

I suspect that the MBR may be totally messed up and there may be no way to fix this problem.

Please advise as to what other tools may fix this problem.

Thanks....

---

### Post by merlinus on 2009-07-29
Post results of

```
sudo fdisk -l
```

---

### Post by Fermanagh on 2009-07-29
/dev/sda1  Linux
/dev/sda2  Extended
/dev/sda5  Linux Swap / Solaris

The /dev/sda1 has the boot marker.

Thanks for the command. I will now try to use this information to
retry the previous mentioned GRUB commands

---

### Post by Fermanagh on 2009-07-29
The command:

grub> find /dev/sda1/boot/grub/stage1

grub> find /dev/sda1/grub/stage1

Both commands return: Error 15: file not found

---

### Post by merlinus on 2009-07-29
Try this:
```

sudo grub
root (hd0,0)
setup (hd0)
quit
```

---

### Post by Fermanagh on 2009-07-29
grub> root (hd0,0)
Error 21: Selected disk does not exist

---

### Post by merlinus on 2009-07-29
If it is saying that (hd0,0) does not exist, then perhaps linux is not on sda1, which this translates to.

Why not run

```
sudo fdisk -l
```

and post the exact output.

---

### Post by Fermanagh on 2009-07-30
See attached image file for the command return:

---

### Post by Fermanagh on 2009-07-30
The screen shot in the previous post is to hard to read. The command returned the following three lines of information:

/dev/sda1  *   1      4659   37423386   83   Linux

/dev/sda2      4660   4864   1646662+    5   Extended

/dev/sda5      4660   4864   1646631    82   Linux swap / Solaris

---

### Post by merlinus on 2009-07-30
OK.  Linux is indeed on (hd0,0), but still does not find the /boot files.

Try mounting your linux partition whilst running from the live cd.  You can probably do this by selecting tt in Places/Computer.

Then use nautilus to navigate to the mountpoint (/media/disk, or something like that), and look in filesystem: /boot/grub to see if the grub files are there.

They should be something like

stage1
stage2

---

### Post by Fermanagh on 2009-07-30
Try mounting your linux partition whilst running from the live cd. You can probably do this by selecting tt in Places/Computer.

Sorry, but I am bit confused. If I navigate to Places -> Computer -> File System , I see a boot folder. If I click into the folder I
see 5 text files (abi-2.6.24-23-generic, config-2.6.24-23-generic, memtest86+bin, System.map-2.6.24-23-generic, vmlinuz-2.6.24-23-generic)

Also, what is tt ?

I am now wondering if the Live CD session can only see itself in RAM memory. I am trying to access partitions on my hard drive. Using the Live CD, I am unable to see any of my folders or files on the hard drive. This might explain whey the above grub commands could not find my files. 

Do I need a special Live CD to do this repair work ?

---

### Post by lindsay7 on 2009-07-30
You need to look for the boot folder on the drive where Ubuntu is installed.

---

### Post by merlinus on 2009-07-30
Yes, you are viewing the live cd filesystem, not the one on your hdd.  Do you not see something called Disk (or something similar) under Places/Computer?  You can mount that by clicking on it.

Alternatively, you will have to do this from a terminal:

```
sudo mkdir /media/disk
sudo mount -t ext3 /dev/sda1 /media/disk
```assuming that linux is on the first partition on your hdd.  If not, then change sda1 to whatever one it is.

Then you can use nautilus to navigate to the mountpoint and look in /boot/grub.

---

### Post by Fermanagh on 2009-07-30
$ sudo mkdir /media/disk  (worked!)


$ sudo mount -t ext3 /dev/sda1 /media/disk

returned: 

mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error
In some cases useful info is found in syslog - try dmesg | tail or so

$ dmesg | tail  returned:

[42861,464198] SQUASHFS error Unable to read page, block 2760367a, sise 6d24
[42861,464324] SQUASHFS error: sb_bread failed reading block 8x9d828
[42861,464327] SQUASHFS error: Unable to read fragment cache block [2760367a]
[42861,464330] SQUASHFS error: Uable to read page, block 2760367a]
[42861,464458] SQUASHFS error: Unable to read fragment cache block [2760367a]
[42861, 464588] SQUASHFS error: sb_bread failed reading block 0x9d828
[42861,464590] SQUASHFS error: Unable to read fragment cache block [2760367a]
[42861,464593] SQUASHFS error: Unable to read page, block 2760367a, size 6d24

I checked and sda1 is where Linux resides. sda2 is is for Extended, and sda5 is for Linux Swap/Solaris

Ubuntu was installed on the only entire hard drive. There is no dual-boot setup. 
[42861,464461] SQUASHFS error:

---

### Post by Fermanagh on 2009-07-30
When I look at Places Computer, I see the icon for 38.3 GB Media along with the CD-RW/DVD+-RW Drive, and Filesystem.

Filesystem the Live Cd's volume. 

If I try to mount the 38.3 GB Media by clicking on the Icon, it returns the same error messages described in the previous post.

Wrong fs type... etc.

---

### Post by merlinus on 2009-07-30
What filesystem is linux using?  Also, you might try running fsck on it, since there appear to be errors.

---

### Post by Fermanagh on 2009-07-30
Ubuntu documentation says ext3

There is mention of an ext4 for release 9.04 Beta. When I did the automatic upgrade I was running version 8.04 LTS with all of the previous upgrades installed.

Maybe the upgrade included 9.04 Beta code?

---

### Post by Fermanagh on 2009-07-30
sudo fsck -C /dev/sda1  returns:

fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Attempt to read block from filesyatem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition

---

### Post by merlinus on 2009-07-30
If fsck is unable to read some blocks on sda1, then it would appear something is definitely amiss.  You might try running fsck with other switches that would attempt to fix the problems, but frankly I am not experienced with this.

---

### Post by Fermanagh on 2009-07-30
I will play with it for a few more days. I may in the end have to bite the bullet and reinstall Ubuntu to recover.   

Thanks for all your help....

---

### Post by presence1960 on 2009-07-30
to get a clearer picture of your setup and boot process boot from Ubuntu Live CD and download to the desktop the Boot Info Script 0.32 from here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Once on the desktop open a termainal and run this command 
```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. Copy & paste the entire contents of that file back here. Once pasted here highlight all text and click the # sign on the toolbar. This will shed more light on your setup than a few commands you have run already.

There have been many problems documented in these forums with the upgrade process. This is not to say that all upgrades fail, it is just that there seems to be a disproportionate number of threads detailing problems with dist upgrades. I stay away from them and prefer clean installs. hopefully between all of us we can get it working, if not you may have to do a clean install anyway. I realize you were not doing a dist upgrade initially but you mentioned ext 4 later on  so maybe that is what you did. Either way run the boot info script to see if we can save this or do a clean install...your choice!

---

### Post by Fermanagh on 2009-07-31
============================= Boot Info Summary: ==============================

 => ```
Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bdf42

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    74,846,834    74,846,772  83 Linux
/dev/sda2          74,846,835    78,140,159     3,293,325   5 Extended
/dev/sda5          74,846,898    78,140,159     3,293,262  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="e53944ca-e9bd-457d-a098-b8d1ebdb83d3" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1




```

---

### Post by Fermanagh on 2009-07-31
[HTML]The previous post is the results of the scan. 

When the Live CD was loading onto my IBM T42 notebook I noticed that there were several messages about "Buffer I/O error on device sda1, Logical block..." but eventually it loaded and I was able to run the test. 

I tried another Ubuntu Live CD (later version) and got the same messages when the 8.04LTS Live CD was loading into RAM. 

There may be a problem on the hard drive(sda1). Not sure... 

My previous mention of ext4 was the result of a google search to find out what file system type is used by Linux. 

To the best of my knowledge, I did not do an update that involved code using the ext4 extent. I simply did a routine update and after the update completed when the system started into the booting process with the updated code, I experienced the Error 25 message mentioned in my initial post.

I would really appreciate some feedback on the results of the test shown in the previous post.  [/HTML]

---

### Post by merlinus on 2009-07-31
I think this says it all:

> 
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''


---

### Post by lindsay7 on 2009-07-31
As a last resort, you might download and run "Testdisk" just to see if it sees anything. You may need to try a few different things with it.  It should not hurt your situation and may find something that is out of line.  Your script info does not show any boot instructions and you had indicated that you could not find stage1 or starge 2 so there is no way to start the OS. At this point it does not mater since the file system unusable. If Testdisk does find problems and you fix those, you would still new to address the grub problem.

It may be easier to do a clean install.

---

### Post by Fermanagh on 2009-07-31
Sounds like my only option is a clean install on a new hard drive.

Thanks again for your interest and help.:)

---

### Post by lindsay7 on 2009-07-31
I have had good luck ordering from Newegg, good prices and quick delivery.  Just make sure that you order the correct drive for you system (IDE or SATA).  If your motherboard  can accommodate both opt for the SATA drive. If you need help installing the new drive or have questions, I will be glad to help.

---

### Post by presence1960 on 2009-08-01
Sorry about the delay, I concur with the others about your situation.

---

