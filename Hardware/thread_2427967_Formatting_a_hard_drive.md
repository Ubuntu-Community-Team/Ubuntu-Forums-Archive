---
title: "Formatting a hard drive"
date: 2019-09-27
forum: Hardware
---

### Post by pipercub45 on 2019-09-27
I have 18.04 and I am trying to format a hard drive.  I type "sudo lshw-Cdisk.  Enter the pass word and get the logical name.  I click "system" from I guess is the Icon  at the bottom of the left hand corner.  I scroll down to "administration"  and look for "partition editor" or "GNOME partition editor".  I cannot find either one.  Where is it?  What am I dong wrong?

Thanks

---

### Post by Skaperen on 2019-09-27
how is this hard drive plugged?  do you know what name the hard drive has?

try this command and see if its name is in that output:  [COLOR=#0000cd][FONT=courier new]**cat /proc/partitions**[/FONT][/COLOR]

---

### Post by Dennis N on 2019-09-27
> **pipercub45 said:**
> I have 18.04 and I am trying to format a hard drive.  I type "sudo lshw-Cdisk.  Enter the pass word and get the logical name.  I click "system" from I guess is the Icon  at the bottom of the left hand corner.  I scroll down to "administration"  and look for "partition editor" or "GNOME partition editor".  I cannot find either one.  Where is it?  What am I dong wrong?

Thanks

Are you using Ubuntu? The Gnome partition editor is not installed by default. To install, start "Ubuntu Software". Search for **gparted** in the Ubuntu Software utility and install.

---

### Post by yancek on 2019-09-28
GParted is on the installation DVD/USB you used to install Ubuntu.  You don't indicate what you are trying to do, which partitions you want to change.  You can't use GParted on mounted partitions so usually using the Live DVD/USB is simpler as you won't be able to modify a running system.

---

### Post by TheFu on 2019-09-28
Don't confuse "a drive" with "partitions."

You should not format a drive.
You should format partitions.

Use gparted.

**sudo -H gparted** is the correct command.  Knowing nothing, but assuming the disk is NOT the disk used with the OS and can be completely wiped, I would:
[LIST=1]
[*]Run gparted
[*]Select the correct disk (upper right-hand picker)
[*]Create a new GPT partition table
[*]Create 1-100 partitions, sized for my needs.
[*]Pick 1 of the partitions, right click on it, and choose the format + file system I want
[*]Click "Apply" and wait as everything is done.
[/LIST]
This will destroy any data on the disk already. If you want to keep anything, back it up first.
If the disk has any OS or boot partitions on it that you need, don't do this.
If you aren't 100% certain that you've selected the correct disk, don't do this.  It is very easy to forget or pick the wrong disk and destroy your OS.

---

### Post by SeijiSensei on 2019-09-28
I format filesystems from the command prompt.

```
sudo mkfs -t ext4 /dev/sdb1
```

Other common types are "ntfs" and "vfat".

Quick and easy if you know what partition you want to format. I still use the hoary fdisk to create partitions.

Easiest way to get an inventory of available partitions and devices is to use "sudo blkid".

---

### Post by pipercub45 on 2019-09-28
Thank you for all the responses!  Wow!

I went with TheFu and it worked just fine.

---

