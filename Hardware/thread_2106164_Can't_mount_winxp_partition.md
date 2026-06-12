---
title: "Can't mount winxp partition"
date: 2013-01-18
forum: Hardware
---

### Post by fdrake on 2013-01-18
I have a dell tower (). I am trying trought a live cd to mount/see the content of the win partition. but I get teh following errors:
```

sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x16652b8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    80292869    40146403+   7  HPFS/NTFS/exFAT

```

```

ubuntu@ubuntu:~$ sudo mkdir /media/win
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /medai/win
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```



When I boot in windows I get these errors:
"Missing file BOOT.INI"
and then it says "Booting from: C:\windows" and then it stops.


I am burning now a winxp cd to see it will let me fix the hdd or copy the missing files.

---

### Post by ahallubuntu on 2013-01-18
I hope running chkdsk from a Windows CD will fix file system corruption.

You may wish to re-boot the Ubuntu disc and install GSmartControl to check S.M.A.R.T. status of the drive to see if has started to fail (very common).  Open a terminal in Ubuntu and type:

```
sudo apt-get update
sudo apt-get install GSmartControl
```

then go back to "dash" and search for "GSmartControl."

Click on the Attributes tab.  Any Attributes highlighted in Red?  Pending sectors are very bad.  Reallocated sectors are not catastrophic but a lot of them are a warning sign that the drive will soon fail.

---

### Post by Mark Phelps on 2013-01-20
> **fdrake said:**
> When I boot in windows I get these errors:
"Missing file BOOT.INI"
and then it says "Booting from: C:\windows" and then it stops.


I am burning now a winxp cd to see it will let me fix the hdd or copy the missing files.

Sorry I didn't respond earlier ... but this means that (1) your filesystem is damaged to the extent that the boot.ini file can no longer be read properly, or (2) your hard drive is failing such that it is corrupting the filesystem.

Unfortunately, Windows filesystems can't really be fixed from Linux.  If you can connect the drive to an Windows PC, you can try running CHKDSK on it.

---

### Post by greg_ory on 2013-01-20
found the same issue in another forum what might help you or at least gives you some ideas.

[http://www.linuxforums.org/forum/ubuntu-linux/164227-solved-error-mounting-mount-exited-exit-code-13-a.html](http://www.linuxforums.org/forum/ubuntu-linux/164227-solved-error-mounting-mount-exited-exit-code-13-a.html)

-Greg

---

### Post by fdrake on 2013-01-23
Thanks Everyone for your help. This is what I got:

- I cannot fix the partition with the win xp cd . It does not recognize the partition.

- @ahallubuntu:
 these are the errors I get with gsmartconrtol (below screenshots and error log)

- @greg_ory: 
  I cannot follow the solution suggested by the O.P. since when I run gparted it just hangs in there.... it does not show any results

- @Mark Phelps:
   I will try to connect the hdd with a usb adapter to a windows system and see if I can get anything done.

PS: I do know that the disk is quite old but I do not really need all the data I just need to have a view of the files: list their name  and location. Even a partial recovery would be fine...

---

### Post by fdrake on 2013-01-25
ok. I got good news. 
I was able to connect the hdd as a slave disk to another pc containiing a winxp partition. Then running the " chkdsk D: -f " did the trick for me. It took a while to recover the system but I got all the files back! I still I canot boot to the original win xp due to some dll files missing but I don't care since now I can mount the filesystem and browse its content.

Thank you for your support and help. ):P:popcorn:

---

