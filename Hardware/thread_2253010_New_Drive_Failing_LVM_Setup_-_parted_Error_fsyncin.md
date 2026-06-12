---
title: "New Drive Failing? LVM Setup - parted Error fsyncing/closing /dev/sdc: Input/output e"
date: 2014-11-16
forum: Hardware
---

### Post by chrisscott on 2014-11-16
Hi All!

So I wanted to combine two drives into one large media drive.  I already had a 2TB drive with data but I got a new 3TB drive.  The original wasn't setup as LVM so my plan was to make the new 3TB drive LVM, copy the data over from the 2TB and then reformat the 2TB drive and extend the LVM to include the 2TB to make a total of 5tb.  But I can't seem to get the new 3TB drive to work.  I think I'm doing something wrong.  Am I screwing this drive up or is it a bad drive?  I did this once already and the SMART tests would complete and say the drive was bad, so I returned it and got a new one, but now the SMART tests won't even complete and I have a slew of other problmes.  These were the steps I took with the new drive:

I'm on ubuntu 14.04 LTS 64bit

- parted /dev/sdc
-- mklabel gpt
-- unit TB
-- mkpart primary ext4 0.00TB 3.00TB
-- set 1 lvm on
- modprobe dm-mod
- added dm-mod to /etc/modules
- pvcreate /dev/sdc1
- vgcreate media /dev/sdc1
- lvcreate -l100%FREE -nvolume media
- mke2fs -t ext4 /dev/media/volume
- mount /dev/media/volume /media/Media

This seemed to work and I could start writing files to the drive.  While copying over the drive drops to read only and so I start a SMART test and it never finishes (even the quick test I let run over 24 hours and it hung on 90% remaining.  Then I reboot my machine and the file system wont mount and I can't view the partition anywhere.  

Fdisk -l doesn't even see /dev/sdc

parted -l gets this:

Error: /dev/sdc: unrecognised disk label                                  
Warning: Error fsyncing/closing /dev/sdc: Input/output error         

testdisk when analyzing gets tons of these errors in the testdisk.log:

file_pread(6,1,buffer,22784(1/106/42)) read err: Input/output error
file_pread(6,1,buffer,22805(1/106/63)) read err: Input/output error
file_pread(6,1,buffer,22855(1/107/50)) read err: Input/output error
file_pread(6,1,buffer,24768(1/138/10)) read err: Input/output error
file_pread(6,1,buffer,22735(1/105/56)) read err: Input/output error
file_pread(6,1,buffer,22738(1/105/59)) read err: Input/output error
file_pread(6,1,buffer,22785(1/106/43)) read err: Input/output error
file_pread(6,1,buffer,22806(1/107/1)) read err: Input/output error
file_pread(6,1,buffer,22856(1/107/51)) read err: Input/output error
file_pread(6,1,buffer,24769(1/138/11)) read err: Input/output error
file_pread(6,1,buffer,22721(1/105/42)) read err: Input/output error
file_pread(6,1,buffer,22722(1/105/43)) read err: Input/output error

and this from the analyze window:

Disk /dev/sdc - 3000 GB / 2794 GiB - CHS 364801 255 63
Analyse cylinder     1/364800: 00%
Read error at 0/254/63 (lba=16064)

in dmesg I get a bunch of these:

[149682.617967] sd 2:0:0:0: [sdc] CDB: 
[149682.631889] sd 2:0:0:0: [sdc] Unhandled sense code
[149682.631891] sd 2:0:0:0: [sdc]  
[149682.631895] sd 2:0:0:0: [sdc]  
[149682.631913] sd 2:0:0:0: [sdc]  
[149682.631919] sd 2:0:0:0: [sdc] CDB: 
[149682.645024] sd 2:0:0:0: [sdc] Unhandled sense code


I'm hoping (for my sanity) I got unlucky twice with two bad drives from Amazon, but I fear its something I did.  I don't care about any of the data on the drive, how can I "start over" with this drive?

Thanks in advance!

---

### Post by houstonbofh on 2014-11-16
Boot a gparted LiveCD and look at the drive.  [http://gparted.org/livecd.php](http://gparted.org/livecd.php)  This eliminates all variables.  If you can see it, wipe it and write a new partition table and format it.  Then boot Ubuntu and see if you can see the smart details.

---

### Post by chrisscott on 2014-11-16
Do I need to do that even if iTd just a media drive?  There is no OS on it. 

Thanks!

---

### Post by oldfred on 2014-11-17
Fdisk does not work on gpt partitioned drives.
I do not think that most partition tools work on LVM. You use the partition tools to create the underlying physical partition and then the LVM adds logical partition(s) inside the LVM.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

 lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

Best to have really good backups with LVM. If either drive fails you lose all data in both drives.

---

