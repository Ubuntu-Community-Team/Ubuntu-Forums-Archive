---
title: "Allow user to write to fat32"
date: 2005-11-30
forum: General Help
---

### Post by Sudden on 2005-11-30
Hi
i'm running dualboot with windows xp and ubuntu. i've created a partion with fat32
and would like to both read and write to it as a normal user without using sudo.
How do i do that?

---

### Post by Edit on 2005-11-30
I think you can get software that enables you to write to FAT32 partitons via linux, but I'm not sure exactly what it's called or where it's from.

But to get your FAT32 drive readable by normal users, go:

```

sudo gedit /etc/fstab

```

Then change the fat32's mount line where it says 'defaults' to 'umask=0222'.

Save the file, reboot and you should have read access via a normal user.

-Edit

---

### Post by teaker1s on 2005-11-30
look [here]("http://ubuntuguide.org/")

---

### Post by Sudden on 2005-11-30
Okay now i can read that's on the fat32 partition
But still i need to be able to write to it.

---

### Post by teaker1s on 2005-11-30
manually

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000


to unmount 
sudo umount /media/windows/


automatic

#

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

# Append the following line at the end of file

/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

# Save the edited file (sample)
# Read How to remount /etc/fstab without rebooting?

---

### Post by aysiu on 2005-11-30
teaker1s has it down.
Only a few things to keep in mind:

1. The instructions assume your FAT32 partition is at /dev/hda1. To find out where it really is, type [i]sudo fdisk -l[/code] in the terminal.

2. To remount without rebooting, *sudo mount -a*

3. Rebooting is cleaner, especially if the partition is already mounted but with the wrong permissions.

---

