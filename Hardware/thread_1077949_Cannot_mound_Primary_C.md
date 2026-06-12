---
title: "Cannot mound Primary C"
date: 2009-02-22
forum: Hardware
---

### Post by EdSquareCat on 2009-02-22
Whoops the title should say mount :)

I've just upgraded from Ubuntu 8.04 to Ubuntu 8.10.  When I try to mount Primary C to access my Windows files, it gives me an error: 
```

Cannot mount volume.

Unable to mount the volume 'PRIMARY C'.

```

...and then this error:
```

Unable to mount location

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. 
Possible causes include: the remote application did not send a reply, the 
message bus security policy blocked the reply, the reply timeout expired, 
or the network connection was broken.

```

---

### Post by cariboo on 2009-02-22
Linux does not use drive letters to mount hard drives, and the only to use the partition label is to delimit the space in the name eg:

```
Primary\C
```

To find what the device label of the hard drive, open a Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

Enter your password when asked. It will not be echoed back when you type it.

If your Primary C partition is the first partition on the first hard drive the device label it will be something like:

```
/dev/sda1
```

Jim

---

### Post by EdSquareCat on 2009-02-23
The output:
```

~$ fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       27206   218492032+   7  HPFS/NTFS
/dev/sda3           27207       30394    25607610    f  W95 Ext'd (LBA)
/dev/sda5           27207       30394    25607578+  83  Linux

```

When I try to access /dev/sda2, it tells me it doesn't exist.

---

### Post by cariboo on 2009-02-23
Can you mount the partition manually?

```
sudo mount -t ntfs-3g /dev/sda2 /mnt
```

Jim

---

### Post by EdSquareCat on 2009-02-24
```

 ~$sudo mount -t ntfs-3g /dev/sda2 /mnt

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /mnt -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /mnt ntfs-3g force 0 0

```
Hmmm, its telling me that its in use, although I don't see how.  I can't even access my Windows (virus).  I have been able to access the partition from Ubuntu since it was infected; it was only after upgrading to 8.10 that this problem arose.

---

### Post by taurus on 2009-02-24
Looks like you didn't shut down your windows cleanly so you can't mount it in Ubuntu without using the force option.  You can fix that with ntfsfix.

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda2
sudo mkdir /media/sda2
sudo mount -t ntfs-3g /dev/sda2 /media/sda2
df -h
```

---

### Post by EdSquareCat on 2009-02-24
Thank you, that worked perfectly! I much appreciate the help.

---

