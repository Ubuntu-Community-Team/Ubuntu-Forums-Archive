---
title: "cannot mount Crashed NTFS HD"
date: 2008-07-05
forum: Hardware
---

### Post by Kopiermeister on 2008-07-05
Hello!
I had a problem in Windows XP (desktop-pc), the hd/System-partition is crashed, i mean XP cannot boot anymore, boot.ini is missing and other system files too.
So i wanted to mount the partition with ubuntu (put the hd in an external case that i can use the hd with my notebook via usb), to save my data. But everytime i want to mount the partition i get the fallowing error message:

[IMG]http://img502.imageshack.us/img502/227/bildschirmfotognomemounci8.png[/IMG]

Can anyone help me, please?

Regards

---

### Post by LinuxRocks713 on 2008-07-05
What is your partition number? Please post the contents of 

```

fdisk -l

```

so we can see.

Once you know, type this in the terminal:

```

sudo mkdir /media/winxp
sudo mount -t ntfs /dev/*** /media/winxp #replace *** with the partition(sdX) or (hdX)

```

Hope that helped :)

---

### Post by coolaj86 on 2008-07-05
Have you tried booting into the Recovery Console from Windows XP CD? You should be able to run chkdsk and maybe even replace corrupted files that way.


You can also force the mount from the command line even though the check failed. I don't know that command off the top of my head though.

---

### Post by Kopiermeister on 2008-07-06
@ LinuxRocks713:
sudo fdisk -l tells me:
```
Platte /dev/sdf: 163.9 GByte, 163928604672 Byte
255 Köpfe, 63 Sektoren/Spuren, 19929 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x00000001

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdf1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sdf2           16709       19626    23438835   83  Linux
/dev/sdf3           19627       19929     2433847+  82  Linux Swap / Solaris

``` i need the sdf1
so i typed in
```
sudo mkdir /media/winxp
sudo mount -t ntfs /dev/sdf1 /media/winxp
``` but i get the same error message as above.


@coolaj86:
Yes i've tried, but i had no success. chkdsk took too much time (1,5h for 18%). Just when i typed in a simple command like "dir" i got an error message, that the directory could not be shown...

There's something really wrong with the hd...

Regards

---

### Post by Kopiermeister on 2008-07-11
No ideas? Pls, i need help!!

Regards

---

### Post by MasterNetra on 2008-07-11
Why would you want to mount it in Ubuntu anyway? Ubuntu can't do anything to its contents. Can't really open,edit,copy,paste files or anything of that nature. Its just pointless.

However from the sounds of it. You probably need to fix the mbr (Master Boot Record) for that you will need the OS cd. Make your way to command prompt via the CD and i think the command is FIXMBR if not should be close. But note this will allow only windows to boot. So if you duel booting, have a install CD for the duel booting software your using to handle both OS's and re-install it after you fix the MBR. And it is possible a virus destroyed or corrupted your boot files and although FIXMBR can restore it, its recommend you do a complete scan of the virus once you can finally get into windows and remove it to prevent it from doing it again (or just do it to see if you have it.)

---

### Post by molochi on 2008-07-11
I haven't had any probs reading or writing to my NTFS partitions and drives.

Am using ntfs3g and fuse but I think it was part of default install.

---

### Post by coolaj86 on 2008-07-11
Well, if it takes three days to run scandisk, let it run 3 days. At least then you're using a windows util to fix a windows drive. Patience is hard, but it's worth it.

Another option is to use gddrescue to copy the drive bit-per-bit and then run photoRec on the image that you create to rescue the raw files.

PhotoRec works on windows too.

But first and foremost I'd try using the windows scandisk. In the worst case that "Deleting orphan file" scrolls down your screen 50,000 times (that happened to me once... ugh... a very bad day) photorec will still work as file recovery.

Until you have an informed decision, do NOT play with your partition table.

Does that help at all?

---

### Post by sisco311 on 2008-07-11
Try:
```
sudo mount -t ntfs -o defaults,force,umask=0002,gid=46 /dev/sdf1 /media/winxp
```

---

### Post by coolaj86 on 2008-07-11
> **MasterNetra said:**
> Why would you want to mount it in Ubuntu anyway? Ubuntu can't do anything to its contents. Can't really open,edit,copy,paste files or anything of that nature. Its just pointless.

Where have you been living? Under a rock?

I thought all those Ubuntu 5.04 cds were out of circulation like 3 years ago. Not only can you do anything you want with the files, you can even install Ubuntu in a windows drive via Wubi.

(Just goofy sarcasm, no offense intended)

---

### Post by ahmedusthefirst on 2008-07-11
hey guys, new user here. i have a similar problem to Kopiermeister, except my ubuntu partition is on an external hard drive and my internal windows partition cannot be mounted. i receive this error whenever i try to mount it: 

Cannot mount Volume
unexpected clusters per mft record (-128). Failed to mount '/dev/sda2': Invalid argument The device '/dev/sda2' doesn't have a valid NTFS. maybe you selected the wrong device? Or the whole disk instead of a partition (eg /dev/hda, not /dev/hda1)? or the other way around?

note: i have three other partitions on my internal hard drive and i can access each one of them.

i've tried accessing the windows recovery utility, but it doesn't see the partition, so i can't rewrite the mbr and i can't access my data. i ran fdisk, but that tells me the partition table for my external drive and not my internal. please help, all my data is on that partition. thanks

---

### Post by coolaj86 on 2008-07-11
Are you using Vista or XP? Vista has a known 'feature' which writes invalid MBRs.
Here's some support info on it: [http://support.microsoft.com/kb/919529](http://support.microsoft.com/kb/919529)

Can you give any background information? E.G. When the problem started happening, after what operation?

Can you post fdisk -l?

---

### Post by ahmedusthefirst on 2008-07-11
yeah, the problem started last night around 12, i was trying to set up grub on my external hd. i think what i did wrong was i typed setup (hd0,1) when i was in sudo grub. when i rebooted after that, my windows partition no longer worked. 
here is my fdisk -l:


Disk /dev/sdb: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa315a315

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7122    57207433+   c  W95 FAT32 (LBA)
/dev/sdb2   *        7123        9560    19583235   83  Linux
/dev/sdb3            9561        9729     1357492+  82  Linux swap / Solaris

however, sdb is my external hard drive and i cant get a table for sda, it keeps telling me cannot open /dev/sda.

---

### Post by coolaj86 on 2008-07-11
So what SHOULD your hda look like?

Something like this?

hda1 - Accessible NTFS
hda2 - Inaccessible windows drive
hda3 - Accessible NTFS

Windows stores a copy of the MFT, which is similar to a superblock in EXT3, at the end of the drive. It sounds like you've wiped the primary one out by installing grub over top of it and copying the backup one over grub could work.

I googled ntfs backup mft and found this, which looks useful at-a-glance.
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Let us know how your luck fairs.

---

### Post by Kopiermeister on 2008-07-13
Jeah, i was able to rescue most data with the tool "GetDataBack for NTFS" !!
Thx allot for help!!

Regards

---

