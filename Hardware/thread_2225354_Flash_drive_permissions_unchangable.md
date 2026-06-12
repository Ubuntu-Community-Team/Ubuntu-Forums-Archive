---
title: "Flash drive permissions unchangable"
date: 2014-05-21
forum: Hardware
---

### Post by LinuxUser666 on 2014-05-21
Hello Ubuntu community, I am running Ubuntu 13.10 Saucy with GNOME Shell and with Nautilus as my file manager. My problems occur whenever I plug in a USB flash drive. It mounts normally but I cannot write on it and in properties under permissions tab for owner it says root.
Then I tried ```
gksu nautilus
``` to open as root, now I can write on it but transfer speed is circa 200 kB/sec and even as root I cannot change permissions. 
Someone please help because I generally have that problem with every flash drive. Is it because they are formatted as FAT32? 

My regards, stay brutal.

---

### Post by sudodus on 2014-05-21
There are two independent problems.

1 - permissions
2 - writing speed
[HR][/HR]***1 - permissions***

The Windows file systems FAT32 and NTFS get their permissions and ownership when mounted and are the same for all files. The only way to change them is when you mount the partition. This is different from linux ext file systems.

One way to change the permissions is to add a line in the file **/etc/fstab** for the USB drive (identfy the drive with its UUID) and include the mount option **noauto**. Then, if you have permissions for the user id, you can mount it with the file browser.

Another way is to create a directory **/media/somename** or ***/mnt/somename*** (a name that suits you) and change ownership to your regular user id.

Then you can mount the USB drive there manually (use the real drive letter as found with ```
sudo parted -l
``` instead of x) with the following command

```
sudo mount /dev/sdx /media/somename
```

You can also use an ext file system, where you can change the partitions of files and directories. It is also good in this case to have read and write access to the main directory.

***2 - writing speed***

Often the writing speed is limited by the flash hardware of the pendrive, particularly when you write many small files. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
[Link to USB 3.0 Flash Drive Speed Tests]("http://usb.userbenchmark.com/") 
[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

Only if the writing speed is significantly lower in Ubuntu compared to Windows or other computers, you can suspect that something is wrong. I have seen cases, when writing to NTFS is slower than to FAT32 and ext file systems, but it should not be the case here, because you have FAT32 in the pendrive.

---

