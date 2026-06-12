---
title: "ntfs external hard drive wont mount"
date: 2010-02-17
forum: Hardware
---

### Post by jhuntington on 2010-02-17
[FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333]hello! i am currently using a sabrent 3.5   USB 2.0 to SATA/SATA II HDD enclosure and a
[/COLOR][/SIZE][/FONT][FONT=Arial, Helvetica, sans-serif][SIZE=2][COLOR=#333333]Seagate 1.5TB LP Serial ATA HD   5900/32MB/SATA-3G[/COLOR][/SIZE][/FONT] as an external hard drive.  when i plug the usb hard drive in it does not show up in the computer section.  occasionally when i use fdisk -l the hard drive will show up as /dev/sdb1 but then will immediately disappear the next time i run fdisk -l.   the same thing happens when i run the disk utility the drive will first show up but then will immediately disappear.  any help in resolving this issue would be greatly appreciated.

---

### Post by jhuntington on 2010-02-17
is there any additional information i should provide?

---

### Post by horgzter on 2010-02-17
I have some major problems also - 

I got one of the disks up and mounted automaticlly, while the outer I got a error message (cannot mount ....)

Used some info in this thread (last post) and this made me able to find them at least and use the stuff on the drives. 
[http://ubuntuforums.org/showthread.php?t=534729](http://ubuntuforums.org/showthread.php?t=534729)

But it does not seem like a good solution ?
Want to be able to mount them like normal in XP with correct volume names and all. 

I have tried running through chkdsk in XP just to make sure there were no errors on them. (tips on several threads with same issue.)

---

### Post by Crafty Kisses on 2010-02-17
First make sure you have the NTFS utilities installed, so if you don't you need to run the following commands and install these packages:
```
apt-get install ntfsprogs
```
I'd also like to see your fstab, you can view your fstab by running the following:
```
cat /etc/fstab
```
I would also suggest seeing if GParted sees the drive, if you don't have GParted, install it.

---

### Post by jhuntington on 2010-02-17
i have already installed the ntfs utilities. here are the results from my cat /etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=5ac8052a-6a0b-48fe-858c-08a7ffee04af /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d1eeffbf-d041-4f52-8092-6a8fc90c86c5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```i downloaded and installed gparted.  the drive does not show up in gparted.  i have plugged the drive into a windows machine and it reads just fine so i know the drive works and the partition is readable.

---

### Post by jhuntington on 2010-02-17
here is a screenshot of what shows up for the drive in the disk utility but then quickly disappears.

---

### Post by caglar sekmen on 2010-02-18
Some of the old ubuntu versions does not have ntfs-config so you can not install it. I tried ubuntu 9.10 and just clicked the two partitions and opened them. Here is the best demonstration.

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

I tried to open an another file in media such as externaldisk but couldnt open the hd. 
The error in detail was that the file was already mounted to the extarnaldisk ..

---

### Post by jhuntington on 2010-02-18
i am currently running ubuntu 10.04 because my new laptops graphic drivers were not supported with 9.10.  i tried mounting the hard drive with a 9.10 live cd and it worked just fine.  any ideas as to what could have been broken in 10.04? any ideas as to a workaround for this situation? its an asus u50f.

---

