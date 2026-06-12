---
title: "gnome auto mount fails"
date: 2008-08-15
forum: General Help
---

### Post by piotrekno1 on 2008-08-15
Hello,

After a while of using a fresh hardy install i've encountered a problem with automounting removable devices.

1)Plugging a pendrive doesn't create a icon on the desktop - in fact the device doesn't mount. Here are the logs:

dmesg -tail

```


[  108.541367] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[  108.731749] sd 2:0:0:0: [sdb] 4014080 512-byte hardware sectors (2055 MB)
[  108.732490] sd 2:0:0:0: [sdb] Write Protect is off
[  108.732497] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  108.732501] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  108.737005] sd 2:0:0:0: [sdb] 4014080 512-byte hardware sectors (2055 MB)
[  108.737752] sd 2:0:0:0: [sdb] Write Protect is off
[  108.737760] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  108.737763] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  108.737772]  sdb: sdb1
[  108.738947] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  108.739015] sd 2:0:0:0: Attached scsi generic sg2 type 0


```

So everything seems to go well. After that i'm able to mount the device by
typing mount -t vfat /dev/sdb1 /mnt  but that's irritating.

2)Plugging a CD/DVD disc into the DVD-ROM doesn't create an icon on the desktop + no autmount here ;/ . Im able to mount it by hand typing 
mount /dev/scd0 /media/cdrom0

3)Plugging a Audio CD (from a music shop) auto mounts properly! A desktop icon is created

here's my fstab:

```


/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6
UUID=43702fe4-2369-40f4-92ef-e5c561e602a1 /               ext2    relatime,errors=remount-ro 0       1
/dev/sda7
UUID=714d41b5-dc46-c3a4-989d-ea7fe56bf0f0 none            swap    sw              0       0
/dev/sda5		/media/WinXP	ntfs	defaults,locale=pl_PL.UTF-8	0	0
/dev/sda8		/media/Shared	vfat	rw,uid=1000,gid=1000		0	0
/sda/sda2		/media/Service	vfat	rw,uid=1000,gid=1000		0	0	


```

Heres my hal preferences.fdi:

```


<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<!-- 
  Some examples how to use hal fdi files for system preferences 
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
<deviceinfo version="0.2">
<!-- 
  The following shows how to hint gnome-volume-manager and other programs 
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->

  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">true</merge>
      </match>
    </match>
  </device>



<!-- 
  The following shows how to put sync and noatime on for devices smaller then
  1Gb and off for device larger then that. Note that the sync option can wear
  out device faster then you'd like too. See
  http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html for
  more info.
--> 
<!--
  <device> 
    <match key="block.is_volume" bool="true">
      <match key="volume.size" compare_lt="1000000000">
        <match key="@block.storage_device:storage.hotpluggable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">true</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
        </match>
        <match key="@block.storage_device:storage.removable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">true</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
        </match>
      </match>
      <match key="volume.size" compare_ge="1000000000">
        <match key="@block.storage_device:storage.hotpluggable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">false</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">false</merge>
        </match>
        <match key="@block.storage_device:storage.removable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">false</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">false</merge>
        </match>
      </match>
    </match>
  </device>
--> 
</deviceinfo>


```

I've tried reinstalling hal,libhal1,libhal-*** - no effect.

I have found many topics considering this subject but non of the given solutions worked for me.


any clues what seems to be the problem?

---

### Post by piotrekno1 on 2008-08-16
still waiting....

---

