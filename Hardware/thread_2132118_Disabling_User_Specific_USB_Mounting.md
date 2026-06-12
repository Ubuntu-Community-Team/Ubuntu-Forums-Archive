---
title: "Disabling User Specific USB Mounting"
date: 2013-04-03
forum: Hardware
---

### Post by gerowen on 2013-04-03
So I did a search of the forums and didn't notice anything regarding this particular issue on the first page or so, so here's my issue.

When you plug in a USB device, that device is, by default, mounted to a location like /media/username/devicelabel .  So my 1 TB external gets mounted to /media/marcus/Storage .  However, I share this computer with my wife, and we both work, so throughout the day I may come home, and she has been on the computer, which means the external is mounted to /media/ash/Storage, and if I want to access it on my name, I have to sudo umount it then remount it.  I've tried adding this device to /etc/fstab and it doesn't mount at boot, and I tried using the Ubuntu GUI method to change its auto mount features so that it mounts to /mnt/Storage at bootup so we will both have access to it without it mattering which person logs in first.  The device mounts just fine if I leave the "Automatic mount options" button toggled to "On", which makes it mount to the user specific locations.  However, if I try changing the options to send it to a different folder, which I've already created by the way, I get these error messages. (See attached screenshots)  I've also tried changing the value of "Identify As" to all of the available options, including the UUID, and none of them seem to make a difference.

OS: Ubuntu Linux 12.10 64 bit
Hard Drive File system: ext4

*Note: Click images to see larger versions*
[ATTACH=CONFIG]240923[/ATTACH][ATTACH=CONFIG]240922[/ATTACH]

---

### Post by conradin on 2013-04-04
You do not have to unmount the drive, to mount it else where. This is because the mount point(s) are all common to the /dev/<device> to which whatever mounted folder refers to. (athough, perhaps you could end up with a race condition, but usually that will post errors unlike the ones you have) the image mount1.png looks like what happens when mount doesnt know how to process the filesystem handed to it. 
you may need to specify the Filesystem type (-t option) like this:
```

mount -t ntfs /dev/sdb1 /mnt/ntfs 

```

can you post your fstab? 
what type of FileSystem is this?

---

### Post by gerowen on 2013-04-04
I fixed it just a few minutes ago by just adding a mount command to /etc/rc.local 

```
mount /dev/sdb1 /mnt/Storage
```

The external drive is formatted in EXT4.  It now mounts at boot and is accessible by both users without having to do anything special, and we've got a bookmark for it in Nautilus so all we have to do is right click the folder icon on the Unity panel and there's a link directly to it.

---

