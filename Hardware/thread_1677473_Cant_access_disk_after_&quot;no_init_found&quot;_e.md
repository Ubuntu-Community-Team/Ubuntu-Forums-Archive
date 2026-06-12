---
title: "Cant access disk after &quot;no init found&quot; error"
date: 2011-01-28
forum: Hardware
---

### Post by perfecti0n on 2011-01-28
Hello!

I have a HP ProBook 6540b labtop and while doing a system resume ubuntu froye at splash screen with the dots. So I powered it off and when starting it again the error showed up

```
mount: mounting /dev/disk/by-uuid/***************************** on /root
failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs)
```Anyway after some googling for the solution i found a tip to do this

sudo fdisk -l

where i got the partition where linux is installed 
and then

sudo fsck /dev/sda1

however, doing this...the terminal returns

   ```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59272   476097536   83  Linux
/dev/sda2           59272       60802    12285953    5  Extended
/dev/sda5           59272       60802    12285952   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```I cant access the disk through Nautilus either. There i get Unable  to mount 488GB filesystem. DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

So can anyone explain to me what the heck is going on with my harddrive? is it dead? is there anyway to recover the data? will a reinstall of ubuntu fix the issue?

---

### Post by mreyes on 2011-03-20
> **perfecti0n said:**
> Hello!
 
I have a HP ProBook 6540b labtop and while doing a system resume ubuntu froye at splash screen with the dots. So I powered it off and when starting it again the error showed up
 
```
mount: mounting /dev/disk/by-uuid/***************************** on /root
failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg
 
Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs)
```Anyway after some googling for the solution i found a tip to do this
 
sudo fdisk -l
 
where i got the partition where linux is installed 
and then
 
sudo fsck /dev/sda1
 
however, doing this...the terminal returns
 
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59272   476097536   83  Linux
/dev/sda2           59272       60802    12285953    5  Extended
/dev/sda5           59272       60802    12285952   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```I cant access the disk through Nautilus either. There i get Unable to mount 488GB filesystem. DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending
 
So can anyone explain to me what the heck is going on with my harddrive? is it dead? is there anyway to recover the data? will a reinstall of ubuntu fix the issue?
 
Hi perfecti0n, 
 
It is happening the same to me with a DELL. After boot error with same message, I used a LiveCD, got the linux partition and, after "fsck", I received same message: "Filesystem mounted or opened exclusively by another program?"
I have not found any way to access the hard drive.
 
Have you found a solution? 
Thank you

---

### Post by mreyes on 2011-03-20
[QUOTE=mreyes;10579869]Hi perfecti0n, 
 
It is happening the same to me with a DELL. QUOTE]
 
Hi again, 
 
consulting more in the forums, I saw that GParted could be used to try to repair partitions. I downloaded an image, burnt a CD and boot from it. Once the application was running, I chose the boot partition and select the option recover (repair). After a minute it completed the repair. 
 
I booted again from the hard disk and now the laptop is working perfectly.
 
Cheers
Marcos

---

### Post by Juand_au on 2011-04-12
> **mreyes said:**
> [QUOTE=mreyes;10579869]Hi perfecti0n, 
 
It is happening the same to me with a DELL. QUOTE]
 
Hi again, 
 
consulting more in the forums, I saw that GParted could be used to try to repair partitions. I downloaded an image, burnt a CD and boot from it. Once the application was running, I chose the boot partition and select the option recover (repair). After a minute it completed the repair. 
 
I booted again from the hard disk and now the laptop is working perfectly.
 
Cheers
Marcos

Thank You!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

