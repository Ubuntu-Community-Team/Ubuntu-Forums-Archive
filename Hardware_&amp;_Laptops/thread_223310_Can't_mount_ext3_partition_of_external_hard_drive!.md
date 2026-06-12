---
title: "Can't mount ext3 partition of external hard drive! Why?"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by KillrBuckeye on 2006-07-26
I have a new external hard drive on which I've created 3 partitions.  One is NTFS (created using Windows disk management), the second is ext3, and the third is FAT32 (ext3 and FAT32 partitions created using GParted).  At first I didn't have any fstab entry for these partitions, and automount wouldn't give me write permissions.  I assume this is because the filesystems were created with root ownership.  

Anyhow, I've created fstab entries for all 3 partitions, and the NTFS and FAT32 partitions will mount with no problems.  However, my ext3 partition is giving me all sorts of problems.  It will *sometimes* mount if I give a "sudo mount /dev/sda2", but other times it gives me the following error:

"mount: wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or other error"

Also, I can mount the NTFS and FAT32 partitions as "user", but the ext3 partition requires "sudo".  What's going on?  Here is my fstab for the devices:

```
/dev/sda1	/media/USB_NTFS ntfs    auto,user,ro,umask=000  0     0
/dev/sda2       /media/USB_ext3 ext3    auto,user,umask=0  0    0
/dev/sda3       /media/USB_FAT  vfat    auto,user,rw,exec,umask=000   0   0
```
The mount locations are owned by user.  Any ideas?

---

### Post by simonn on 2006-07-26
umask is not a valid option for ext3 file systems (see man mount).

umask is only needed/valid when the file system does not support permissions natively.

---

### Post by KillrBuckeye on 2006-07-26
Thanks, you are right.  I got it working now, but I'm still working on the fstab.  I'd like to set up the devices to be mounted according to label, but I'm having some trouble.

---

### Post by simonn on 2006-07-26
> **KillrBuckeye said:**
>  I'd like to set up the devices to be mounted according to label, but I'm having some trouble.

Like what? I can't help unless I know what is happening.

By "label", do you mean "/media/USB_ext3"?

---

### Post by KillrBuckeye on 2006-07-26
> **simonn said:**
> Like what? I can't help unless I know what is happening.

By "label", do you mean "/media/USB_ext3"?I'm sorry, I am getting confused as I go along, but I seem to be figuring it out bit-by-bit.  I tried setting a label for the ext3 partition using the "e2label" command so that I could reference it in the fstab by this name instead of /dev/sda2.  The idea is to avoid conflicts if I connect a different USB storage device.  Anyhow, ever since I tried doing this, I am having a few strange problems.  One is that when Ubuntu is booting up, it fails on the "Checking all filesystems" step, reporting that there is "No such file or directory while trying to open /dev/sda2".  However, if I continue to boot ignoring this error, all 3 partitions seem to be mounted correctly.  Finally, I am unable to unmount the partitions as user.  I must do it manually from the command line using "sudo umount".  I don't know what to do next, and I have made so many changes to fstab and my /media mount points that I've lost track of everything.

---

### Post by KillrBuckeye on 2006-07-26
Okay here's the status of my issue:  Everything works great now when I plug in the drive after Ubuntu is booted.  My fstab file has been edited such that all mount locations and permissions are the way I want them.  However, during the boot process the filesystem check will fail when it tries to mount the partitions as specified in the fstab file, regardless of whether the drive is plugged in or not.  What are my options at this point?  Is there some option in fstab to specify whether to perform a boot-time mount?

---

### Post by simonn on 2006-07-26
Sorry, I was not paying attention enough when I first looked at this. 

The problem (or good thing depending on your perspective) about hotplugable drives is that they are controlled by hal because it is impossible to guarantee that a certain usb drive will be allocated the same device everytime. 

For example, you have a camera and an external harddrive, none of which are plugged in all the time.

On monday you plug in your camera which is assigned to /dev/sda. You then plug in your external harddrive which is assigned to /dev/sdb. You do your stuff and then unmount and unplug them.

On tuesday you plug in your external harddrive. This time, as there are no other USB devices plugged in, it is assiged to /dev/sda, not /dev/sdb.

You can use fdi files to modify hal's behaviour e.g. I use it to set change the mount point, set permissions (using fstab parameters) and a system wide icon for our camera, by adding the following file with the following contents:

/etc/hal/fdi/policy/95userpolicy/60-Fuji-F10.fdi

```

<?xml version="1.0" encoding="ISO-8859-1"?> <!-- -*- SGML -*- --> 
<deviceinfo version="0.2">
 <device>
  <match key="info.category" string="volume">
   <match key="@info.parent:@info.parent:@info.parent:@info.parent:usb.vendor_id" int="0x04cb">
    <match key="@info.parent:@info.parent:@info.parent:@info.parent:usb.product_id" int="0x0177">
     <merge key="volume.policy.desired_mount_point" type="string">Fuji F10</merge>
     <merge key="volume.label" type="string">Fuji F10</merge>
     <merge key="volume.policy.mount_option.gid=users" type="bool">true</merge>
     <merge key="volume.policy.mount_option.uid=a_user" type="bool">true</merge>
     <merge key="volume.policy.mount_option.umask=007" type="bool">true</merge>
    </match>
   </match>
  </match>

  <match key="info.category" string="storage">
   <match key="@info.parent:@info.parent:@info.parent:usb.vendor_id" int="0x04cb">
    <match key="@info.parent:@info.parent:@info.parent:usb.product_id" int="0x0177">
     <merge key="storage.icon.volume" type="string">/usr/local/share/pixmaps/Fuji-F10-48x48.png</merge>
    </match>
   </match>
  </match>
 </device>
</deviceinfo>

```

I also use the below to set the mount point of my external drive I use to backup media:

/etc/hal/fdi/policy/95userpolicy/70-media-backup.fdi

```

<?xml version="1.0" encoding="ISO-8859-1"?> <!-- -*- SGML -*- --> 
<deviceinfo version="0.2">
  <device>
   <match key="block.is_volume" bool="true">
    <match key="@info.parent:@storage.physical_device:usb.vendor_id" int="1037">
     <match key="@info.parent:@storage.physical_device:usb.product_id" int="0x6204">
      <merge key="volume.policy.desired_mount_point" type="string">MediaBackup</merge>
      <merge key="volume.label" type="string">MediaBackup</merge>
     </match>
    </match>
   </match>
  </device>
</deviceinfo>

```

The best place to start is to open Device Manager (sorry, I am a bit of a command line person and cannot remember exactly where it is in the menus) and unplug (unmounting the partitions first!) and replug the external drive while observing what happens. lshal is good for dumping all the device information visible to the hal daemon to the command line.

As your aim appears to be to change the mount points of the partitions on your external drive we can start with the above as a basis. 

The difference is that I only have one volume (i.e. partition) on my external drive, so I can easily use the usb.vendor_id and and usb.product_id to uniquely identify the volume (unless I get another drive with the same vendor and product ids). You will need to use something else.

The volumes may have a volume.uuid parameter - check in device manager. If they all have unique uuids, you may be able to use the following:

/etc/hal/fdi/policy/95userpolicy/70-my-external-drive.fdi

```

<?xml version="1.0" encoding="ISO-8859-1"?> <!-- -*- SGML -*- --> 
<deviceinfo version="0.2">
  <device>
   <match key="block.is_volume" bool="true">
    <match key="volume.uuid" string="[uuid of ntfs volume]">
     <merge key="volume.policy.desired_mount_point" type="string">USB_NTFS</merge>
     <merge key="volume.label" type="string">USB_NTFS</merge>
    </match>
    <match key="volume.uuid" string="[uuid of ext3 volume]">
     <merge key="volume.policy.desired_mount_point" type="string">USB_ext3</merge>
     <merge key="volume.label" type="string">USB_ext3</merge>
    </match>
    <match key="volume.uuid" string="[uuid of FAT volume]">
     <merge key="volume.policy.desired_mount_point" type="string">USB_FAT</merge>
     <merge key="volume.label" type="string">USB_FAT</merge>
    </match>
   </match>
  </device>
</deviceinfo>

```

If not, you have to look for something that is persistent (i.e. does not change) and unique to each of the volumes and match against it instead - again use Device Manager for this.

Please do not hesitate to ask further questions - hal is confusing at first, but very powerful and easy once you get used to it.

---

### Post by KillrBuckeye on 2006-07-27
Wow thanks for the info.  I actually sorted out my boot-time problem, but now my problem lies with the device allocations that you mentioned.  Sometimes the drive is assigned /dev/sda, while other times it is assigned as /dev/sdb.  So far, it has been suggested to use 3 different methods to solve the problem:

1) Assign labels to each of the volumes, and simply refer to these volume labels instead of the device names in the fstab file.

2) Use "udev" rules as in this link:  [http://reactivated.net/writing_udev_rules.html]("http://reactivated.net/writing_udev_rules.html")

3) Use fdi files to modify hal's behaviour according to your previous post.

Being a Linux n00b, I'm not aware of the advantages and disadvantages of each method.  If it works, it seems like the volume labeling method would be easiest.  Do you know of a reason why it wouldn't work or wouldn't be desirable?  Thanks again for your help.

---

### Post by simonn on 2006-07-27
> **KillrBuckeye said:**
> Do you know of a reason why it wouldn't work or wouldn't be desirable?

No be honest it is probably horses for courses - I have never used the labelling method. I learned all the hal stuff when I was using Fedora. FC4 used fstab-sync to dynamically modify fstab so you needed to play with hal to change mount points.

Are you able to unmount/eject the drive if you use the fstab label method?

I suppose that one advantage with using hal is that you can do other stuff like set system wide icons and as it works at a higher level there is probably less chance of interfering with what Ubuntu expects.

---

### Post by KillrBuckeye on 2006-07-28
The volume labeling method worked for me, but I had to give up on using it in conjunction with fstab.  Once all the volumes were labeled appropriately, the automounter created directories in '/media' corresponding to each of the labels, which is exactly what I wanted.  All I had to do was change ownership and permissions on the directories, and I was set.  For some reason if I kept the fstab entries, it seemed to conflict with the automounter and I was getting duplicate mounts and other weird problems.  Thanks for your help.

---

### Post by shemonskizzle on 2006-07-29
Hi, I am attempting to make a fdi file as mentioned above, but it doesn't seem to be working. I don't have fstab-sync because it doesn't seem to ship with Ubuntu. Did you need to install fstab-sync in order to get your fdi file working? Or is there some other program that modifies the fstab file?

Thanks.

---

