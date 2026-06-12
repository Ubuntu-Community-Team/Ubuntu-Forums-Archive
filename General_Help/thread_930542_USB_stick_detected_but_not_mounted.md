---
title: "USB stick detected but not mounted"
date: 2008-09-26
forum: General Help
---

### Post by vlc on 2008-09-26
Hi *,

I currently have a problem that a USB stick is recognized, but not mounted. After plugging it in, I can see that it has been detected and scanned in the system log:

```

Sep 26 13:01:02 albacete kernel: [ 1633.363628] usb 5-7: new high speed USB device using ehci_hcd and address 5
Sep 26 13:01:02 albacete kernel: [ 1633.498372] usb 5-7: configuration #1 chosen from 1 choice
Sep 26 13:01:02 albacete kernel: [ 1633.503356] scsi7 : SCSI emulation for USB Mass Storage devices
Sep 26 13:01:02 albacete kernel: [ 1633.504072] usb-storage: device found at 5
Sep 26 13:01:02 albacete kernel: [ 1633.504076] usb-storage: waiting for device to settle before scanning
Sep 26 13:01:02 albacete NetworkManager: <debug> [1222426862.535732] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_077A05B40D55'). 
Sep 26 13:01:02 albacete NetworkManager: <debug> [1222426862.625218] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_077A05B40D55_if0'). 
Sep 26 13:01:07 albacete kernel: [ 1638.500213] usb-storage: device scan complete
Sep 26 13:01:07 albacete kernel: [ 1638.500833] scsi 7:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
Sep 26 13:01:07 albacete NetworkManager: <debug> [1222426867.609912] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_077A05B40D55_if0_scsi_host'). 
Sep 26 13:01:07 albacete NetworkManager: <debug> [1222426867.613746] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_077A05B40D55_if0_scsi_host_scsi_device_lun0'). 
Sep 26 13:01:07 albacete kernel: [ 1638.715377] sd 7:0:0:0: [sdb] 4030464 512-byte hardware sectors (2064 MB)
Sep 26 13:01:07 albacete kernel: [ 1638.716126] sd 7:0:0:0: [sdb] Write Protect is off
Sep 26 13:01:07 albacete kernel: [ 1638.716133] sd 7:0:0:0: [sdb] Mode Sense: 23 00 00 00
Sep 26 13:01:07 albacete kernel: [ 1638.716139] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Sep 26 13:01:07 albacete kernel: [ 1638.718996] sd 7:0:0:0: [sdb] 4030464 512-byte hardware sectors (2064 MB)
Sep 26 13:01:07 albacete kernel: [ 1638.719747] sd 7:0:0:0: [sdb] Write Protect is off
Sep 26 13:01:07 albacete kernel: [ 1638.719753] sd 7:0:0:0: [sdb] Mode Sense: 23 00 00 00
Sep 26 13:01:07 albacete kernel: [ 1638.719785] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Sep 26 13:01:07 albacete kernel: [ 1638.719791]  sdb: sdb1
Sep 26 13:01:07 albacete kernel: [ 1638.720985] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Sep 26 13:01:07 albacete kernel: [ 1638.721054] sd 7:0:0:0: Attached scsi generic sg2 type 0
Sep 26 13:01:07 albacete NetworkManager: <debug> [1222426867.764241] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13fe_1d00_077A05B40D55_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Sep 26 13:01:08 albacete NetworkManager: <debug> [1222426868.364667] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_2E09_1CC4'). 
Sep 26 13:01:08 albacete NetworkManager: <debug> [1222426868.407268] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial__USB_DISK_2_0_077A05B40D55_0_0'). 
```

When running fstab -l, the stick is also displayed:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7872     2015216    e  W95 FAT16 (LBA)
```

Now I can manually mount the stick by executing something like

```

$ sudo mkdir /media/USB
$ sudo mount /dev/sdb1 /media/USB
```

But mounting / unmounting the stick by hand is a kind of annoying, so I would like to have it done automatically, what normally should be working.

Does anyone has an idea why the stick is not mounted?

Thanks a lot in advance!

---

### Post by mailtwogopal on 2008-09-26
Hi,

  Probably [this]("http://ubuntuforums.org/showthread.php?t=80070") may help you, as this is solved. Also try [this]("http://www.mydigitallife.info/2006/09/10/how-to-mount-usb-disk-drive-in-unix-or-linux/") and let us know what happen?

---

### Post by vanadium on 2008-09-26
@mailtwogopal: please do not link to threads that just link to other trheads. that is just not helpfull. You might also have noticed that the other article you referred to does apply to older linux distributions where USB sticks are noot automounted.

That said, as far as I can be helpful, I do not see anything going wrong in the output the original poster provided. You should probably check first whether your USB effectively is not being automatically mounted using the "mount" command. It is possible that it is being mounted after all, but that the icon does not automatically appear on the desktop.

Something else to check is whether the file system on the USB is healthy. If you are still using Windows, you can use the command "chkdsk /f" to check and repair the volume. In Linux, you can use "dosfsck" to check and repair fat volumes.

---

### Post by vlc on 2008-09-26
The USB stick is not automounted, it does not appear in the output of the mount command.

The file system itself seems to be okay, after mounting it by hand I can read the files without problems. And dosfsck gives the following output:

```
$ sudo dosfsck /dev/sdb1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Reclaimed 1 unused cluster (32768 bytes).
Leaving file system unchanged.
/dev/sdb1: 226 files, 11444/62967 clusters
```

---

### Post by kpkeerthi on 2008-09-26
You may want to reformat the flash drive using gparted and try again.

---

### Post by mc4man on 2008-09-26
What does this show  (inserted but not mounted
```

gnome-mount -vbd /dev/sdb1
```

---

### Post by vanadium on 2008-09-26
The output of dosfsck anyway indicates that there is a problem with the file system. Before trying anything else, see whether repairing the file system fixes the issue.

---

### Post by vlc on 2008-09-26
Thanks a lot for the replies. I can try to reformat the USB stick, but the very same stick is mounted at another PC running the same Ubuntu version (8.04.1) without problems. So I don't think that this is the actual problem.

---

### Post by vanadium on 2008-09-27
Do not reformat it, just repair it. In dos, you would have used "chkdsk a: /f". I guess the equivalent command in linux would be "dosfsck -a /dev/sdbs" for automatic repair, or the "-r" option for interactive repair (program asks what approach to take). There is no point starting troubleshooting the OS before the file system is healthy.

---

### Post by vlc on 2008-09-29
I repaired the file system using *sudo dosfsck -a /dev/sdb1*, but the problem persists: The USB stick is detected and scanned, but not mounted.

```
$ sudo dosfsck /dev/sdb1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb1: 227 files, 11445/62967 clusters
```

---

### Post by vanadium on 2008-09-29
You already showed you can mount it manually without a problem. This means that the problem is in the combination of your USB stick (hardware or the way it is partitioned) and the automatic mounting mechanism. I cannot help further in this. At this point, I would now also recommend reformatting the USB stick as kpkeerthi suggested and see whether the issue persists. A next step would be to repartition and reformat. This will eliminate the possibility that the issue is caused by some issue with the partitioning or formatting of the stick.

---

### Post by Causer1984 on 2008-09-29
[URL="http://ubuntuforums.org/showthread.php?t=582045"]http://ubuntuforums.org/showthread.php?t=582045
[/URL]Does this do anything for you?

Apparently, it might still be an issue in Hardy

---

### Post by vlc on 2008-09-29
> **mc4man said:**
> What does this show  (inserted but not mounted
```

gnome-mount -vbd /dev/sdb1
```

```
$ gnome-mount -vbd /dev/sdb1
gnome-mount 0.8
** (gnome-mount:9209): DEBUG: Mounting /org/freedesktop/Hal/devices volume_uuid_2E09_1CC4
** (gnome-mount:9209): DEBUG: read default option 'shortname=mixed' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:9209): DEBUG: read default option 'uid=' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:9209): DEBUG: read default option 'utf8' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:9209): DEBUG: read default option 'umask=077' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:9209): DEBUG: read default option 'exec' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:9209): DEBUG: read default option 'flush' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:9209): DEBUG: Mounting /org/freedesktop/Hal/devices/volume_uuid_2E09_1CC4 with mount_point='USB', fstype='', num_options=6
** (gnome-mount:9209): DEBUG:   option='shortname=mixed'
** (gnome-mount:9209): DEBUG:   option='uid=1213'
** (gnome-mount:9209): DEBUG:   option='utf8'
** (gnome-mount:9209): DEBUG:   option='umask=077'
** (gnome-mount:9209): DEBUG:   option='exec'
** (gnome-mount:9209): DEBUG:   option='flush'
Mounted /dev/sdb1 at "/media/USB"
```

---

### Post by vlc on 2008-09-29
> **Causer1984 said:**
> [URL="http://ubuntuforums.org/showthread.php?t=582045"]http://ubuntuforums.org/showthread.php?t=582045
[/URL]Does this do anything for you?

Apparently, it might still be an issue in Hardy

I'm now through with all the suggestions in this thread, but the USB stick is still not auto-mounted.

Bad luck :(

---

### Post by mc4man on 2008-09-29
> ** (gnome-mount:9209): DEBUG:   option='uid=1213'

I would think that should be *option='uid=1000'*, that's what I see on all of mine that auto mount correctly.



what happens if you comment out or remove the fstab entry?

---

### Post by vlc on 2008-09-29
> **mc4man said:**
> what happens if you comment out or remove the fstab entry?

Actually, there is no entry for the USB stick in my fstab.

---

### Post by mc4man on 2008-09-29
> there is no entry for the USB stick in my fstab

Sorry I should have read back, just thought I'd seen an fstab entry.

Otherwise don't know, was just an observation about on all of my flash drives of varying brands, file systems they all show the option='uid=1000.
why don't you just transfer the files and repartition as suggested?


edit; just for curiosity sake set up a flash drive with uid=1213 on the *volume*, didn't prevent it from being auto mounted, just prevented me writing to it. Changing back to uid=1000 allowed writing (and added back the orange usb icon to mounted drive icon which is also tied to browse media upon insertion

Though being somewhat thick at times it just stuck me the mount options are  irrelevant to automounting, did learn some stuff about how to change the settings and if you screw up how to fix in the configuration editor

edit 2 : While a lot of the settings in the configuration editor have no effect or only reflect settings made elsewhere came across this one which is active. (many in apps -> nautilus are.
If it's unchecked the drive (removable media) won't mount. ( there's another one that hides or shows the icon in the desktop folder

---

### Post by vlc on 2008-09-30
@mc4man: unfortunately not. The entries *apps/nautilus/preferences/media_automount*, *apps/nautilus/preferences/show_desktop* and *apps/nautilus/desktop/volumes_visible* are all set.

Nevertheless, thanks a lot for your help!

---

### Post by Causer1984 on 2008-09-30
I know it's a sloppy workaround, but what would you say about creating your own udev rule?

I've got (a little) experience (a very little) in that, so if you want help, that could be arranged.

---

### Post by vlc on 2008-10-03
@Causer1984: Thanks for your offer! I already started an "investigation" in the udev rules, but I haven't found anything yet and actually, currently I don't have the patience - quite busy at work.

I put a button which mounts the USB stick with one click and I can live with this right now.

Nevertheless, thanks a lot!

---

