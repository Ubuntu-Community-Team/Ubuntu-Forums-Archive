---
title: "Partition/Disk problems - Help please!"
date: 2016-11-30
forum: Hardware
---

### Post by ian49 on 2016-11-30
I'm running Ubuntu 14.04 off an SSD. I also have a 2TB drive which has 2 partitions. One is used for general purposes and the other is used by a Windows 7 virtual machine. This arrangement has worked fine for a number of years. Today, after upgrading Samba I seem to have lost the data in both partitions. The Samba upgrade may or may not be a red herring. Anyway if I try to access either of these partitions from my Ubuntu Places menu this is what I get:

```
partition 1
windows_data
536 GB NTFS
```

Sorry, could not display all the contents of "windows_data": ```
Error when getting information for file '/media/windows_data/D Drive': Input/output error
```
```
partition 2
ubuntu_data
1.5TB Ext4
```
Sorry, could not display all the contents of "ubuntu_data": ```
Error when getting information for file '/media/ian/ubuntu_data/.Trash-1000': Input/output error

``` Looking at the drive using the Disks utility shows "Disk is OK. One bad sector". And it shows the partitions as being 64% full (windows_data) and 9.4% full (ubuntu_data).

If I boot onto Ubuntu using a flash drive and try and access these same partitions this is what I get:

```
Error mounting /dev/sdg1 at /media/ubuntu-mate/windows_data:
Command-line `mount -t "ntfs" -o
"uhelper=udisks2,nodev,nosuid,uid=999,gid=999" "/dev/sdg1"
"/media/ubuntu-mate/windows_data"' exited with non-zero exit status
13: Error reading $MFT: Input/output error
Failed to load $MFT: Input/output error
Failed to sync device /dev/sdg1: Input/output error
Failed to mount '/dev/sdg1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```
and

```
Error mounting /dev/sdg2 at /media/ubuntu-mate/ubuntu_data:
Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid"
"/dev/sdg2" "/media/ubuntu-mate/ubuntu_data"' exited with non-zero
exit status 32: mount: wrong fs type, bad option, bad superblock on
/dev/sdg2,
```
I should also add Gparted gives the following error:

```
Error fsyncing/closing /dev/sdb: Input/output error
```
So I'm not really sure what has happened or whether there's anything at all I can do to retrieve the data. Any advice would be very welcome.

---

### Post by yancek on 2016-11-30
The error for the windows partition means that you were booted into windows and left it hibernated before booting into Ubuntu.
Try running fsck on the Ubuntu data partition.

---

### Post by ian49 on 2016-11-30
> **yancek said:**
> The error for the windows partition means that you were booted into windows and left it hibernated before booting into Ubuntu.
Try running fsck on the Ubuntu data partition.

Hi, thanks for responding.

I'm puzzled by the windows partition error because I only boot into Ubuntu. I didn't even have the Windows 7 virtual machine running at the time the problem presented itself.

I tried running fsck on the Ubuntu data partition as suggested and got the following error:

sudo fsck /dev/sdb2
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb2
Could this be a zero-length partition?

In addition, the Disks application shows Partitioning for the whole drive as "Unknown".

---

### Post by ian49 on 2016-11-30
I have a 2GB internal HD and am running Ubuntu 14.04 on an SSD.  The 2GB drive was divided into 2 partitions, one as NTFS and the other as ext4.

I'm currently unable to access either partition. Running gparted generates the following error messages:

Error fsyncing/closing /dev/sdb: Input/output error
Input/output error during read on /dev/sdb

After ignoring and cancelling through the various errors it shows the drive as 1.83Tb unallocated.

The gnome disk utility, Disks, however, shows the drive as having the following:

partition 1
windows_data
536 GB NTFS
64% full

partition 2
ubuntu_data
1.5TB Ext4
9.4% full

What I'm trying to determine is whether to write off the disk and bin it or is there any likelihood I can rescue it.  Any help very much appreciated.

---

### Post by DuckHook on 2016-11-30
What does Disks app say about SMART data? Is the drive self-reporting errors and pending disk failure? You can also use:```
sudo smartctl -a /dev/sdb
```&#8230;and post all output back to this thread (make sure to use [noparse]```
 and 
```[/noparse] tags).

---

### Post by ian49 on 2016-11-30
I ran the command line you suggested and got the following output:

```
sudo smartctl -a /dev/sdb
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-96-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Vendor:               /1:0:0:0
Product:              
User Capacity:        600,332,565,813,390,450 bytes [600 PB]
Logical block size:   774843950 bytes
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
```

---

### Post by DuckHook on 2016-12-01
I was about to post second thoughts to my suggestion when I got your reply.

Your HDD is 2 GB, which means it is so old as to likely not even have SMART circuitry. Therefore, no amount of tinkering with options will work; it can't report what it doesn't know.

To cut to the chase: it is likely your HDD is toast. Admittedly, this is nothing more than a wild-eyed guess. But I work with a lot of old HW and have a bit of a nose for such things. A 2 GB HDD is positively ancient (I'm surprised you were able to install it!), so it is well past its intended lifetime and the chances are big that it just gave up the ghost.

If you have important data on the thing that you haven't backed up, then you can try a number of rescue techniques and apps: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by ian49 on 2016-12-01
Sorry, that was my mistake, it's late here (5am) and my brains are fried, I should have said  2TB.

I ran the smartctl command again with the permissive option and got the following:

```
sudo smartctl -a -T permissive /dev/sdb
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-96-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Vendor:               /1:0:0:0
Product:              
User Capacity:        600,332,565,813,390,450 bytes [600 PB]
Logical block size:   774843950 bytes
Physical block size:  1549687900 bytes
Lowest aligned LBA:   0
>> Terminate command early due to bad response to IEC mode page

=== START OF READ SMART DATA SECTION ===

Error Counter logging not supported

Device does not support Self Test logging
```

---

### Post by DuckHook on 2016-12-01
2TB is a relative baby, but they can fail too. It would definitely have SMART circuitry, so the error message is concerning… possible drive failure.

[LIST=1]
[*]
[*]Can you see any partition from Windows? I'm assuming you dual boot because you have an NTFS partition.
[*]Do you have some sort of RAID controller between HDD and MB?
[/LIST]
Stop writing anything to HDD. If you must rescue data, use the measures in link of my previous post starting with [gddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html") and then proceeding to the other steps.

Last but not least, trying to rescue data while your brain is fried is not a good combination. Put the drive away for when you are fresh and capable. The problem will still be there when you return. I'm reaching end of my tether for today as well. Cannot help you until tomorrow, though others are more than welcome to jump in.

---

### Post by ian49 on 2016-12-01
Just briefly as I must get some sleep....

I don't dual boot but I have Windows 7 running inside a vmware virtual machine.

I don't have any kind of RAID controller, just a SATA cable to the drive from the MB.

Will have a look at the gddrescue stuff tomorrow.

Thanks for your input.

---

### Post by DuckHook on 2016-12-01
ian49

Do not duplicate post. I did not catch this until I started responding, but your duplicate post is missing info from the original, misleads all helpers (as it did me), creates redundant replies and confuses the community (again, as it did me).

Threads have been merged. The next time, it will be closed or jailed.

Also, please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

