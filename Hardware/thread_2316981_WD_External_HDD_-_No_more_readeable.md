---
title: "WD External HDD - No more readeable"
date: 2016-03-12
forum: Hardware
---

### Post by cedric11 on 2016-03-12
Hello, 

After 6 hours of trials I have no more solution to make my Western Digital HDD operating again.

_Problem:_
I share a NTFS WD HDD with my wife who is running under Windows. She used it a lot recently with my ubuntu to backup all her pictures. 
It leads to have HDD no more operational under its windows (it blocks Windows computers after mounting) but it was still operation under my ubuntu. 

Ubuntu version: 
```
cedric@laptop-cedric:~$ uname -a
Linux laptop-cedric 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:57:19 UTC 2016 i686 i686 i686 GNU/Linux

```

I tried to remove some no more used files on this disk, then also to launch some command line as **"sudo fsck -y /dev/sda1"**  or **"sudo ntfsfix /dev/sdb"**
But finally nothing is operational anymore... the drive is no more mounting on her Windows and now on my Ubuntu... 

HDD Hardware Version:
```
cedric@laptop-cedric:~$ sudo lsusb 
Bus 002 Device 008: ID 1058:0740 Western Digital Technologies, Inc. My Passport Essential (WDBACY)

```
No more disk found when I use command "sudo fdisk -l", it does not return my HDD. 

 I tried to use also testdisk or Photorec but the disk is no more detected... 

Error message from the disk: 
```

cedric@laptop-cedric:~$ dmesg | tail -n 30
[19052.828026] sd 10:0:0:0: [sdb] Sense Key : Not Ready [current] 
[19052.828029] sd 10:0:0:0: [sdb] Add. Sense: Logical unit is in process of becoming ready
[19054.847965] sd 10:0:0:0: [sdb] Test WP failed, assume Write Enabled
[19056.867921] sd 10:0:0:0: [sdb] Asking for cache data failed
[19056.867927] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[19056.875402] sd 10:0:0:0: [sdb] Spinning up disk...
[19059.888204] ......................................................................not responding...
[19309.365709] sd 10:0:0:0: timing out command, waited 180s
[19489.369634] sd 10:0:0:0: timing out command, waited 180s
[19669.377830] sd 10:0:0:0: timing out command, waited 180s
[19669.377855] sd 10:0:0:0: [sdb] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[19669.377859] sd 10:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[19669.377863] sd 10:0:0:0: [sdb] Add. Sense: Internal target failure
[19669.379084] sd 10:0:0:0: [sdb] Unit Not Ready
[19669.379086] sd 10:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[19669.379089] sd 10:0:0:0: [sdb] Add. Sense: Internal target failure
[19849.381646] sd 10:0:0:0: timing out command, waited 180s
[19849.383287] sd 10:0:0:0: timing out command, waited 180s
[20029.389590] sd 10:0:0:0: timing out command, waited 180s
[20029.389614] sd 10:0:0:0: [sdb] Attached SCSI disk
[20029.391226] sd 10:0:0:0: timing out command, waited 180s
[20209.393693] sd 10:0:0:0: timing out command, waited 180s
[20209.393770] sd 10:0:0:0: [sdb] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[20209.393783] sd 10:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[20209.393793] sd 10:0:0:0: [sdb] Add. Sense: Internal target failure
[20389.397739] sd 10:0:0:0: timing out command, waited 180s
[20569.405651] sd 10:0:0:0: timing out command, waited 180s
[20569.411013] sd 10:0:0:0: [sdb] Unit Not Ready
[20569.411018] sd 10:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[20569.411021] sd 10:0:0:0: [sdb] Add. Sense: Internal target failure

```

:confused::confused:
Next time I will backup my files before modifying anything.... 
I think the command line "ntfsfix /dev/sdb" broked something... 

Thanks for your support as I have no more solution from my side... 

Regards, 
Cédric

---

### Post by cedric11 on 2016-03-12
Hello, 

By the way error when trying to mount the device: 
```

cedric@laptop-cedric:~$ sudo ntfs-3g -o force,rw /dev/sdb /media/cedric/BOUCHET1/
Failed to read bootsector (size=0)
Failed to mount '/dev/sdb': Argument invalide
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

Something wrong on bootsector.

---

### Post by weatherman2 on 2016-03-12
The hard drive may have physically failed.  This is very common.  In Ubuntu, install GSmartControl (the graphic interface to smartmontools).  Then check the S.M.A.R.T. health of your drive, if you can see it at all.  After you install GSmartControl, you can also try from a terminal if you can't access S.M.A.R.T.

```
sudo smartctl -a /dev/sda
```

If that doesn't find the drive, try adding options "-d sat" and/or "-T permissive"

```

sudo smartctl -a  -d sat /dev/sda
sudo smartctl -a  -T permissive /dev/sda
sudo smartctl -a  -d sat  -T permissive /dev/sda

```

If you can get Attributes from that, post them here.

It's also possible the controller in the portable drive has failed.

---

### Post by Bashing-om on 2016-03-12
cedric11; Hey !

I am working a similar issue on my system with a WD backup drive failure. I 'think' I have it isolated to a bad/loose sata cable. I have better sata cables on order, will be a few days arriving . 
Once I have the drive back operational I will update my status.

My symptom is a intermittent loss of visibility to the drive, and I have messed up the partition table .

Your situation could be similar.

[INDENT][INDENT]I hate when that happens
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2016-03-12
You said this is an external drive but then used command "sudo fsck -y /dev/sda1" which will not be the external drive; sda1 is the first partition on the first (or only) internal HDD, so you have either told us incorrect information or you ran fsck on the wrong partition.

Either way fsck will do nothing for an NTFS partition, and to fix an NTFS partition you really need to use Windows not Linux.  I can not comment on ntfsfix, nor do I know if it is used on the whole disk, /dev/sdb or on a partition, /dev/sdb1.

---

### Post by weatherman2 on 2016-03-12
Bashing-om, you might check your power supply too.  I once had a flaky (internal) hard drive that got corrupted - and then I realized the power supply was failing intermittently.  Once I replaced it, the problems disappeared.  If these drives don't have reliable power, things can go terribly wrong.

I've seen poor SATA cables throw S.M.A.R.T. errors (CRC errors that were corrected successfully, supposedly due to the cabling)) but not cause corruption, though I suppose it's certainly possible.

---

### Post by Bashing-om on 2016-03-12
weatherman2; Hey !

I sure appreciate that heads up .. will keep the power supply voltages in mind.
Pending now is replacing the sata cable and powering the problematic drive back up ( smartctl sees no problem, certainly not definitive - but of some assurance ); maybe swapping out the sata controller port .. will see .. 

[INDENT][INDENT]could be, might be
[INDENT][INDENT][INDENT]but what is
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cedric11 on 2016-03-13
Hello wetherman2, 
Thank you for your support,device shall be mounted from /dev/sdb, the command seems to not return anything relevant, 

sudo smartctl -a  -d sat -T permissive /dev/sdb
> 
cedric@laptop-cedric:~$ sudo smartctl -a -d sat -T permissive /dev/sdb
smartctl 6.4 2014-10-07 r4002 [i686-linux-4.2.0-30-generic] (local build)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")

Read Device Identity failed: scsi error device will be ready soon

=== START OF INFORMATION SECTION ===
Device Model:     [No Information Found]
Serial Number:    [No Information Found]
Firmware Version: [No Information Found]
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   [No Information Found]
Local Time is:    Sun Mar 13 16:28:11 2016 CET
SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 82-83 don't show if SMART supported.
SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 85-87 don't show if SMART is enabled.
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.


Information about my disk:
> 
cedric@laptop-cedric:~$ sudo lshw -class disk  
  *-disk NON-RÉCLAMÉ      
       description: SCSI Disk
       produit: My Passport 0740
       fabriquant: WD
       identifiant matériel: 0.0.0
       information bus: scsi@14:0.0.0
       version: 1003
       numéro de série: WXQ1A9187706
       configuration: ansiversion=6


---

### Post by cedric11 on 2016-03-13
Hello ajgreeny, 

Yes, correct I did "sudo fsck -y /dev/sdb", (there is no partition on the disk), sorry the error. 
I also tried to perform check using chkdsk (chkdsk /r /f) command from windows but the volume does not success to be mounted on Windows. 
In the disk manager section the disk is "unknown" and widows require to "initialize" the disk...

Return of the command is perhaps strange, it seems limited to "ext2/ext3/ext4 " format not '"ntfs"
> cedric@laptop-cedric:~$ sudo fsck -y /dev/sdb
fsck de util-linux 2.26.2
e2fsck 1.42.12 (29-Aug-2014)
fsck.ext2: Argument invalide lors de la tentative d'ouverture de /dev/sdb

Le superbloc n'a pu être lu ou ne contient pas un système de fichiers
ext2/ext3/ext4 correct. Si le périphérique est valide et qu'il contient réellement
un système de fichiers ext2/ext3/ext4 (et non pas de type swap, ufs ou autre),
alors le superbloc est corrompu, et vous pourriez tenter d'exécuter
e2fsck avec un autre superbloc :
    e2fsck -b 8193 <périphérique>
 ou
    e2fsck -b 32768 <périphérique>


Regards,
Cédric

---

### Post by cedric11 on 2016-03-13
Hello Bashing-om, 

It is not an cable issue, I just use an other cable from an other Western Digital external drive I have, and it is exactly the same.
In my case I have no intermittent loss of visibility, I only never see my drive... 

Rgds, 
Cédric

---

### Post by yancek on 2016-03-13
> Return of the command is perhaps strange, it seems limited to "ext2/ext3/ext4 " format not '"ntfs"
                           

No, it's not strange it is what is expected as it is designed to only run those Linux filesystem and not the proprietary windows filesystems.  You need to use chkdsk from windows if the partition is windows (ntfs).  Your lshw output shows the WD drive, does it show in the BIOS?  The standard is to create a partition and mount the filesystem on it, i.e, sdb1.   See your output referencing this in post 3.  Not sure what the problem is.

---

### Post by montag dp on 2016-03-13
FYI on WD drives.  Apparently there is a feature called intellipark which causes them to get destroyed very quickly under Linux:

[https://forum.manjaro.org/index.php?topic=17890.0](https://forum.manjaro.org/index.php?topic=17890.0)

There is a solution mentioned in that thread. Although it is not Ubuntu, I think that it would also work in Ubuntu provided idle3ctl is available in the repos.  I don't know if it will solve the OP's problem, though, as his drive might already be failing.  But it would be good to know in the future or for other people using these drives.

---

