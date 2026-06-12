---
title: "Triple Boot Question"
date: 2008-11-18
forum: General Help
---

### Post by cobhc on 2008-11-18
Ok, I don't know if this is the right section or not, sorry if it isn't.

I've got a triple boot setup where I installed XP first, then Vista, then Ubuntu 8.10. I used EasyBCD to mod the Vista Boot Manager to include Ubuntu. There is also GRUB running under the Ubuntu Partition. These 3 OS' are on 3 different partitions on one 200GB drive. Now I'd like to remove Vista, and then resize both the XP and Ubuntu partitions to 100GB each. What's my best way of doing this so that they will both still boot ok? My main worry is the Ubuntu partition will become the second partition on the drive, not the third (as it is currently), and I think this might confuse GRUB. Can I simply remove/resize the partitions, and then run FIXMBR from the XP CD, and then reconfigure GRUB and/or the XP Boot.ini? I don't mind which I end up using as long as both partitions boot ok.

Also, I've seen online that resizing partitions might corrupt some OS', I've resized partitions in the past, but as far as I'm aware they were blank, so never came across this before.

Thanks in advance for your help.

---

### Post by TeXtonyx on 2008-11-18
I'll offer one opinion. I just got rid of Vista. I ran fixmbr and
fixboot from the XP cd first. If XP will boot then I think it's
safe to delete Vista. The worst that can happen in that you'll
have to do a Startup Repair from Vista Recovery Console to make
everything boot again. With just XP and Ubuntu I use Bootpart
to boot Ubuntu from XP's boot.ini menu, but you can also do it
with grub. Hmmm, if you delete Vista and apportion the unallocated
space to XP and Ubuntu there will only be two partitions. But I
suppose you could put a swap partition in between them. I'm not
so sure that your concern is valid, or not.

---

### Post by caljohnsmith on 2008-11-18
How about first posting:
```
sudo fdisk -lu
```
Also, is XP the first partition on the drive? If so that's good, because you definitely don't want to resize XP's partition from the beginning unless you want to jump through alot of hoops to get XP booting again. If the Vista partition is in between XP and Ubuntu, it sounds like your plan will work fine, but there are definitely some details you will need to take care of. For one thing, probably all of Vista's boot files are located in your XP partition, which is usually what happens when you install Vista after XP. Also, Vista would have modified the XP boot sector to boot "bootmgr" instead of XP's "ntldr", so you'll need to repair the XP boot sector to boot XP again. And about your boot loader, I would recommend just using Grub to boot either XP or Ubuntu, but as TeXtonyx suggests, another option is you can modify your Windows boot.ini to boot Ubuntu. It's up to you, and there are other options available too. If you would like more specifics of how to do any of the things I mentioned, please post the fdisk output first and we can work from there if you want. :)

---

### Post by cobhc on 2008-11-18
> **caljohnsmith said:**
> How about first posting:
```
sudo fdisk -lu
```
Also, is XP the first partition on the drive? If so that's good, because you definitely don't want to resize XP's partition from the beginning unless you want to jump through alot of hoops to get XP booting again. If the Vista partition is in between XP and Ubuntu, it sounds like your plan will work fine, but there are definitely some details you will need to take care of. For one thing, probably all of Vista's boot files are located in your XP partition, which is usually what happens when you install Vista after XP. Also, Vista would have modified the XP boot sector to boot "bootmgr" instead of XP's "ntldr", so you'll need to repair the XP boot sector to boot XP again. And about your boot loader, I would recommend just using Grub to boot either XP or Ubuntu, but as TeXtonyx suggests, another option is you can modify your Windows boot.ini to boot Ubuntu. It's up to you, and there are other options available too. If you would like more specifics of how to do any of the things I mentioned, please post the fdisk output first and we can work from there if you want. :)

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x747aa6b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   153597464    76798701    7  HPFS/NTFS
/dev/sda2       153597465   307194929    76798732+   7  HPFS/NTFS
/dev/sda3       307194930   390716864    41760967+  83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x238b175e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   390716864   195358401    7  HPFS/NTFS

```

That's the output of fdisk -lu.

XP is the first partition on the drive. So I could delete the partition, resize the XP and Ubuntu partitions, then run FIXMBR from the XP cd to get the XP bootblock back in place, and then add Ubuntu back into the XP Boot.ini since GRUB would still be in place on the Ubuntu partition? The reason I was worried about Ubuntu being the second partition is that obviously at the moment GRUB is set to boot from (hd0,2) and it would need to boot from (hd0,1) instead, right?

---

### Post by caljohnsmith on 2008-11-18
So are you planning on using the XP boot loader rather than Grub in the MBR? Running "fixmbr" will install a Windows MBR, but not to the boot sector of the Windows partition. The problem I mentioned earlier about Vista modifying the XP partition boot sector to boot bootmgr instead of ntldr can be fixed by running "fixboot" on the XP partition. After that, XP will probably boot just fine; you will probably want to delete the C:\bootmgr file and the C:\Boot directory from the XP partition since those are for Vista only. 

If you don't want to install Grub to the MBR and instead want to use the Windows boot loader, you will have to first install Grub to the partition boot sector of the Ubuntu partition with:
```
sudo grub
grub> root (hd0,1)
grub> setup (hd0,1)
grub> quit
```
Assuming Ubuntu is sda2. Then you can copy over the Grub boot sector to use in Windows boot.ini using the "bootpart" program TeXtonyx mentioned. Let us know how it goes.

---

### Post by cobhc on 2008-11-18
Which is the easiest option? Grub, or the XP Boot loader?

---

### Post by caljohnsmith on 2008-11-18
> **cobhc said:**
> Which is the easiest option? Grub, or the XP Boot loader?
I prefer to use Grub instead of the XP boot loader, and it takes just a few simple steps to install it to your MBR from the Live CD:
```
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
And that's it. Of course you will also need to modify your menu.lst so that the UUIDs and the (hd0,2) references are changed for Ubuntu, since both will change. But regardless of whether you use Grub in the MBR or the Windows boot loader, you still have to modify your menu.lst. You can find the new UUID for Ubuntu's partition with:
```
sudo blkid
```
Let me know how it goes.

---

### Post by cobhc on 2008-11-18
Ok, cool. So I remove the Vista partition, and resize the partitions, etc. in Ubuntu. Then run the steps you posted using the Live CD, then I can get back into Ubuntu and edit Grub to boot off of XP as well? Also, where is menu.lst located?

---

### Post by caljohnsmith on 2008-11-18
> **cobhc said:**
> Ok, cool. So I remove the Vista partition, and resize the partitions, etc. in Ubuntu. Then run the steps you posted using the Live CD, then I can get back into Ubuntu and edit Grub to boot off of XP as well?
Actually, I just realized that since the UUID of the Ubuntu partition will change, you will also need to update your /etc/fstab, which you can do from the Live CD. So once you resize XP and Ubuntu, then you can do the following from the Live CD fix your menu.lst and /etc/fstab:
```
sudo mount /dev/sda2 /mnt
sudo blkid
gksudo gedit /mnt/boot/grub/menu.lst
```
Then in your menu.lst, change (hd0,2) in the Ubuntu entries to use (hd0,1), and also change the "UUID" lines in the Ubuntu entries to use the new sda2 UUID as given by the blkid command above. You'll also want to change the "#groot=(hd0,2)" line to be "#groot=(hd0,1)", and the "#kopt" line to use the new sda2 UUID. Next open fstab:
```
gksudo gedit /mnt/etc/fstab
```
Find the line in fstab that mounts the Ubuntu partition on "/", and change it to use the new sda2 Ubuntu partition UUID, similar to:
```

UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 [COLOR="Red"]/[/COLOR]  ext3  relatime,errors=remount-ro 0 1
```
So change the above UUID in your fstab entry. After that you should be able to boot Ubuntu. Windows might take a little more work to boot than just doing the "fixboot", because sometimes resizing its partition partially corrupts the file system parameters in the partitions boot sector; fortunately that is usually easy to fix with testdisk if it is a problem. 

Let me know how it goes. :)

---

### Post by cobhc on 2008-11-18
Ok, I'll come back to you after I'm back into Ubuntu. Thanks for the help man.

---

### Post by cobhc on 2008-11-18
Ok, so I'm using the Live CD at the moment, to partition the drive. It looks like the Ubuntu partition is going to stay as sda3, unless it changes once the partition operations finish?

---

### Post by cobhc on 2008-11-18
> **cobhc said:**
> Ok, so I'm using the Live CD at the moment, to partition the drive. It looks like the Ubuntu partition is going to stay as sda3, unless it changes once the partition operations finish?

Finished it now and the Ubuntu partition stayed as sda3, I know this doesn't really matter, but any way of changing this to sda2?

---

### Post by caljohnsmith on 2008-11-18
> **cobhc said:**
> Finished it now and the Ubuntu partition stayed as sda3, I know this doesn't really matter, but any way of changing this to sda2?
I don't know of any way to simply change the partition number, but it will make fixing things a little easier. Just follow the instructions from my previous posts, but use the UUID for sda3, and also continue to use (hd0,2) in your menu.lst. Give it a shot and let me know if you run into problems.

---

### Post by cobhc on 2008-11-18
I'm assuming that the line "sudo mount /dev/sda3 /mnt" is like the subst command in windows and it should mount the drive to the /mnt folder? There is nothing related to the drive when I look in the /mnt folder though.

---

### Post by caljohnsmith on 2008-11-18
> **cobhc said:**
> I'm assuming that the line "sudo mount /dev/sda3 /mnt" is like the subst command in windows and it should mount the drive to the /mnt folder? There is nothing related to the drive when I look in the /mnt folder though.
Once you mount sda3 on /mnt, the /mnt directory should have your root Ubuntu directory, i.e. should look similar to:
```
drwxr-xr-x   2 root root  4096 2008-11-14 07:00 bin
drwxr-xr-x   3 root root  4096 2008-11-11 10:51 boot
lrwxrwxrwx   1 root root    11 2008-11-03 14:55 cdrom -> media/cdrom
drwxr-xr-x  15 root root 13880 2008-11-18 12:12 dev
drwxr-xr-x 130 root root 12288 2008-11-18 12:13 etc
drwxr-xr-x   3 root root  4096 2008-11-03 15:13 home
lrwxrwxrwx   1 root root    32 2008-11-03 15:24 initrd.img -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 root root  4096 2008-11-14 07:01 lib
drwx------   2 root root 16384 2008-11-03 14:55 lost+found
drwxr-xr-x   6 root root  4096 2008-11-11 19:12 media
drwxr-xr-x   3 root root  4096 2008-11-16 16:40 mnt
drwxr-xr-x   2 root root  4096 2008-10-29 15:53 opt
dr-xr-xr-x 122 root root     0 2008-11-18 00:00 proc
drwxr-xr-x  13 root root  4096 2008-11-13 14:18 root
drwxr-xr-x   2 root root  4096 2008-11-14 07:01 sbin
drwxr-xr-x   2 root root  4096 2008-10-29 15:53 srv
drwxr-xr-x  12 root root     0 2008-11-18 00:00 sys
drwxrwxrwt  14 root root  4096 2008-11-18 12:13 tmp
drwxr-xr-x  11 root root  4096 2008-10-29 15:58 usr
drwxr-xr-x  15 root root  4096 2008-10-29 16:12 var
lrwxrwxrwx   1 root root    29 2008-11-03 15:24 vmlinuz -> boot/vmlinuz-2.6.27-7-generic

```
If it doesn't look similar to what's above, then please post a listing of the /mnt directory:
```
ls -l /mnt
```

---

### Post by cobhc on 2008-11-18
```
lrwxrwxrwx    1 root root      11 2008-11-17 12:44 cdrom -> media/cdrom
lrwxrwxrwx    1 root root      32 2008-11-17 12:50 initrd.img -> boot/initrd.img-2.6.27-7-generic
lrwxrwxrwx    1 root root       4 2008-11-17 12:45 lib64 -> /lib
drwx------ 1085 root root 1179648 2008-11-17 12:44 lost+found
drwxr-xr-x    2 root root    4096 1970-01-01 00:00 sbin
lrwxrwxrwx    1 root root      29 2008-11-17 12:50 vmlinuz -> boot/vmlinuz-2.6.27-7-generic

```

That's all I get. Does that sound like my Ubuntu Partition is bricked?

---

### Post by caljohnsmith on 2008-11-18
It looks like everything might be in your "lost+found" folder; how about posting the contents of that folder. Also, please post:
```
sudo fdisk -lu 
```

---

### Post by cobhc on 2008-11-18
Saying I don't have the permissions to access lost+found both in terminal and the file browser. And "sudo fdisk -lu" returns this:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x747aa6b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   195366464    97683201    7  HPFS/NTFS
/dev/sda3       195366465   390716864    97675200   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x238b175e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   390716864   195358401    7  HPFS/NTFS

```

---

### Post by caljohnsmith on 2008-11-18
How about doing:
```
sudo chmod 755 /mnt/lost+found
```
And try to look in lost+found again. If you still have problems, you could open a file browser as root user:
```
gksudo nautilus /mnt &
```

---

### Post by cobhc on 2008-11-18
Gained access, but all the files are called #242972, #2429756, etc. I think it's knackered lol.

---

### Post by caljohnsmith on 2008-11-18
> **cobhc said:**
> Gained access, but all the files are called #242972, #2429756, etc. I think it's knackered lol.
Unfortunately, I would have to agree with you; sounds like something must have gone wrong with the partition resizing and now all the files are obviously messed up. Did you get any errors from the partition editor (gparted)? It looks like you're stuck with a reinstall. Did you have any important files you need to recover? Recovering any files could take alot of time at this point since they have all been renamed, and we don't know what is what.

---

### Post by cobhc on 2008-11-18
> **caljohnsmith said:**
> Unfortunately, I would have to agree with you; sounds like something must have gone wrong with the partition resizing and now all the files are obviously messed up. Did you get any errors from the partition editor (gparted)? It looks like you're stuck with a reinstall. Did you have any important files you need to recover? Recovering any files could take alot of time at this point since they have all been renamed, and we don't know what is what.

No errors, and no. All the important stuff I have was on the second disk. I'll get XP back up and running by itself and reinstall Ubuntu. Thanks for your help anyway.

---

### Post by caljohnsmith on 2008-11-18
> **cobhc said:**
> No errors, and no. All the important stuff I have was on the second disk. I'll get XP back up and running by itself and reinstall Ubuntu. Thanks for your help anyway.
That's really a bummer, I've never had any problems with gparted like that yet. I sure wonder what happened. Anyway, good luck with the reinstall. :)

---

