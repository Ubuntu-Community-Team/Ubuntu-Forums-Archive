---
title: "Adding Another HD"
date: 2015-10-12
forum: Hardware
---

### Post by tkolano on 2015-10-12
I know this has been asked before, but I was not able to figure out the exact process.
The problem: Running out of storage space
I have two HD's installed already. One has Ubuntu installed and where all my files/programs are. The other has nothing there but is marked as "lost and found".
The second HD seems to be auto mounted.
The second HD is called Raptor 2 and under the properties for "Disk" the location is: /media/username File system ext3/4

I want to be able to install programs on this drive, or merge this drive so Ubuntu knows it can install files/programs there, and use it as swap if needed (I know the swap may be tricky and is not the main point of this thread).

I have Gparted installed as well.
main drive path says /dev/sda
Partition:
/dev/sda1 - ext 4
/dev/sda2 - extended
/dev/sda5 - linux-swap

The second drive (Raptor 2)
/dev/sda1 - ext4
Mount point:
/media/username/Raptor2

How can I take advantage of the storage of Raptor 2?

Thanks!

---

### Post by yancek on 2015-10-12
You already have a swap partition on sda and do not need another one.  Check the permissions by opening a terminal and running this command:

```
ls -l /media/username
```

It should show the owner:group for Raptor 2.  It's generally a bad idea to have spaces in directory names.  The lost+found directory is expected to be there on an otherwise empty partition.  Most applications you install will be dependent upon libraries and other software and won't function if not installed to the proper location.  You can put data there obviously but depending upon the owner and permissions.  Also, your second drive should not be 'sda1' as sda refers to the first drive and the numbers are partitions.  Post the ls -l output as well as the output of:  sudo fdisk -l(Lower Case Letter L in the command)

---

### Post by tkolano on 2015-10-12
Below is the output
> krash@krash-122-CK-NF68:~$ ls -l /media/krashtotal 4
drwx------ 3 krash krash 4096 Jul 20 12:38 Raptor2
krash@krash-122-CK-NF68:~$ 


---

### Post by weatherman2 on 2015-10-12
We need the output of

```
sudo fdisk -l
```

too.

If the second disk is a lot bigger, you could simply clone the first disk to it (which copies everything), then switch to using only the second disk for everything (maybe use the first disk as a spare or a little extra storage or something).  But more specific recommendations can be made with the info above.

---

### Post by tkolano on 2015-10-12
Both disks are the same size;

output below

> Disk /dev/sda: 37.0 GB, 37019566080 bytes255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005b68b


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    63918079    31958016   83  Linux
/dev/sda2        63920126    72302591     4191233    5  Extended
/dev/sda5        63920128    72302591     4191232   82  Linux swap / Solaris


Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8e9dadd8


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    72303839    36151888+  83  Linux




---

### Post by weatherman2 on 2015-10-12
I'd probably move your /home partition to /dev/sdb1 .  You may be able to do this while booted (assuming /dev/sdb1 is empty):

1. Make sure Raptor2 is mounted, then:


```
sudo rsync -a /home /media/username/Raptor2/
```

2. After this point, anything you might save in /home/username will be lost until you finish the remaining steps so do this all at once.

3. Find the UUID of your /dev/sdb1 (so you could add disks later and not worry about the order they are connected):

```
sudo blkid
```

There will be several lines of output, including one that looks like this (not exactly):

```
/dev/sdb1: LABEL="Raptor2" UUID="f7480d9c-cda4-4fd0-801f-75ef5d11ab46" TYPE="ext4" 
```

Use that UUID (in quotes) below.

3. Edit your /etc/fstab file:

```
sudo gedit /etc/fstab
```

(or use your favorite text editor)

Add this line at the bottom:

```
UUID=f7480d9c-cda4-4fd0-801f-75ef5d11ab46 /home               ext4    defaults        0       2
```

but (important) REPLACE "f7480d9c-cda4-4fd0-801f-75ef5d11ab46" with your partition's UUID.

(You can use any text editor to do this, not just gedit.)

Save the edited fstab file after you are done.

4. Finally, mount the partition and make sure everything is correct:

```
sudo mount -a
```

If this command succeeds, THERE IS NO OUTPUT (kind of counter-intuitive).  If there was a mistake, it will give you an error.

If there is no output, type the df command to confirm the new /home is mounted:

```
df
```

You should now see an extra line showing your new /home on /dev/sdb1 .

Reboot to be completely sure all is well (you won't have an option to mount /media/username/Raptor2 anymore).

Now, to free up space on the first drive, remove the old /home.  It might be easiest to do this from a live USB boot, but you could try it without that:

Unmount the new /home partition (assuming the steps above were successful and you have rebooted):

```
sudo umount /dev/sdb1
```

Now type "df /home" and you should see the old /home again.  You can erase it:

```
sudo rm -rf /home
```

Again - I'm assuming you made sure everything was correctly copied from /home to the new one on /dev/sdb1 and you have tested that it worked correctly.

Now reboot.

---

### Post by tkolano on 2015-10-12
Thank you so much for that info. I am about to try it out, but will this COMBINE both drives so I can use both to save programs? It looks as though this is a move. Thanks and sorry for the noobish comments!

---

### Post by weatherman2 on 2015-10-12
Please ask as many questions as you need to before even attempting what I have proposed!

What I am suggesting moves everything in /home to the second drive.  I am making the assumption that you use a considerable amount of space in /home to save files, but I could be wrong.  (FYI, all Downloads, Documents, Music, etc. go into your home folder by default).  You could run this command:

```
sudo du -k /home | tail
```

This will tell us how much space is being used in /home.

Unless you are downloading and installing many programs (more than the typical user) or compiling lots of programs from source code, you don't really need much space in your / (root) partition. 37GB including a swap and root (/) partition is probably sufficient for the average user, just for that.  My laptop's root partition is only 15GB with Ubuntu, but I also have my /home on another partition.

---

### Post by tkolano on 2015-10-13
Thanks for being so patient, it's greatly appreciated. So we are really talking about moving my home directory to my other drive (Raptor 2). Raptor2 will not have / (ubuntu/Linux) thereby giving me that much more space on raptor2. The next question would be what would I do when Raptor 2 gets tight on space?

output below:
> krash@krash-122-CK-NF68:~$ sudo du -k /home | tail[sudo] password for krash: 
20	/home/krash/.kde/share/apps/libkface/database
24	/home/krash/.kde/share/apps/libkface
12	/home/krash/.kde/share/apps/kconf_update/log
16	/home/krash/.kde/share/apps/kconf_update
200	/home/krash/.kde/share/apps
296	/home/krash/.kde/share
300	/home/krash/.kde
4	/home/krash/Music
12344520	/home/krash
12344524	/home
krash@krash-122-CK-NF68:~$ 




---

### Post by weatherman2 on 2015-10-13
OK, you are using about 12.3GB on /home.  So moving it to its own hard drive will balance things nicely on a 37GB volume.

What do you do when Raptor2 gets low on space?  Delete some stuff - or upgrade to a larger hard drive.

---

### Post by weatherman2 on 2015-10-13
You COULD create an LVM volume on Raptor2 instead of a regular partition.  Then, someday, if Raptor2 fills up, you could simply attach a third hard drive and create another LVM and add it to your existing /home volume.  But that's a bit more complicated than what I suggested above.

---

