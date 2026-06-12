---
title: "Seagate expansion drive - dupe?"
date: 2016-08-11
forum: Hardware
---

### Post by Vaclav Vasek on 2016-08-11
This post is a dupe , since I cannot find my original here.
But I am adding some more info , errors now. 

I am trying to copy partitions from USB drive into Seagate Expansion Drive, running Ubuntu 16.04.

I can copy (cp) one or two partitions successfully, but the last one does something strange to the drive and I end up unable to even "Open" it on Desktop.

Here is a response to "fdisk -l" :, only the relevant Seagate HDD output is posted 


```
Disk /dev/sdd: 2.7 TiB, 3000592981504 bytes, 5860533167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: B69FED83-79A4-48E3-9313-55E477023D6B

Device      Start        End    Sectors  Size Type
/dev/sdd1      34     262177     262144  128M Microsoft reserved
/dev/sdd2  264192 5860532223 5860268032  2.7T Microsoft basic data
```

This is last line from fdisk , it is in red color and I am not sure which drive it belongs too.

[COLOR=#ff0000]Partition 1 does not start on physical sector boundary.[/COLOR]


And here is what "Open" get me - Unable to access... 

```
Error mounting /dev/sdd2 at /media/a/Seagate ONE: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdd2" "/media/a/Seagate ONE"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdd2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```
BTW - I have formated ( NTFS ) the Seagate drive and than I could "Open" it. 
But it took less than a second to format the 3TB (!) with NO feedback from Ubuntu (?) 


Is is possible, but would be stupid IMHO, that the "Microsoft reserved " stops Ubuntu ? 

I am looking at two options - fix this or return the drive to place of purchase - since it is marketed as Windows 7 and up "compatible". 

Please refrain from recommending  "use x instead of cp" , cp does work , slow but works.

---

### Post by wildmanne39 on 2016-08-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

I did not find a duplicate post, must have had a forum hiccup while you were trying to post the first time.

---

### Post by Vaclav Vasek on 2016-08-11
I am copying the data I want to save directly to working SATA drive, slow process.
Than I will reformat the Seagate using GParted and NTSF format. 
 Got nothing to lose but try that and if it does no fly , just return the drive. 
.
According to Seagate customer service the drive is designed (?) to work with Windows 7 and up ONLY. 
That is hard to swallow.

I am open to any other suggestion.

---

