---
title: "Grub &quot;Unknown Filesystem&quot;"
date: 2010-01-06
forum: Hardware
---

### Post by joux on 2010-01-06
Hi forum. I already have some experience with Ubuntu, but haven't signed up to this forum until now. I hope you can help me with the following problem, I found no existing help.

I have installed a new, larger harddisk to my dual-boot notebook and copied the old data with dd. Then I resized and moved the partitions with GParted, in order to use the new space.

But now the Grub bootloader fails saying "error: unknown filesystem"

From a boot CD, I checked all partitions (ext4, swap, ntfs), they are ok and I can mount them. I re-installed Grub with ```
grub-install --root-directory=/mnt/drive /dev/sda
``` which completes successfully. Also, the device.map file looks ok, it just says ```
(hd0) /dev/sda
```
When I type ls at the Grub rescue shell, it correctly lists all my partitions. but when I try to list the contents of a particular partition (ls (hd0,2) ) it says "unknown filesystem" again.
What else do I need to check? I really don't want to reinstall both Ubuntu and Windows XP.

I'm looking forward to your help and suggestions.

---

### Post by joux on 2010-01-07
I'm attaching the results of the [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/"), this should contain all details I forgot..

---

### Post by meierfra. on 2010-01-07
The boot info script did not reveal any problems, so I'll have to take a shot in the dark.

How old is your laptop? Some bios are only able to handle hard drive of size up to 137GB.   Try this

```
sudo mount /dev/sda4 /mnt 
sudo grub-install --disk-modules=ata --root-directory=/mnt /dev/sda
```


If this did not work, let's see what happens if you put the Grub folder on the first partition:

```
sudo mount /dev/sda1 /mnt 
sudo grub-install --root-directory=/mnt /dev/sda
```

I'm not sure that either of these will work, but I would it least like to know whether they make any difference.

---

### Post by joux on 2010-01-08
Thank you.

I have already tried putting Grub into the first partition (I actually repartitioned and reinstalled Ubuntu, without the Windows partitions) without any luck,

I will try the --disk-module parameter when I find the time, for now I had to put the old, working hdd back in. The computer is not too old, a HP nx6325, maybe 3 years old.

---

### Post by adam814 on 2010-01-08
Hmm...just as a passing thought...maybe GRUB isn't loading the modules it needs?  If you try "insmod ext4" and "insmod ntfs" first does it work?

---

### Post by meierfra. on 2010-01-08
I must have been asleep, when I checked your "RESULTS.txt" last night.  You  were missing "grub.cfg", the file that generates the Grub menu.
Anyway, since you reinstalled that does not matter anymore. 

> I have already tried putting Grub into the first partition (I actually repartitioned and reinstalled Ubuntu, without the Windows partitions) without any luck,

It's not so important that Ubuntu is on the first partition, but where exactly the boot files are.  So you need to create a small partition for Ubuntu (say 15-20GB) at the beginning of the drive and then a large  Home or  Data partition. Or create a small Boot partition (500MB) at the beginning of the drive.

But since your computer is only three years old, I actually doubt that this will solve your problem,


> maybe GRUB isn't loading the modules it needs? If you try "insmod ext4" and "insmod ntfs" first does it work? 


Good point.   So if you end up at the Grub prompt again, try

```
insmod ntfs
insmod ext2
```

before using the "ls" command.  (Grub uses "ext2" for all the ext filesystem:  ext2, ext3, ext4)

If none of this helps, run the boot info script again so we can have  a look at your new setup.

---

### Post by joux on 2010-01-11
Thank you for your support. I tried the --disk-module=ata switch. After that, I was getting
```
error:device can not be identified
error: ATA read error
```
but after some time (and disk access) the Grub menu would finally come up.

As I did not want to have these error messages slow down my boot process, I tried the other thing you said. Now I have a small ext3 /boot partition at the beginning of the disk. And everything seems to be fine now.

Thanks again.ö

---

### Post by meierfra. on 2010-01-11
> Now I have a small ext3 /boot partition at the beginning of the disk. And everything seems to be fine now.

Great. Have fun with Ubuntu.

---

### Post by introspectif on 2010-05-28
> **meierfra. said:**
> How old is your laptop? Some bios are only able to handle hard drive of size up to 137GB.

This was true for me. I am using an EeePC 901, and got this problem when I tried to install on my USB hard disk after a 200+ GB partition. I just changed the partition to somewhere near the beginning of the disk, and all the problems are gone now.

Just thought that this would be useful to those who have the EeePC 901. 

I wonder what significance the "137 GB" has, or whether it's only an arbitrary number.

---

