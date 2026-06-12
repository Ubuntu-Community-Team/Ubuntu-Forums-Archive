---
title: "Raid + ntfs"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by UAnovice on 2009-09-09
Hello,
it's a RAID thing again propably. Installed from alternate CD (ubuntu 9.04), dual boot ok (vista home premium and ubuntu), both running fine.
UBUNTU does not find the ntfs partions however. Also due to RAID?
Any suggestions?
thanks

---

### Post by falconindy on 2009-09-09
If it's a hardware RAID, then you might be missing a driver. If it's software, you're prolly SOL.

---

### Post by UAnovice on 2009-09-09
I don't know what SOL is.
The alternate installerdid ok, selected the largest free partition and went ahead.
It's a dell XPS 720 , with an nVidia GForce raid controller
(says the windows device manager)
where do I go from here?

---

### Post by ronparent on 2009-09-09
If the ntfs is on a raid, it may be mounted by linking the symbolic link for the partition located in /dev/mapper to a filesystem location. This may be done either with a mount command or automatically during boot with a line in /etc/fstab creating the link.

OK, now to get down to brass tacks. List your sysbolic links with the terminal command **ls /dev/mapper**. You can also use the terminal command **blkid** which will also include your symbolic links plus a bit more information about the partitions. This will make it easier to identify the specific partition(s) you want to mount. The symbolic links themselves appear as one randomly asigned name designating the entire raid array and the same name ended with a number designating each individual mountable partition. The mount command is written in a terminal in the form **mount <syboliclink1> /target/<windrive>**. You have to create the **/target/<windrive>** as the mount point prior to trying a mount command of this form. Substitute whatever name you want for <windrive>. And it can be created at another location if you please (ie /media, /WinXPfiles, etc.). I haven't gone into mount options because in their absence the default options are used and this has generally worked fine for me.

For the same drive to mount automatically on boot you need to enter a line in /etc/fstab of the same form.  Just mimic the existing lines and options for partitions already being mounted in fstab. You have to edit /etc/fstab as an adminstrator (ie in a terminal write **sudo gedit /etc/fstab**, edit, and save).

This was a lot, fast. If you have any questions post them here. Good luck.

---

### Post by UAnovice on 2009-09-09
I'm a bit scared. This is what I get
mw@ubuntu:~$ ls /dev/mapper
control          nvidia_hdcaijac1  nvidia_hdcaijac3  nvidia_hdcaijac6
nvidia_hdcaijac  nvidia_hdcaijac2  nvidia_hdcaijac5  nvidia_hdcaijac7
mw@ubuntu:~$ blkid
/dev/mapper/nvidia_hdcaijac1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-021C" TYPE="vfat" 
/dev/mapper/nvidia_hdcaijac2: UUID="4EDA2FA2DA2F84F5" LABEL="New Volume" TYPE="ntfs" 
/dev/mapper/nvidia_hdcaijac3: UUID="5A36C6DC36C6B7F1" LABEL="VISTA" TYPE="ntfs" 
/dev/mapper/nvidia_hdcaijac5: UUID="86D256DBD256CF55" LABEL="Data disk" TYPE="ntfs" 
/dev/mapper/nvidia_hdcaijac6: UUID="ce2b1037-b5e0-495b-9b98-8ec83355b7cc" TYPE="ext3" 
/dev/mapper/nvidia_hdcaijac7: UUID="9d3bbbf4-d7fc-4661-b1ac-2c988580f120" TYPE="swap" 
and this is fstab (but I commented out intended changes)
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/nvidia_hdcaijac6 during installation
UUID=ce2b1037-b5e0-495b-9b98-8ec83355b7cc /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/mapper/nvidia_hdcaijac7 during installation
UUID=9d3bbbf4-d7fc-4661-b1ac-2c988580f120 none            swap    sw              0       0
#vista
#UUID="5A36C6DC36C6B7F1" vista
#data
#UUID="86D256DBD256CF55" data

/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
you think I'm ok?
I created two folders in /media (vista and data)

---

### Post by ronparent on 2009-09-09
Your doing great so far. You first have to create a mount point. For instance, you could first create the mount point: **md /Windrives/Datadisk**

To manually mount, in a terminal you would write: **mount /dev/mapper/nvidia_hdcaijac5 /Windrives/Datadisk** 

At this point you can read and write to windows partition Data disk. There are mounting options you could add but I have found that the unstated defaults have worked for me.

To mount from fstab you would add the lines:

[B]#data was /dev/mapper/nvidia_hdcaijac5 
/dev/mapper/nvidia_hdcaijac5 /Windrives/Data ntfs relatime,errors=remount-ro 0 1 [/B]

Translation, you would now at boot be mounting the file system linked to **/dev/mapper/nvidia_hdcaijac5** to the filesystem location you created for the purpose **/Windrives/Data**. The remainder of the line are the mounting defaults I copied monkey see, monkey do from the other mounting instructions in fstab. Don't worry abount doing it wrong. If you don't get it right it will merely not mount and you won't be able to see it in nautilus. The worse that is likely to happen in this instance is that the computer will make you do it over and over again until you get it exactly right. Greaty teacher that. If youwant you could check **man mount** to checkout the mounting options. Have fun and keep posting if you need more help.

---

### Post by UAnovice on 2009-09-10
works fine, 2 icons were added to my desktop on startup, one for each volume
thanks, your help was really to the point

---

### Post by ronparent on 2009-09-10
I initially had to struggle myself with this exact issue. Glad it worked out.

---

