---
title: "Floppy mounting"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by Martian on 2006-06-13
vfat (only) floppy mounting

Update: see this post (below) for a solution:

[http://www.ubuntuforums.org/showthread.php?p=1944482#post1944482]("http://www.ubuntuforums.org/showthread.php?p=1944482#post1944482")

----

It takes nearly 2 minutes for my system to mount a floppy in Ubuntu.  Once mounted, the floppy works fine.  Unmounting is fine, as well.

Here are the messages that usually come up when mounting a floppy:
```
Jun 13 14:10:21 xyz kernel: [4299637.121000] attempt to access beyond end of device
Jun 13 14:10:21 xyz kernel: [4299637.121000] fd0: rw=0, want=2884, limit=2880
Jun 13 14:10:21 xyz kernel: [4299637.121000] UDF-fs: No VRS found
Jun 13 14:11:08 xyz kernel: [4299684.500000] attempt to access beyond end of device
Jun 13 14:11:08 xyz kernel: [4299684.500000] fd0: rw=0, want=2884, limit=2880
Jun 13 14:11:08 xyz kernel: [4299684.500000] UDF-fs: No VRS found
Jun 13 14:11:15 xyz kernel: [4299691.097000] Unable to identify CD-ROM format.
Jun 13 14:11:21 xyz kernel: [4299697.294000] Unable to identify CD-ROM format.
```

Sometimes I get these messages instead:
```
Jun 13 13:07:23 xyz kernel: [4295858.685000] UDF-fs: No VRS found
Jun 13 13:07:31 xyz kernel: [4295866.683000] UDF-fs: No VRS found
Jun 13 13:07:38 xyz kernel: [4295873.681000] Unable to identify CD-ROM format.
Jun 13 13:07:44 xyz kernel: [4295879.878000] Unable to identify CD-ROM format.
```

Thinking that it was taking so long because it was trying to determine what format the floppies are (they are vfat). I tried adding
```
/dev/fd0 /media/floppy vfat rw,user,noauto 0 0
```
to /etc/fstab.  And then remounting the filesystems using
```
sudo mount -a
```

However, when I then attempt to mount a floppy, an error box comes up:
```
Mount Error
Unable to mount the selected floppy drive.
mount: mount point /media/floppy does not exist
```
and that seems true enough: /mount/floppy doesn't appear until I (**without** the addition to /etc/fstab) mount the floppy.

Can anyone please help?

---

### Post by Martian on 2006-06-14
I reformated a floppy as FAT using Ubuntu (as opposed to Windows)--no change in mounting.

I then formated a floppy as ext2 using Ubuntu.  The floppy did mount faster, but there were plenty of messages:
```
Jun 14 18:02:08 xyz kernel: [4316345.901000] UDF-fs: No partition found (1)
Jun 14 18:02:21 xyz kernel: [4316359.094000] UDF-fs: No partition found (1)
Jun 14 18:02:27 xyz kernel: [4316365.001000] Unable to identify CD-ROM format.
Jun 14 18:02:33 xyz kernel: [4316370.986000] Unable to identify CD-ROM format.
Jun 14 18:02:34 xyz kernel: [4316371.688000] VFS: Can't find a valid FAT filesystem on dev fd0.
Jun 14 18:02:34 xyz kernel: [4316371.694000] VFS: Can't find a valid FAT filesystem on dev fd0.
Jun 14 18:02:34 xyz kernel: [4316371.723000] NTFS driver 2.1.25 [Flags: R/O MODULE].
Jun 14 18:02:34 xyz kernel: [4316371.779000] HFS+-fs: unable to find HFS+ superblock
Jun 14 18:02:34 xyz kernel: [4316371.785000] HFS+-fs: unable to find HFS+ superblock
Jun 14 18:02:34 xyz kernel: [4316371.810000] VFS: Can't find a HFS filesystem on dev fd0.
Jun 14 18:02:34 xyz kernel: [4316371.818000] VFS: Can't find a HFS filesystem on dev fd0.
```

---

### Post by Martian on 2006-06-17
While looking around the HAL Device Manager, I noticed the following key for "PC Floppy Drive": storage.policy.mount_filesystem.  This key's value is currently "auto".  Would changing this to "vfat" skip what appears to be a rather lengthy floppy disk format detection process?  If so, how (or where) should I go about changing this value (if it is safe to do so...)?

---

### Post by Martian on 2006-06-19
Solution:

In the terminal
```
sudo gedit /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi
```

In 10-storage-policy.fdi, under "<!-- floppy drives -->", I changed this
```
<merge key="storage.policy.mount_filesystem" type="string">auto</merge>
```
to this
```
<merge key="storage.policy.mount_filesystem" type="string">vfat</merge>
```

---

### Post by Martian on 2006-12-29
Just an update to my previous posts.  The 'solution' I've given seems to be a non-permanent one -- it seems as though /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi gets overwritten if HAL gets updated... :-k 

I searched out a way to make a more permanent 'override' of the defaults...... and here is what I ended up doing:

1) I created a directory called
```
30user
```
in
```
/usr/share/hal/fdi/policy/
```

2) In that directory (/usr/share/hal/fdi/policy/30user), I made a file called
```
90-floppy-policy.fdi
```
with the following contents
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- --> 
<deviceinfo version="0.2">
  <device>
      <!-- floppy drives -->
      <match key="storage.drive_type" string="floppy">
	<merge key="storage.policy.mount_filesystem" type="string">vfat</merge>
	<merge key="storage.policy.desired_mount_point" type="string">floppy</merge>
      </match>
  </device>
</deviceinfo>
```

3) I then restarted my computer.

---

