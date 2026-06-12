---
title: "Assigning Pre-partitioned Partitions during Install?"
date: 2005-01-21
forum: Installation &amp; Upgrades
---

### Post by drbista on 2005-01-21
I am trying to install the Ubuntu in the amd64. But I am surprised how could I mount different directories in different partitions during install (partition disks)?

I want to assign like this, particularly for Ubuntu64:

/dev/hda1 -> /boot
/dev/hda7 -> /
/dev/hdb10 -> /var
/dev/hdb13 -> /usr


And the followings as shareable partitions with FC1:

/dev/hda5 -> /swap
/dev/hdb11 -> /swap
/dev/hdb6 -> /tmp
/dev/hdb16 -> /home (contains a world of data from FC1)

Now I am surprised how to go about assigning them at the very boot installation from CD?

I reached upto 'Partitiion Disks' and stuck. I tried also with the 'expert' mode but it just whined me around the Debian mirror state as it kept on reporting me that [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) is a wrong archive. So I quit.

In the meantime, I also tried to post the same at #ubuntu (and am still there), but none seems helpful. 

Help solicited so that I could install Ubuntu64 without damaging my existing data.  :confused: 

Thanking you in advance for your time and cooperation

---

### Post by Buffalo Soldier on 2005-01-21
At the "Partitioning Disk" page. You're asked,
```
Partitioning method:
- Erase entire disk
- Manually edit partition table
```
choose "Manually edit partition table". 

Then you are give all the list of partitions you have on your disk. Then you highlight the partition that you want to mount, press ENTER, then highlight MOUNT, press ENTER, then type in where you want to mount that partition.

Example,

highlight "/dev/hda1", press ENTER
highlight MOUNT, press ENTER
type in "/boot"

---

### Post by drbista on 2005-01-21
Sorry that is not what I intend to say. It is like telling to do "format c:" in Windows and is windows way.

However I found the way. In the "Partition Disks" stage, select the concerned partition you want to mount. Then click on format disk and at the mount point there are several options, you just mount it. Simple!

Now I proceed ahead!

---

