---
title: "External Hard Drive Permissions"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by ninjapirate350 on 2007-04-22
I went out and bought a Seagate FreeAgent 250 GB Hard Drive today to back up all my files on and I'm having a little trouble.  I don't regret the purchase one bit.  On sale for $100 @ CompUSA today..  Very nice!:) 

Anyway, to get to the point...

I plugged it in and the icon shows up on my desktop and I can access the files already pre-loaded on it.  However, it will not allow me to move my files over to the new hard drive.  I get the error:  "You do not have permission to write to this folder."  So, I right clicked and opened up the properties and it says root has access to the folder.  Naturally, I went to the root terminal and tried to sudo move my files that way and still no dice.  It told me that I still do not have permission  It says
> root@philip-laptop:/home/philip# sudo mv /home/philip/Desktop/Documents /media/FreeAgent\ Drive
mv: cannot create symbolic link `/media/FreeAgent Drive/Documents': Read-only file system
root@philip-laptop:/home/philip# 

What do I need to do to be able to access this drive?  I have the NTFS Configuration tool installed and all that.  I know I must be missing something.  Help!

---

### Post by BoneKracker on 2007-04-22
You (using sudo, in the terminal) can create one or more directories on the device, then give yourself access to those directories:```

sudo mkdir /dev/foo/bar
```
(where "foo" is the device and "bar" is the directory you want to create)```
sudo chmod 770 /dev/foo/bar
```
If you don't know the device name, right-click on the icon on your desktop and select properties.  Then select the volume tab.  It should show something next to "Mount Point".  Make a note of that.  Then type this in the terninal (replacing /media/blah with whatever the mountpoint was):
```
sudo mount | grep /media/blah
```(It should come back with a line that tells starts with /dev/foo)
(the pipe symbol in between mount and grep is not a capital I, it is located above the Enter key.)

[/CODE](this makes it readable and writable only by the owner and the group, with no access for others)```
sudo chown root.backup /dev/foo/bar

```

Then just add yourself (and anybody else who should have access) to that group (you can use the user & groups administrative tool).

---

### Post by BoneKracker on 2007-04-22
I didn't really do that justice.

Here is what I'd do.

First, while the disk is still mounted, find out the devide name:
```
sudo mount | grep FreeAgent

```It will spit out a line starting with /dev/<something>; make a note of the /dev/<something>

Second, if you want to keep any of those files that are on it, copy them off.

Third, umount the device:
sudo umount /media/FreeAgent\ Drive

Fourth, delete that stupid mount point and replace it with something meaningful to you.
cd /media
sudo rmdir FreeAgent\ Drive
sudo mkdir backups

Fifth, partition the disk if needed:
e.g. create a partition for your backups and one for your family photographs
you can install gparted, which is a graphical tool that will make this easy, otherwise, you'll want to use fdisk or parted (they both have man pages.  Type man fdisk or man parted in the terminal).

Sixth, format the disk with a nice filesystem:
If you want to access the disk from a Windows system, then use the filesystem "vfat", otherwise, I recommend "ext3"
If you've got gparted, you can do it from there, otherwise, from the terminal it would be 
sudo mkfs.ext3 /dev/<something>  (where something will probably be like sda or sdc).

Seventh, create a new line for the drive in /etc/fstab to provide some mount options that establish the access controls you want (otherwise, the system will use some assumed controls set up in HAL or udev):
sudo nano /etc/fstab
```
/dev/sdc1              /media/backups  ext3            rw,user,noauto                  0       0
/dev/sdc2              /media/pictures   vfat             rw,user,noauto                  0       0

```
The device names, mount points, and filesystems will depend on your earlier choices)
Press ctrl-o to save and ctrl-x to exit.

Eighth, reboot the system.

You should now be able to manually mount the disk when and if you want and have access to it.  You can then create folders within those partitions as you see fit.  Also, read the man page for "mount" and look at the mount options for the filesystems you have chosen.  You can specify, for example, that only the owner of the partition can mount it (if you want to be the only person who can mount the backup partition).

---

