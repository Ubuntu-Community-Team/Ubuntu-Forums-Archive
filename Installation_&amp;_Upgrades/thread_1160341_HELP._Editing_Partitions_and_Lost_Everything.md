---
title: "HELP. Editing Partitions and Lost Everything"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by danger pigeon on 2009-05-15
I was editing my partitions last night because i had done a poor job allocating space when i installed ubuntu. I had given root 280gb and it turns out it didnt need nearly that much. So i decided to shrink it to 50gb, leave 100gb open to install windows xp on, and put the rest into my home partition. I used the live cd and everything seemed to work fine. When i rebooted it was all good. 

However when i tried to install windows i kept getting an error message that windows could not write to the hard disk and i needed to create a partition windows could use. I tried a few times to create an ntfs partition in the 100gb partition but no dice. So i figured it was a bad cd and quit the setup process. When i rebooted this time it said it could not find the OS. I fired up the live cd again, which i'm on now and checked the partitions, thinking windows had mislabeled something, and it says my whole HD is unallocated with no partitions. I don't know how this happened, what i did, or how to fix it. I need some help here.

---

### Post by acer8930 on 2009-05-15
I'am in no way anywhere as familiar with Linux as a lot of these people, and have only been using Ubuntu a few weeks, so I'm not really gonna try to give you technical help.

There are some tools you could try aside from the partion tool on the Live CD.

You could search a torrent site for "HiRen bootcd". I think the latest version is 9.8. There are several tools on there you could try.

Theres also GParted Live:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

You could burn that or put it on a USB drive and see if anything pops up.

---

### Post by oldos2er on 2009-05-15
Can you run this command while booted to the LiveCD, and paste the results here?
```
sudo fdisk -l
```

---

### Post by danger pigeon on 2009-05-15
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x776b776b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       42528   341606128+  83  Linux
/dev/sda2           42529       60801   146777872+   5  Extended
/dev/sda3           59478       60801    10634998+  82  Linux swap / Solaris
/dev/sda5           42530       46467    31631953+  83  Linux
/dev/sda6           46468       59477   104502793+   e  W95 FAT16 (LBA)

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux
ubuntu@ubuntu:~$

---

### Post by logos34 on 2009-05-15
either the attempted resize or windows messed up the partition table

> omitting empty partition (5)


doesn't look like sda1 shrank at all

what does 
> 
sudo sfdisk -d

show?

---

### Post by danger pigeon on 2009-05-15
It did shrink the partition though, at least at first. After  changed the partitions around i was worried i messed something up because i've never changed the partitions so much while there was data on them before. But i restarted immediately after and everything worked fine, and the partitions were all the right sizes. It wasn't until i tried installing windows that this happened.


ubuntu@ubuntu:~$ sudo sfdisk -d 
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=683212257, Id=83, bootable
/dev/sda2 : start=683212320, size=293555745, Id= 5
/dev/sda3 : start=955498068, size= 21269997, Id=82
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=683228448, size= 63263907, Id=83
/dev/sda6 : start=746492418, size=209005587, Id= e
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=1953520002, Id=83
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

---

### Post by logos34 on 2009-05-15
Try this:

> sudo sfdisk -d /dev/sda | sudo sfdisk --force /dev/sda

to correct the partition table

After you do that run
> 
sudo fdisk -l

again and post output.

Then maybe you can install windows

---

### Post by danger pigeon on 2009-05-16
Here's the output:
 
ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x776b776b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       42528   341606128+  83  Linux
/dev/sda2           42529       60801   146777872+   5  Extended
/dev/sda3           59478       60801    10634998+  82  Linux swap / Solaris
/dev/sda5           42530       46467    31631953+  83  Linux
/dev/sda6           46468       59477   104502793+   e  W95 FAT16 (LBA)

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux
ubuntu@ubuntu:~$ 

I'm gonna try to restart and see if this worked. I'll let you know what happens.

---

### Post by danger pigeon on 2009-05-16
If someone could help me just get the information from my home folder off the HD, i'll just do a clean install. I want to try to avoid losing all my settings if i can. I can't access my home folder from the live cd for some reason. I changed the permissions of it to allow me read/write acess but now instead of saying i don't have permissions it just shows the folder as being empty. Is there something else i have to do that i'm not doing?

---

### Post by logos34 on 2009-05-16
Well, at least that cleared the partition table of the 'empty' ones (I think).

Does Gparted show the disk partitions now correctly?

So, you still can't boot ubuntu install on sda1 and now you can't even see anything in /home from the live cd?  You shouldn't have changed the permissions though--if you applied it recursively to the entire dir then you screwed things up and will definitely have to reinstall.

Are you sure it's mounted and you're looking in the right place?  Did you try mounting it manually?

sudo mkdir /media/ubuntu

sudo mount -t ext3 /dev/sda1 /media/ubuntu

ls -l /media/ubuntu/home/<yourusername>

---

### Post by danger pigeon on 2009-05-16
Gparted still shows an unallocated drive. And I did apply it recursively to the whole dir so i guess i'm out of luck. This is like the 4th or 5th time i've had to reinstall cause i tried doing something without really understanding what i'm doing. At least i have all my files on an external. This time i'll install windows first then install ubuntu. 

Thanks for the help logos. This is why ubuntu is awesome though, this kind of help would have cost over $100 for a windows technician to tell me my computer was ******. Is it alright if i message you later if something goes wrong with the reinstall?

---

### Post by logos34 on 2009-05-16
There is one final way to recover the disk/partitions as it was BEFORE the resize and windows install business.  

Install and run **testdisk** on the live cd:

first enable **universe** repositories in system>admin>synaptic>Settings>repos

sudo apt-get install testdisk

sudo testdisk

Read [this page]("http://www.users.bigpond.net.au/hermanzone/p21.html") and the [official docs]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

---

