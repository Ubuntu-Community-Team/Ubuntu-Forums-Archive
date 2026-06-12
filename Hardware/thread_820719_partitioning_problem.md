---
title: "partitioning problem"
date: 2008-06-06
forum: Hardware
---

### Post by four2theizz0 on 2008-06-06
Hey everyone,

I have a new laptop with a 250gb hard drive.  I am having some problems creating a new partition.

I have these partitions on it in this order stating from teh beginning of the disk

1 - recovery partition with restore files from manufacturer cuz they dont ship with disks anymore - 10gb
2 - c:/ - 60gb
3 - ext2 - Hardy - 40gb
4 - Swap - 10gb

That leaves me with approx 120gb of unallocated space.  I know you can only mkae 4 primary partitions...which is what i now have


What i would like is a fat32 shared partition and I cannot make it because an extended partition is part or a primary(according to the gpartitioner error) and in the future a d:/ drive for vista

So i want two more logical drives basically and cant make an extended partition.  Am i able to do this?

I know I can also use samba for a shared drive..but the problem would still remain how to make the new drive

Any help or suggestions woudl be greatly appreciated

Thank you

---

### Post by logos34 on 2008-06-07
yes its possible to make an extended partition if you delete the swap first (you meant **1** GB, right?)

Then using Gparted create a new ext'd partition out of the remaining disk space, and stick a new swap, fat32 amd anything else inside.

Boot from the livecd, open gparted and delete swap.  Create extended and logical partitions for new swap and others

Click on details in the gparted dialog box to see new uuids. Change swap uuid to new one in fstab and add entries for other partitions. Open file browser as root:

gksudo nautilus

Mount root partition.  Edit swap line in /etc/fstab and add entries for the others.  Don't forget to create mount point(s).

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-58b0f4b165129f43a80bba6c1c4227c490efa119](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-58b0f4b165129f43a80bba6c1c4227c490efa119)

Personally, I'd use ntfs rather than fat, or else ext3 and install **fs-driver **on vista side.

---

### Post by four2theizz0 on 2008-06-09
sweeet, thanks alot man.  it worked.  :guitar:

I also used ntfs.  I had just read somewhere that fat32 was more reliable between the two OS's but I had wanted to use ntfs.

One problem was that I was unable to update the fstab, but it is still working.  it still has the old info and I am not sure what to put in place for the new drives.  I have the UUID's:
```

ls /dev/disk/by-uuid/
1A1EC54E1EC5239B                      9C967C6A967C4734
6630-3837                             A6C66857C66829AF
937f29ee-4af6-492f-a41b-8208a9ce34ec  c35caae3-26f7-4794-86ee-be11898d6c74

```

Here is my current fstab
```

 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c35caae3-26f7-4794-86ee-be11898d6c74 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=fc077308-d1e3-4ed3-8811-7087f3c55083 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

Here is fdisk -l
```
sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf8743c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1245     9995264   27  Unknown
/dev/sda2   *        1245        9077    62914560    7  HPFS/NTFS
/dev/sda3            9078       13988    39447607+  83  Linux
/dev/sda4           13989       30401   131837422+   5  Extended
/dev/sda5           13989       14677     5534361   82  Linux swap / Solaris
/dev/sda6           14678       21095    51549184    7  HPFS/NTFS


```

I have searched around and found a few fstab editing posts but am not sure.  If you can help or have any good posts that would be great.  Thanks again!

---

### Post by logos34 on 2008-06-09
Use [ntfs-config ]("https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971")to add ntfs partitions and edit fstab automatically

Use 
[B]
ls [COLOR="Red"]-l[/COLOR] /dev/disk/by-uuid/[/B]

to find the uuids AND the partitions they correspond to.

Then update the swap uuid (now sda5) in fstab:

gksudo gedit /etc/fstab

---

### Post by four2theizz0 on 2008-06-11
holy crap, that was it?!  Thank you.  I thought it was alot more, All done :biggrin:

thanks again

---

