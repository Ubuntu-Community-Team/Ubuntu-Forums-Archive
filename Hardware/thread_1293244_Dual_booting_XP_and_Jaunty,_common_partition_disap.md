---
title: "Dual booting XP and Jaunty, common partition disappeared under Ubuntu."
date: 2009-10-16
forum: Hardware
---

### Post by Vague Rant on 2009-10-16
Hey guys. A couple of weeks ago I installed Ubuntu Netbook Remix on my Acer Aspire One. Originally my drive had a small recovery partition (primary) and a large partition for XP (primary, boot); I cannibalised some space from the XP install for Ubuntu (turning it into an extended partition with logical partitions for Ubuntu itself, /home, and swap), but later realised I needed a common partition for all my media, as I'm fond of hibernating my system and that was curtailing my options.

So I copied all of my media onto an external HD and added a fourth partition (NTFS) under the extended partition, then copied all my stuff from the external HD onto the common partition. That was yesterday, and while everything was working fine then (I played some music, watched some videos, etc.), this morning the common partition has disappeared. It doesn't show up in Nautilus at all and is not present under /media (presumably it isn't mounted), however I can see it under gparted, and it does not list any errors with the partition, etc. On a right click, "unmount" is present but greyed out.

When running Windows, the partition appears and functions just fine. I ran a chkdsk /f on it just in case, but no change. I've tried both hibernating and shutting down Windows in case that was somehow causing the problem, but again, no change. The partition is obviously working to some degree, since it appears in gparted and works fine under Windows, so this problem is solely on the Ubuntu side. I tried to manually mount sda8 (the partition) to /media/Common (its label is Common, and it usually mounts to this position), but it just reported "fuse: failed to access mountpoint /media/Common: No such file or directory". Possibly I'm just doing the mount wrong, not super knowledgeable about Linux. 

I don't really understand how things went from working fine to having the drive not appear at all, but hopefully someone will have an idea. Thanks for any help.

EDIT: I think I might have things working again as they should. As I suspected, I was failing at doing the mount, I had to create the /media/Common directory before I could mount the partition to it. Once I did that I was able to mount the drive and it appears to remain stable across OSes and hibernates. The only thing I haven't checked yet is whether the drive will still appear after a full reboot (i.e. not hibernate), as I'm in the middle of something, so if that's a problem I will report back about it, otherwise things seem to be OK. Still no idea what caused the problem, so please feel free to reply back if you have any thoughts as to what may have happened.

---

### Post by hal10000 on 2009-10-16
> mountpoint /media/Common: No such file or directory
This tell you that you don't hsve the directory to mount yout ntfs partition to.
So first create the mountpoint:
```
sudo mkdir /media/Common
```
an then mount it manually with
```
sudo mount -tntfs /dev/sda8 /media/Common
```

If you're not sure about the correct entry in your /etc/fstab, then post it here

---

### Post by Vague Rant on 2009-10-17
That does indeed work for mounting the partition, but as I suspected, it disappears again on boot. It used to be that even my unmounted partitions would appear under Places (in Nautilus and in the GNOME menu) and I just had to click on them to mount them. Not sure what I did to lose that feature. Hopefully all of this will be mooted when I upgrade to karmic; I haven't been running jaunty long but I've had enough problems besides this that it's probably worth a fresh install, and hopefully karmic will play a little more friendly with my hardware. In the meantime, though, it'd be nice to have mounting drives back to normal. I notice I get a few errors when running nautilus from the terminal, maybe they could be of some help:

```
(nautilus:4869): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:4869): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/gvfs/gvfs-gdu-volume-monitor received signal 11

(nautilus:4869): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GPhoto2VolumeMonitor: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 127

** (nautilus:4869): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: unknown format for key 'videos/usershare_acl' as it contains 'Everyone:R,'.  Assuming that the share is read-only
```

---

### Post by hal10000 on 2009-10-17
> That does indeed work for mounting the partition, but as I suspected, it disappears again on boot.

Well, then everything is fine but your /etc/fstab file.
Post the output of 
```
cat /etc/fstab
```
so we can help you to make the correct entries here

---

### Post by Vague Rant on 2009-10-17
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=36f7433b-52be-468b-ae33-2301dacd6f9d /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=68ec2fdd-0275-41c2-90bc-a3f6edbd85f8 /home           ext4    relatime        0       2
# swap was on /dev/sda7 during installation
UUID=c613d15e-e1a2-48ee-ae28-5c7206a97208 none            swap    sw              0       0

```

There's what's in my fstab, appreciate the rapid support.

---

### Post by hal10000 on 2009-10-17
First we have to find out the UUID for your /dev/sda8 partition, so run:
```
blkid
```
find the line for your /dev/sda8, you can see the UUID

Then open the /etc/fstab file as root:
```
 gksudo gedit /etc/fstab
```

And make a new entry on the last line of the file:
```
# /dev/sda8 , this is just a comment line, no code
UUID=XXXXXXXXXXXXXXX /media/Common ntfs    defaults,umask=007,gid=46 0       1

```Instead XXXXXXXX fill in the UUID you have found with the blkid command, but without the quotes. It is very important here to take care of the syntax, so write everything here exactly as i stated, including spaces and tabs. Save the file and exit gedit.

Good luck

---

