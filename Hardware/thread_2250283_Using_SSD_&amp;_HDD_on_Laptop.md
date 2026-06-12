---
title: "Using SSD &amp; HDD on Laptop"
date: 2014-10-27
forum: Hardware
---

### Post by bunchy on 2014-10-27
Hi

I've installed Ubuntu 14.04 on my new Acer V7 Laptop.
It has both SSD (24GB) & an HDD (500GB).   I installed it on the SSD and wanted to keep the HDD as a storage for big files. Currently, Ubuntu wont let me access the HDD at all. How can i fix this without re-installing the whole thing?
If this is not possible, how do i manually make this happen during installation?
I am somewhat familiar with Gparted. please see below for setup with auto-installation:

Thank You!

sda1 extended - 465.76GB  boot
sda5 ext4 465.76 GB

sdb1 ext4  /mount point   14.48GB
sdb2 extended - 7.88GB
sdb5  linux swap 7.88GB

---

### Post by weatherman2 on 2014-10-27
Your HDD looks to have a big ext4 partition on it - taking the whole drive - on /dev/sda5 .  You're saying you can't mount it?  In a terminal for example can you do this:

```
sudo mount /dev/sda5 /mnt
```

?

(Then in the filesystem navigate to the directly /mnt ).

To make that happen automatically at each boot, add a line to the file /etc/fstab (but pick some other mount point, probably not "/mnt").

To allow writing files to the partition, try this in a terminal:

```
sudo chown -R yourname:yourname /mnt/
```

(replace "yourname" with  your login/username)

---

### Post by bunchy on 2014-11-03
Thanks weatherman2

Would you put both commands, mnt & chown in the fstab file?

---

### Post by weatherman2 on 2014-11-03
No, the /etc/fstab file is a descriptive file explaining to the operating system what to mount, where.

The two commands I gave you are one-time commands to run in a terminal window.

The chown command needs to be run only once and never again.  It changes the ownership of the files to be you (and not the administrator account) so you can read/write files to that partition.

The mount command I gave you could be run only when you want to mount a partition "on-the-fly" instead of having it mounted automatically (or perhaps because there is no automatic mount for it).  It is not required to run this command - it's only to check out once to see if you can actually mount this partition anywhere.

You already have an /etc/fstab file.  Take a look at it (though it may make no sense to you yet).  It contains description lines to explain to the operating system where to mount other partitions (on the SSD).

To mount the HDD partition automatically, you need to add one line to this file.  For example, you could add this line:

```

/dev/sda5 /home/YOURUSERNAME/Data ext4 rw,errors=remount-ro 0 0

```

(replace YOURUSERNAME with whatever your name is.)

But you need to make a mount directory first.  Run this command one time to create the Data directory:

```

sudo mkdir /home/YOURUSERNAME/Data

```

(You can make the mount directory anywhere you want - replace "/home/YOURUSERNAME/Data" with something else if you like.)

To the bottom of your fstab file.  You need to edit it as "root" (sudo).  In a terminal type this to open the gedit editor:

```
sudo gedit /etc/fstab
```

(give the admin password if asked)

A while editor window will pop up - add the line I gave you (or one similar if you want to change it) at the end of the file.   Save the changes and exit.

Now to mount the partition at its new mount point, in a terminal type:

```

sudo mount -a

```

This command may confuse you at first; it will mount everything in your /etc/fstab file, and if all is mounted successfully (or already mounted), it returns no output.  Only if there's an error (partition couldn't be found or something) would it return any output, like an error or warning.

You don't have to run "mount -a" every time you boot - it gets run automatically from now on at each boot.  But you can run it this once to make sure your HDD partition was mounted under your home folder in "Data" (if you follow the example I gave you).

---

