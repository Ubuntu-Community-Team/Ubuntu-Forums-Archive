---
title: "Problem with usb drives"
date: 2009-01-27
forum: Hardware
---

### Post by kd4dii on 2009-01-27
I am having a problem with 2 external drives, one is an 80 GB hard drive in an external enclosure, the other a usb memory stick.  The problem is if I try to write to the drive or delete any files on it I get a permission denied error.  I can write to the drives as root.  When I check the permissions in properties it says it is unable to determine permissions for the device.  I had the hard drive set up as NTFS before but changed it to EXT2 which is when the problem with it began.  The memory stick is from Bestbuy and has some software on it that is from the so called Geek squad.  I don't know what it supposed to do and I don't want it, just want to use it as an extra drive.  I am running Ubuntu 8.1 on a Toshiba laptop and am still somewhat of a noobe.

Bob

---

### Post by taurus on 2009-01-27
Where (mount point) did you mount the USB drive?  If it's ext2, you can change the ownership of the mount point for that drive from root to your login name.  Then, you can write or delete whatever you want on that drive.

```
sudo fdisk -l
df -h
id
```

---

### Post by kd4dii on 2009-01-27
Thanks for the quick reply.  I tried the code you sent and the first 2 give me a lot of info about the disks in my system and the third info about my login name, but I don't see where I can change ownership of the drive.  Sorry to be a pain but I am still pretty much a noobe and am not too familiar with terminal commands.

Bob

---

### Post by taurus on 2009-01-27
Since you don't want to post the outputs, I will assume that drive is mounted to /media/sdb1 and your login name is john.  You can change the ownership of /media/sdb1 to your log in name with

```
sudo chown -R john:john /media/sdb1
```

---

### Post by kd4dii on 2009-01-27
Sorry, I didn't realize you wanted me to post the output, here it is:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00028882

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19199   154215936   83  Linux
/dev/sda2           19200       19457     2072385    5  Extended
/dev/sda5           19200       19457     2072353+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2622eb63

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

dad@dad-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             145G  8.2G  130G   6% /
tmpfs                 346M     0  346M   0% /lib/init/rw
varrun                346M  340K  346M   1% /var/run
varlock               346M     0  346M   0% /var/lock
udev                  346M  2.7M  343M   1% /dev
tmpfs                 346M  396K  346M   1% /dev/shm
lrm                   346M  2.0M  344M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1              74G  147M   70G   1% /media/disk

dad@dad-laptop:~$ id
uid=1000(dad) gid=1000(dad) groups=4(adm),20(dialout),21(fax),24(cdrom),26(tape),29(audio),30(dip),44(video),46(plugdev),104(scanner),106(fuse),108(lpadmin),114(netdev),123(admin),124(sambashare),1000(dad)
dad@dad-laptop:~$ 


Again, thanks for the quick reply.

Bob

---

### Post by taurus on 2009-01-27
```
sudo chown -R dad:dad /media/disk
ls -la /media/disk
```

---

### Post by kd4dii on 2009-01-27
Thanks Taurus, that worked, I can write to the drives now.  The only remaining problem is that there appears to be a hidden partition that has the software from the "Geeksquad" on it.  I cant see it in Qtparted or the partition editor.  When the drive is mounted it wants to run software.  I can see the partition, but can't delete it or write to that section.  I don't think the info above shows it either.  Not a major problem just an annoyance.  Thanks again for the help.

Bob

---

