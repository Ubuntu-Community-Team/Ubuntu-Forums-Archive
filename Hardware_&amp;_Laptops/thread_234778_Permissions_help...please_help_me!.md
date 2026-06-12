---
title: "Permissions help...please help me!"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by seiferkai on 2006-08-12
i would like to know how to permanatly mount this drive to a certain directory in /media/hdb1

in fstab i have inserted this code

"/dev/hdb1       /media/hdb1     ext3    defaults        0       0"

and then i press alt+f2 and added this code

"sudo mount /dev/hdb1 /media/hdb1"

now when i try to access the drive on my profile not root i get this message

The folder contents could not be displayed.

You do not have the permissions necessary to view the contents of "hdb1".

how can i permanatly mount it and how can i get permissions please help me!

---

### Post by JerMe on 2006-08-12
Try using Applications > Terminal.  When you issue the sudo command, you need to type in a password.

Actually, since you already edited your /etc/fstab file, type **sudo mount -a** to mount all the drives contained in your /etc/fstab file.  Again, do this using the terminal, and enter your password when prompted.

---

### Post by seiferkai on 2006-08-12
ok i did that and now i get this error

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: wrong fs type, bad option, bad superblock on /dev/hdb1,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



and i was starting to believe that it might be in NTFS format..i was praying it wasnt but i ran "run sudo fdisk -l" and i got a reading with this


Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4665    37471581   83  Linux
/dev/hda2            4666        4866     1614532+   5  Extended
/dev/hda5            4666        4866     1614501   82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36481   293033601    7  HPFS/NTFS


so how can i go about getting this harddrive linux compatable?? anyoone?
or is there a way i can use this ntfs in linux??

---

### Post by JerMe on 2006-08-12
I'm going to link you to a VERY good source of information where I first learned how to format and partition drives in Linux.  It might be a little to read, but you won't regret it.  It's from the Gentoo Linux install guide.
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4#doc_chap3](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4#doc_chap3)

Teach a man to fish, they say... ;)

In a nutshell, you'll use fdisk to edit the /dev/hdb1 partition table, wipe out the current NTFS drive and create a Linux partition.  Then you'll use the command **mke2fs -j -O dir_index /dev/hdb1** to create an Ext3 partition.  Then, you can mount your /dev/hdb1 as an Ext3.

When they say you learn about Linux when you install Gentoo, they weren't kidding.  The good thing about it is that you learn enough to help others.  Good luck~

---

### Post by seiferkai on 2006-08-12
lol sorry to ask but how do i open fdisk for hdb1??
i plan on making 1 big partition on this drive cause all i want to use it for 
is to store music and pics and other files

---

### Post by JerMe on 2006-08-12
The "#" signs in the Gentoo install guide means root.  So when you see that before the command, just put a "sudo" in front of it.

So **sudo fdisk /dev/hdb** will open the fdisk prompt for your 2nd HDD.

---

### Post by seiferkai on 2006-08-12
i was wondering..should i follow what they said and make 3 partitions or does this look right to create 1 partition with the full 300gb

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36481   293033601   83  Linux

---

### Post by JerMe on 2006-08-12
Looks beautiful.  You don't need to do the swap and other things; you only need to know how to delete partitions, and make them with fdisk (which you did nicely).  Now run the command to make it an Ext3.

---

### Post by seiferkai on 2006-08-12
ok i did it and im getting this

seifer@Aeris:~$ mke2fs -j -O dir_index /dev/hdb1
mke2fs 1.38 (30-Jun-2005)
mke2fs: Permission denied while trying to determine filesystem size

does this mean i have to make it into a ext2?

---

### Post by JerMe on 2006-08-12
sudo!!!

```
sudo mke2fs -j -O dir_index /dev/hdb1
```

---

### Post by seiferkai on 2006-08-12
ok thanks

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 21 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.


does that mean its done?? i mean truly
could it be mounted and used now?

---

### Post by JerMe on 2006-08-12
Time to find out.  Mount everything your /etc/fstab by issuing
```
sudo mount -a
```

---

### Post by seiferkai on 2006-08-12
i guess it worked...i can enter it and all i can see is a lost+found folder
will it stay mounted even after restart?
and how can i set permissions to 777?

---

