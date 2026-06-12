---
title: "Hard Drive Formatting issues."
date: 2015-01-20
forum: Hardware
---

### Post by rick_ratliff2 on 2015-01-20
Okay, so, im running Trusty Tahr, the computor is a Hp Pav. Dm3 1039-wm( just covering the bases). The harddrive i'm trying to format is actually, the drive for the computor, so that i can install Trusty on it clean. I'm using a harddrive enclosure, ad it has worked for numerous other jubs. When I use the Disk utility to delete a partition, it reads 

 Error creating file system: Command-line `mkntfs -f -F -L "Name-Goes-Here" "/dev/sdb1"' exited with non-zero exit status 1:
stdout: `Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
'
stderr: `Error writing to /dev/sdb1: Input/output error
Error writing non-resident attribute value.
add_attr_sd failed: Input/output error
Couldn't create root directory: Input/output error
Failed to fsync device /dev/sdb1: Input/output error
Warning: Could not close /dev/sdb1: Input/output error
' (udisks-error-quark, 0)

When i try to mount it, it reads 

Error mounting /dev/sdb4 at /media/ubuntu/(Drivename): Command-line `mount -t "vfat" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush" "/dev/sdb4" "/media/ubuntu/(Drivename)"' exited with non-zero exit status 32: mount: /dev/sdb4: can't read superblock

Please, does anyone know how to help? My goal is to format the disk, and install ubuntu. I have tried to just install ubuntu using the launcher, but gives me an error message.

---

### Post by weatherman2 on 2015-01-20
Edit: OK, I see you were really trying to delete a partition.  If disk utility does not work, you can try Gparted.

If you want to erase the entire disk - this will erase ALL partitions including any HP recovery partitions for Windows, so make sure this is really what you wish to do! - at last resort you could issue this command:

```
sudo dd if=/dev/zero of=/dev/sdb bs=2048 count=8
```

Assuming /dev/sdb is your HP hard drive - if not, replace it with the correct device ID.  Be CAREFUL with the dd command or you could erase the wrong thing!

Then you may need to create a partition table - either Gparted or Disk Utility can do this - before the installation.

---

### Post by rick_ratliff2 on 2015-01-23
Thank you fr the prompt response, sorry I wasn't here to respond. I did as you said, and all i got was 

(Code)

8+0 Records in
8+0 records out
16284 bytes (16 kB) copied, 0.449833 s, 36.4 kB/s

(/code) 

and it did nothing. I rebooted, did multiple other things, but got the exact same errors, and the disk utility still says it's partitioned... 
It's probably my error, but i have no idea where i went wrong.

---

### Post by weatherman2 on 2015-01-24
You have to make sure /dev/sdb is your actual disk device.  if not, the dd command will do nothing.

---

### Post by rick_ratliff2 on 2015-01-24
It's drive /dev/sda, and ive been putting that in. It's still doing zip. I've tried to do it on two separate computers now, and i'm still bashing my head against a wall. It won't mount anything but one of the partitions(and that gets errors and doesn't actually mount too), does that hold any weight?

edit: the problem is always and 'input/output' error. seemed obvious, but hey, i dont know whats important info.

---

### Post by weatherman2 on 2015-01-24
Check the drive's S.M.A.R.T. status with GSmartControl (you'll have to install it probably).  Run the short test there (takes about 2 minutes) and make sure the drive is actually good.

---

### Post by rick_ratliff2 on 2015-01-24
Thanks for the continued help weatherman. Um it's labeling it as "unknown model" and whenever i try to scan it, it returns an unknown error occurred.

---

### Post by weatherman2 on 2015-01-24
If connected by USB, sometimes SmartMonTools (which GSmartControl uses) has trouble accessing a USB drive.  In that case, try adding the options "-d sat" and/or "-T permissive" (without the quotes) as options for the smartctl command.  There's a place to add them within GSmartControl. You can also run the smartctl command directly in a terminal but it's less friendly to use it that way.

---

### Post by rick_ratliff2 on 2015-01-24
It's just telling me the same old thing... hang on, No identify device structure detected... well dang. no clue what that means.

---

### Post by weatherman2 on 2015-01-24
Are you planning to use this hard drive as an internal drive in a computer, or are you hoping to use it as an external hard drive and install Ubuntu on it?

If you are using the USB adapter just for preparation, I'd install the drive back in the original computer and try using a live boot USB to boot Ubuntu and try formatting there.  I suspect there is some incompatibility between your USB adapter and Ubuntu and/or the drive and the USB adapter.

---

### Post by rick_ratliff2 on 2015-01-24
I'm trying to use it as an internal drive. I've been doing that, taking it out and putting it back in, and out and in, ect. thanks for all your help weatherman, but i think its just impossible right now. Unless you have anything else that you think'll work?

---

### Post by rick_ratliff2 on 2015-01-24
I've been mixing and matching in and out, over and over to get this... and i think we've hit an impasse. Thank you for sticking with me here weatherman.  Maybe the drive is screwed, maybe its not. You got any last ideas?

---

### Post by weatherman2 on 2015-01-24
Last idea would be trying another drive. ;-)  Sorry, I have a pile of spare drives so it would be easy for me to do that, not for everyone...

---

### Post by rick_ratliff2 on 2015-01-24
Yep, only problem being compatibility... or is that a non-existent problem?

---

### Post by weatherman2 on 2015-01-24
Compatibility?  I've never had a hard drive compatibility issue with Ubuntu (with USB adapters?  Occasionally.).  If it's a typical SATA drive, it should work fine.

---

