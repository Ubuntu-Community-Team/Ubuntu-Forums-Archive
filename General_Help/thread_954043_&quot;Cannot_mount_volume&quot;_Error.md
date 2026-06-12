---
title: "&quot;Cannot mount volume&quot; Error"
date: 2008-10-20
forum: General Help
---

### Post by jamestaylor11 on 2008-10-20
[FONT=Verdana][SIZE=2]Hi, 

Installed Ubuntu and managed to get most of the things working that I want to, apart from being able to use my external HDD.  

When i plug it in and turn it on i get the following error message:[/SIZE][/FONT]  


[FONT=Arial][SIZE=2]Cannot mount volume.

Unable to mount the volume.

mount:wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error.  In some cases useful info is found in syslog - try dmesg | tail or so

[SIZE=2][FONT=Verdana]
I have been told the way to mount my HDD is to make a folder and set it up to mount to that each time the drive is turned on.  I dont have a clue how to do this though.  

Im sure the answer is on these forums somewhere but i havent managed to find it. 

Thanks for any help in advance, 
James.  
[/FONT][/SIZE][/SIZE][/FONT]

---

### Post by shawnrgr on 2008-10-20
plug your drive in and paste the output of the following:

```
sudo fdisk -l
```

---

### Post by jamestaylor11 on 2008-10-21
Thank you for the response.  



```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007a9fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00063e52

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24792   199141708+   7  HPFS/NTFS
```

---

### Post by shawnrgr on 2008-10-21
```
sudo mkdir /media/my-ntfs
mount -t ntfs-3g /dev/sdb1 /media/my-ntfs -o force
```

if you get an error post the output

---

### Post by buixuanduong1983 on 2008-10-21
Normally I have problem with external harddisk if I use it in Windows and forget to unmount it before unpluging it out. In that case I just borrow a Windows to safety remove USB device.

---

### Post by vanadium on 2008-10-21
You should also precede the second command of shawnrgr with "sudo":

```
sudo mkdir /media/my-ntfs
sudo mount -t ntfs-3g /dev/sdb1 /media/my-ntfs -o force
```

The procedure he is making you follow is the best to obtain a good diagnosis of the problem. The rest is speculation.

---

### Post by jamestaylor11 on 2008-10-21
> **shawnrgr said:**
> ```
sudo mkdir /media/my-ntfs
mount -t ntfs-3g /dev/sdb1 /media/my-ntfs -o force
```

if you get an error post the output


That worked.  But then when i turned the drive off and back on again, it said i could not access it.  I did the same as what i did before to make it work, but i got this error:

ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory


Is there a way of it being able to be mounted by its self each time i turn it off and on again?

Thanks.

---

### Post by jamestaylor11 on 2009-02-02
This works now but each time i have to enter:

sudo mkdir /media/my-ntfs
sudo mount -t ntfs-3g /dev/sdb1 /media/my-ntfs -o force

Is there a way i can get it to mount on its own when i turn the drive on?

Thanks, 
James.

---

