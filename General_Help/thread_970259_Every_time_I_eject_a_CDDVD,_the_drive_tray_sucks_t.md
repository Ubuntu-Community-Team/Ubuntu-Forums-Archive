---
title: "Every time I eject a CD/DVD, the drive tray sucks the disc back in on its own"
date: 2008-11-04
forum: General Help
---

### Post by diablo75 on 2008-11-04
This problem has been going on since I upgraded to 8.10.  Right now, I have a DVD in my burner that, if I open up nautilus and use the new quick-eject button to eject the disc, the tray will pop out... and then less than a second later, go back in.

If that's not strange enough, this same thing happens if I eject the disc using the button on the front of the physical drive it self.  I've done this with 100 percent consistency 6 times in a row, and the software I used to burn the disc is not running (I've checked system monitor's process viewer for brasero).  The only time it doesn't do this is if the drive contains no disc, and in order for that to happen, I have to grab it very quickly before it sucks the tray back in.  What might be causing my DVD drive to do this?  Is this happening with anybody else out there?

---

### Post by Peter09 on 2008-11-04
This is a known bug

[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/283316](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/283316)

---

### Post by ProgramErgoSum on 2008-11-04
If this was fiction, I would have laughed out loud !

:rolleyes:

---

### Post by sdowney717 on 2008-11-04
when it ejects grab the tray and forceably hold it out, it will comply.
or cycle it twice -- out, in, out and it will stay out on the second button push.
this is a known bug that never got fixed. In fact you got to wonder why seeing this would effect so many people.


here is a fix that people say will work, and i tried it and it DOES WORK fine.


[email]/email]  wrote on 2008-11-01:  (permalink)

    * Modified to include untested patch for cd/dvd tray issue (3.7 KiB, text/plain)

i can confirm this issue exists, brasero is currently (for me at least) impossible due to the speed at which the tray opens and closes itself

i made a one-line fix to /etc/udev/rules.d/60-persistent-storage.rules that seemed to solve the problem without even rebooting the machine, it was mentioned in another thread...look for the following in said file:

# skip unpartitioned removable media devices from drivers which do not send "change" events
ENV{DEVTYPE}=="disk", KERNEL!="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"

just beneath the second line, add the following (make sure to back up your original):

ENV{DEVTYPE}=="disk", KERNEL=="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"

(the subtle difference is in the "KERNEL" portion)

i'll attach my "version" of the file in case anyone would like to try it themselves as a temporary workaround:

---

### Post by lukjad on 2008-11-04
Shouldn't there be an easy fix? I mean, this *is* a major release, not a Release Candidate.

---

### Post by Peter09 on 2008-11-04
There is an easy fix (read dirty workaround :p)

It is described in the bug report in launchpad.

---

### Post by philinux on 2008-11-04
When it's gone back in just push the eject button.

---

### Post by rbmorse on 2008-11-04
Sdowney717: You need to restart udev after you edit the rules file:

sudo /etc/init.d/udev restart

**UPDATE:  Syslog says the following is invalid**

All I did was delete the "!" character from the line:

> ENV{DEVTYPE}=="disk", KERNEL!="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"then restarted udev. Seems to fix the immediate retraction problem, but I haven't tested to ensure it doesn't break something else.

---

### Post by shane19174 on 2008-11-04
In fact you don't have to do the manual workaround if you don't want. A fix has been submitted to the intrepid-proposed repository. If you temporarily enable the repo and install the updated version of udev, it should be fixed without any manual editing. If you don't know what you're doing or don't want to risk breaking anything, don't install any of the other updates and disable the proposed repository after getting udev.

Hope this helps someone.

---

### Post by rfurman24 on 2008-11-06
> **rbmorse said:**
> Sdowney717: You need to restart udev after you edit the rules file:

sudo /etc/init.d/udev restart

**UPDATE:  Syslog says the following is invalid**

All I did was delete the "!" character from the line:

then restarted udev. Seems to fix the immediate retraction problem, but I haven't tested to ensure it doesn't break something else.



After trying all other suggestions and even doing the "proposed" upgrade this finally fixed it.


I spoke to soon. It is still broken.

---

### Post by ferral-cat on 2008-11-06
I was able to solve the problem by upgrading the package named "udev" from the old version 124-8 to the new version 124-9 that is available from the repository named "intrepid-proposed"

Here are instructions that are Noobie Friendly:

Open Synaptic with System > Administration > Synaptic Package Manager (or you can also do it by pressing Alt+F2 and "synaptic")

Once you have Synaptic open then go to Settings > Repositories

Click the "Updates" tab

Tick the checkbox next to "Prereleased updates (intrepid-proposed)"

Untick the checkboxes from the other 3 sources.

Click close button.  A warning will come up saying you need to hit the reload button.  Hit the reload button.  Now search for "udev" package.  Upgrade to version 124-9.  Hit Apply button at the top.  

After udev has been successfully upgraded to version 124-9 then go back and remove the tick from "Prereleased updates (intrepid-proposed)"

Restore the ticks to the way they where before.  In my case I have only the first 2 sources ticked.  

Hit reload. 

Exit Synaptic and reboot your computer.  

This should fix your eject problem. :guitar:

---

### Post by rfurman24 on 2008-11-06
I have tried that and it did nothing.

---

### Post by rfurman24 on 2008-11-06
Can you post a copy of your /etc/udev/rules.d/60-persistent-storage.rules?
I thought I backed mine up but can not find it.

---

### Post by rfurman24 on 2008-11-06
Never mind I downgraded udev and then upgraded again.

---

### Post by rfurman24 on 2008-11-06
Still broken on one of two drives. Both ide.

---

### Post by ciscosurfer on 2008-11-06
> **rfurman24 said:**
> Still broken on one of two drives. Both ide.Can you post the output of **sudo fdisk -l** (just curious about something)

---

### Post by rfurman24 on 2008-11-06
I will in the morning when I get home from work. Thanks.

---

### Post by ferral-cat on 2008-11-06
Im sorry to hear of your trouble.  Here is my 

 /etc/udev/rules.d/60-persistent-storage.rules

But this is after upgrading the udev package.  Keep in mind the only thing I have ever done is upgrade the udev package.  I never modified any of the text.  

```

# do not edit this file, it will be overwritten on update

# persistent storage links: /dev/disk/{by-id,by-uuid,by-label,by-path}
# scheme based on "Linux persistent device names", 2004, Hannes Reinecke <hare@suse.de>

# forward scsi device event to corresponding block device
ACTION=="change", SUBSYSTEM=="scsi", ENV{DEVTYPE}=="scsi_device", TEST=="block", ATTR{block/*/uevent}="change"

ACTION!="add|change", GOTO="persistent_storage_end"
SUBSYSTEM!="block", GOTO="persistent_storage_end"

# skip rules for inappropriate block devices
KERNEL=="ram*|loop*|fd*|nbd*|gnbd*|dm-*|md*", GOTO="persistent_storage_end"

# never access non-cdrom removable ide devices, the drivers are causing event loops on open()
KERNEL=="hd*[!0-9]", ATTR{removable}=="1", DRIVERS=="ide-cs|ide-floppy", GOTO="persistent_storage_end"
KERNEL=="hd*[0-9]", ATTRS{removable}=="1", GOTO="persistent_storage_end"

# ignore partitions that span the entire disk
TEST=="whole_disk", GOTO="persistent_storage_end"

# /sys/class/block will export this
ENV{DEVTYPE}!="?*", ATTR{range}=="?*", ENV{DEVTYPE}="disk"
ENV{DEVTYPE}!="?*", ATTR{start}=="?*", ENV{DEVTYPE}="partition"

# for partitions import parent information
ENV{DEVTYPE}=="partition", IMPORT{parent}="ID_*"

# by-id (hardware serial number)
KERNEL=="hd*[!0-9]", IMPORT{program}="ata_id --export $tempnode"
KERNEL=="hd*[!0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/ata-$env{ID_MODEL}_$env{ID_SERIAL}"
KERNEL=="hd*[0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/ata-$env{ID_MODEL}_$env{ID_SERIAL}-part%n"

KERNEL=="sd*[!0-9]|sr*", ATTRS{ieee1394_id}=="?*", ENV{ID_SERIAL}="$attr{ieee1394_id}", ENV{ID_BUS}="ieee1394"
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}!="?*", SUBSYSTEMS=="usb", IMPORT{program}="usb_id --export %p"
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}!="?*", IMPORT{program}="scsi_id --export --whitelisted -d $tempnode", ENV{ID_BUS}="scsi"
KERNEL=="cciss?c[0-9]d[0-9]", ENV{ID_SERIAL}!="?*", IMPORT{program}="scsi_id --export --whitelisted -d $tempnode", ENV{ID_BUS}="cciss"
KERNEL=="sd*[!0-9]|sr*|cciss?c[0-9]d[0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}"
KERNEL=="sd*[0-9]|cciss*p[0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}-part%n"

# libata compat (links like hd*)
KERNEL=="sd*[!0-9]|sr*", ENV{ID_VENDOR}=="ATA", PROGRAM="ata_id $tempnode", RESULT=="?*", ENV{ID_ATA_COMPAT}="$result", SYMLINK+="disk/by-id/ata-$env{ID_ATA_COMPAT}"
KERNEL=="sd*[0-9]", ENV{ID_ATA_COMPAT}=="?*", SYMLINK+="disk/by-id/ata-$env{ID_ATA_COMPAT}-part%n"

KERNEL=="mmcblk[0-9]", SUBSYSTEMS=="mmc", ATTRS{name}=="?*", ATTRS{serial}=="?*", ENV{ID_NAME}="$attr{name}", ENV{ID_SERIAL}="$attr{serial}", SYMLINK+="disk/by-id/mmc-$env{ID_NAME}_$env{ID_SERIAL}"
KERNEL=="mmcblk[0-9]p[0-9]", ENV{ID_NAME}=="?*", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/mmc-$env{ID_NAME}_$env{ID_SERIAL}-part%n"

# by-path (shortest physical path)
ENV{DEVTYPE}=="disk", IMPORT{program}="path_id %p"
ENV{DEVTYPE}=="disk", ENV{ID_PATH}=="?*", SYMLINK+="disk/by-path/$env{ID_PATH}"
ENV{DEVTYPE}=="partition", ENV{ID_PATH}=="?*", SYMLINK+="disk/by-path/$env{ID_PATH}-part%n"

# skip unpartitioned removable media devices from drivers which do not send "change" events
ENV{DEVTYPE}=="disk", KERNEL!="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"
# skip optical drives without media
ENV{DEVTYPE}=="disk", KERNEL=="sr*", ENV{ID_CDROM_MEDIA_TRACK_COUNT}!="?*", GOTO="persistent_storage_end"

# import filesystem metadata
IMPORT{program}="vol_id --export $tempnode"

# by-label/by-uuid links (filesystem metadata)
ENV{ID_FS_USAGE}=="filesystem|other|crypto", ENV{ID_FS_UUID_ENC}=="?*", SYMLINK+="disk/by-uuid/$env{ID_FS_UUID_ENC}"
ENV{ID_FS_USAGE}=="filesystem|other", ENV{ID_FS_LABEL_ENC}=="?*", SYMLINK+="disk/by-label/$env{ID_FS_LABEL_ENC}"

LABEL="persistent_storage_end"

```

I only have one SATA dvd-rw drive.  I am using a Dell Vostro 200 Tower.  

Ubuntu 8.10 installed 2 days ago.  (fresh install)

---

### Post by rfurman24 on 2008-11-06
Thanks for posting it. It looks just like mine.

---

### Post by rfurman24 on 2008-11-07
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f345a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       30281       30401      971932+  82  Linux swap / Solaris
/dev/sda2               1          18      144553+  83  Linux
/dev/sda3              19        2450    19535040   83  Linux
/dev/sda4            2451       30280   223544475   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095eb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          18      144553+  83  Linux
/dev/sdb2              19        1355    10739452+  83  Linux
/dev/sdb3            1356       30280   232340062+  83  Linux
/dev/sdb4           30281       30401      971932+  82  Linux swap / Solaris

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       60800   488375968+  83  Linux

---

