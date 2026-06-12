---
title: "unable to mount ntfs partition"
date: 2009-02-07
forum: Hardware
---

### Post by ujwal10101 on 2009-02-07
please help! i'm unable to mount an ntfs partition (its got vista in it). i did chkdsk /f in windows and rebooted twice. it didn't help. it tried ntfsfix and got this output.

ujwal@ujwal-desktop:~$ sudo ntfsfix /dev/sda5
Mounting volume... pread: Input/output error
Failed to calculate number of free clusters: Input/output error.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
pread: Input/output error
Failed to calculate number of free clusters: Input/output error.
Remount failed: Input/output error.
please help!!!

---

### Post by AlexBellisBrown on 2009-02-07
Try downloading Mount manager from the add remove programs, that will let you set it to mount automatically on bootup. :)

---

### Post by taurus on 2009-02-07
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by ujwal10101 on 2009-02-08
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13991398

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       19457   115330635    f  W95 Ext'd (LBA)
/dev/sda5            5100       10198    40957686    7  HPFS/NTFS
/dev/sda6           10199       17847    61440561    7  HPFS/NTFS
/dev/sda7           17848       19383    12337888+  83  Linux
/dev/sda8           19384       19457      594373+  82  Linux swap / Solaris
```

yes i see something, i'm no expert but the start value of sda5, (the one i can't mount) is wrong. i've got 2 more ntfs partitions which i can mount without any problem. one of them has windows xp in it. xp can mount my vista partition.

---

### Post by caljohnsmith on 2009-02-08
Do you have a Windows Install CD? If not, you can download a Windows Recovery CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). I would boot that, go to the "recovery console" and do:
```
map
```
That will give the drive letters for all the partitions on your drive, so choose the one that is sda5 (it will be the 3rd NTFS partition listed by "map"), and then do:
```
chkdsk /r E:
```
But replace "E" with whichever is sda5's drive letter, and run the chkdsk command as many times as it takes until it reports no errors. Then try booting into Ubuntu again and mounting it, and please post any errors you might get. Also, please post:
```
sudo fdisk -lu
```
Note that uses "-lu" rather than "-l" so we can see the start/stop values of your partitions in sectors, rather than cylinders, which will help us discern if you might have a possible problem with your partition table (not likely, but it's worth checking). We can work from there if you want.

---

### Post by ujwal10101 on 2009-02-09
I don't need the Windows Recovery CD, as I can perfectly boot into both Vista and XP. I know which drive letter they use, Vista is installed on D: and my XP on C:. I also have a E: which contains mostly multimedia files as they are very large. As mentioned before, XP can mount D: (sda5 in Linux) without any problem.

I think chkdsk /r D: would attempt to recover the bad sectors. Let me clarify I used the graphical tool for chkdsk provided by windows as well. I checked both the options provided (fix and recover). I actually did this even before I posted this thread, then did it again after caljohnsmith told me to. Both times I got an error-free report. Still I was not able to mount it.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=102719&stc=1&d=1234157097[/IMG]

On typing the following ```
sudo fdisk -lu
``` i got the following output 

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13991398

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sda2        81915435   312576704   115330635    f  W95 Ext'd (LBA)
/dev/sda5        81915498   163830869    40957686    7  HPFS/NTFS
/dev/sda6       163830933   286712054    61440561    7  HPFS/NTFS
/dev/sda7       286712118   311387894    12337888+  83  Linux
/dev/sda8       311387958   312576704      594373+  82  Linux swap / Solaris
```

---

### Post by ujwal10101 on 2009-02-09
bump

---

### Post by caljohnsmith on 2009-02-09
Just so we can see exactly what error you are getting when trying to mount sda5, how about posting:
```
sudo mount -t ntfs-3g -o force /dev/sda5 /mnt && ls -l /mnt

```
And in order to get an idea of what type of boot sector your sda5 partition has, how about posting the output of:
```
sudo xxd -s 128 -l 2 -p /dev/sda5
```
And lastly, I would recommend using testdisk to check your sda5 partition boot sector; first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows sda5 partition, choose "Boot", then choose "Rebuild BS"; please post the output of that screen.

---

### Post by ujwal10101 on 2009-02-09
When I do 
```
sudo mount -t ntfs-3g -o force /dev/sda5 /mnt && ls -l /mnt
``` i get the following 
```
ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
```
When I do ```
sudo xxd -s 128 -l 2 -p /dev/sda5 

``` i get ```
08cd
```
on running testdisk and after doing the mention steps i get 
```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition                  Start        End    Size in sectors
 5 L HPFS - NTFS           5099   1  1 10197 254 63   81915372

filesystem size           81915372 81915372
sectors_per_cluster       8 8
mft_lcn                   786432 786432
mftmirr_lcn               5119710 5119710
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
Extrapolated boot sector and current boot sector are different.

```
testdisk was able to list the directories and files of sda5, something i was able to do for the first time in linux.

---

### Post by caljohnsmith on 2009-02-09
OK, I would go ahead and let testdisk fix your sda5 boot sector, because it looks like that is at least part of the issue. You can do that by selecting "write" in that testdisk screen you posted. Then quit testdisk and again try:
```
sudo mount -t ntfs-3g -o force /dev/sda5 /mnt && ls -l /mnt
```
And please post the output.

---

### Post by ujwal10101 on 2009-02-09
ok i did "write" in testdisk, it told me i may have to reboot for the effect to take place, so i did. I still couldn't mount it and i get the same error message as before.
For ```
sudo mount -t ntfs-3g -o force /dev/sda5 /mnt && ls -l /mnt
```
I get
```
ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```

---

### Post by caljohnsmith on 2009-02-09
How about trying the following:
```
sudo testdisk /dev/sda5
```
Choose "Proceed", "None", "Analyze", "Quick Search", then press "p" to list the root directory of the sda5 NTFS partition. Does that work or does it give you an error?

---

### Post by ujwal10101 on 2009-02-09
yes it works. but i'm still not able to mount it.

---

### Post by ujwal10101 on 2009-02-09
bump

---

### Post by ujwal10101 on 2009-02-10
bump

---

### Post by caljohnsmith on 2009-02-10
Ujwal10101, please follow the forum rules and do not bump the thread sooner than every 24 hours. I would recommend running the testdisk procedure again from post #8, except instead of choosing "Rebuild BS", this time choose "Repair MFT" if that option is available for the sda5 partition. If testdisk allows you to use that option, try mounting the sda5 partition again after you finish with testdisk and please post the results.

---

### Post by ujwal10101 on 2009-02-11
sorry to have bumped the thread twice in the same day. i did what u said, but it says ```
Can't read NTFS MFT mirror.
``` Pardon me if i'm wrong, but it seems what i did now was pretty similar to what i did with ntfsfix (see post #1).

---

### Post by caljohnsmith on 2009-02-11
Since we have changed some things about your NTFS partition with testdisk, can you run "chkdsk /r" on your sda5 partition again from Windows? Let me know what that returns. Also, please post the output of:
```

sudo umount /mnt
sudo mount -o loop,offset=$((81915498*512)) -t ntfs-3g /dev/sda /mnt && ls -l /mnt
```

---

### Post by ujwal10101 on 2009-02-13
nothing is mounted at /mnt.
the second command does nothing at all.

---

### Post by ujwal10101 on 2009-02-14
bump

---

### Post by dE_logics on 2010-04-21
Well then... bump.

---

### Post by dE_logics on 2010-04-21
> **caljohnsmith said:**
> OK, I would go ahead and let testdisk fix your sda5 boot sector, because it looks like that is at least part of the issue. You can do that by selecting "write" in that testdisk screen you posted. Then quit testdisk and again try:
```
sudo mount -t ntfs-3g -o force /dev/sda5 /mnt && ls -l /mnt
```
And please post the output.

IT DID IT!!!!...Thanks man!!

---

### Post by dE_logics on 2010-04-22
No, it did not work... my fault.

---

### Post by chmacka on 2010-06-04
I have the same problem:

```

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```I just don't understand how **I can access all of the files** on my external hard disk and copy them to another disk **with** **testdisk** (view animated .gif) but I can't open the external hard disk at all from nautilus, terminal or Windows. I can't run chkdsk on Windows cause it says that filesystem on the external hard disk is RAW.

---

