---
title: "Boot issue/change"
date: 2008-11-01
forum: General Help
---

### Post by jsegars on 2008-11-01
I can't remember how I setup my boot but here's what's happening...I have a 120G disk and a 320G disk. I have linux installed on the 120G and I use the 320G for data storage. I tried to remove the 320 today to add it to a network storage box only to find that my comp wouldn't boot...kept getting "can't find a system disk" or something along those lines. I popped my 320G back in and l0oked at everything with fdisk and the partition on the 320G was flagged as BOOT. This is not what I want so I'm lookin' for some help to get everything onto the 120G. The boot partition is on the 120G so I'm not sure what's hanging out on the 320 unless it's in the MBR. Below is the output from fdisk:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd789d789

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8aef8ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14216   114189988+  83  Linux
/dev/sdb2           14217       14593     3028252+   5  Extended
/dev/sdb5           14217       14593     3028221   82  Linux swap / Solaris

```
And the output from df after an initial boot:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             109G   65G   39G  63% /
varrun                506M  232K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   68K  506M   1% /dev
devshm                506M   48K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon      109G   65G   39G  63% /home/jboy/.gvfs
/dev/sdc6             9.8G  5.0G  4.8G  51% /media/LINUX TRANS
/dev/sdc5             140G  102G   38G  74% /media/Storage
/dev/scd0              77M   77M     0 100% /media/cdrom0
```

---

### Post by meierfra. on 2008-11-01
> I'm not sure what's hanging out on the 320 unless it's in the MBR. 
It looks like grub  is installed to the MBR of your 320GB drive. To fix this:

Open a terminal and type

```
sudo grub
```

and at the grub prompt:

```

device (hd0) /dev/sdb
root (hd0,0)
setup (hd0)
quit
```

You also need to edit menu.lst:

```
gksudo gedit /boot/grub/menu.lst
```

Look for

# groot=(hd1,0)

(should be close to line 74) and change it to

# groot=(hd0,0)


Save the file. In the terminal


```
sudo update-grub
```


You should now be able to boot  when the 320GB drive is unplugged. (If you want to boot with both drives plugged in, you will have to set your bios to boot from the 120GB)

---

### Post by jsegars on 2008-11-01
That worked like a charm, thanks for the help and the quick response.

---

