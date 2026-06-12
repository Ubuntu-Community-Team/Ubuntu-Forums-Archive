---
title: "help please"
date: 2010-01-31
forum: Hardware
---

### Post by dasylencer1 on 2010-01-31
when i burn the ubuntu cd put it in my crashed laptop. click on try ubuntu without any changes to my computer.  I try to open up hard drive but it keeps on saying unable to mount location?  Can someone please help me fix this problem please.  It's saying that the volume is in use by another process. please reply asap. thanx

---

### Post by lisati on 2010-01-31
What have you tried so far?

---

### Post by CGZ1977 on 2010-02-01
lisati can you please help me with my problem? How to mount my HD while using the cd on my crashed laptop.....username cgz1977. Thanks

---

### Post by amsterdamharu on 2010-02-01
The partition you are trying to mount is an ntfs partition I assume. When the computer crashed windows did not write something to some file indicating it was done with the partition. This might be why linux does not want to mount it, same happens when you yank out a usb stick under windows and try to mount it under linux.

Can you try the following?:
Open a console and run the following commands:
```

sudo su
mkdir /media/sda1
mount -t ntfs /dev/sda1 /media/sda1

```

I assume there will be some error, can you allso post the output of the following command
```
sudo fdisk -l
```

---

### Post by dasylencer1 on 2010-02-02
when I typed sudo su in the command prompt it says sudo is not recognized as an internal or external command, operable program or batch file.  typed mkdir /media/sda1  it says the syntax of the command is incorrect.  typed mount -t ntfs /dev/sda1 /media/sda1 it says mount is not recognized as an internal or external command, operable program or batch file.  typed sudo fdisk -1 it says sudo is not recognized .....  was I suppose to type it in in the ubuntu? ok I typed all those commands except the sudo fdisk -1 and it opened up the sda1 hard drive on the lcation my computer. And I opened it and there are a whole bunch of files there. Am I suppose to open one of the files?   When I typed sudo fdisk -l in the terminal it poped up  Disk /dev/sda: 80.0 gb, 80026361856 bytes 255 heads, 63 sectors/tract, 9729 cylinders units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x0b6dd6a6     Device Boot   Start       End    Blocks    Id    System /dev/sda1            1       1274    10233373+  27    unknown /dev/sda2    *    1275       5519    34097962+   6     FAT16 /dev/sda3         5520       9729    33816825    7    HPSF/NTFS root@ubuntu:/home/ubuntu#   Please reply asap thanx.

---

### Post by amsterdamharu on 2010-02-02
You have lost me "not recognized as an internal or external command, operable program or  batch file" means that you typed the command in dos or windows but you say your laptop crashed and I assume you could not open windows.

"and it opened up the sda1 hard drive on the lcation my computer. And I  opened it and there are a whole bunch of files there. Am I suppose to  open one of the files?" means that you've mounted your harddisk from the ubuntu cd, that's what you wanted. Are you surprised there are files on the harddisk?

Since your disk mounted without any problems you can just click on it in filemanager and see whats on the disk.

If you want to repair windows I suggest you post what is wrong with windows (in a windows forum).

---

### Post by dasylencer1 on 2010-02-02
lol  sorry I don't know what I have to do.  I'm trying to use the ubuntu cd that I burned on my crashed laptop.  And I typed in all your commands and on the locations, my computer, the sda1 drive poped up while im using the ubuntu cd, not my windows.  I guess I'm trying to mount my hard drive to ubuntu but it keeps on saying unable to mount location instead of unable to mount volume. And I heard that ubuntu  is used to back up your hard drive. So I guess thats what I'm trying to do because yes, my windows can not open. thanx

---

### Post by amsterdamharu on 2010-02-02
There is no way the message you posted can come from ubuntu: "not recognized as an internal or external command, operable program or   **batch file**". Maybe the harddisk has a dos partition on it but there is nothing on the ubuntu cd that will give that output on any command.

sda1 is an unknown partition and sda2 is fat16, since sda3 is ntfs I think that makes it your windows partition (3 partitions on your harddisk). You can just click on these in the file browser in ubuntu:
places -> computer -> ...gb harddisk ... gb filesystem

If that gives you an error you can try to manually mount it. In ubuntu can you please start a terminal (applications -> accessories -> terminal
copy and paste the command lines under here in the terminal and copy and paste the output.

```
sudo su
mkdir /media/sda3
mount -t ntfs /dev/sda3 /media/sda3
```

---

### Post by dasylencer1 on 2010-02-02
lol sorry again, I didn't type that in ubuntu, it was  without ubuntu.  In ubuntu I can open gb filesysytem but not gb hard disk. And when I try to mount it manually with your commands , after i typed in all of it, another line pops up. &quot;root@ubuntu:/home/ubuntu#&quot;  or I maybe it says fuse: mount failed: Device or resource busy.  When I try to open gb hard disk acer, a message pops up saying &quot;unable to mount location&quot;.  DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending.   I have three things on my mycomputer in ubuntu.   gb hard disk acer,  gb hard disk data, and filesystem.   Thanx.

---

