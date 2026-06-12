---
title: "mount and unmount ext4"
date: 2013-01-31
forum: Hardware
---

### Post by Mascarade on 2013-01-31
Hi everybody!

I try to mount a partition in ext4, and i was following this french thread :
[http://forum.ubuntu-fr.org/viewtopic.php?id=383127](http://forum.ubuntu-fr.org/viewtopic.php?id=383127)

but, i was stuk at 2 line (of command) next the end....
It was possible to view the /media/video in ext4, but it was impossible to write on it...
And i saw a folder in /media/video, is name was lost&found, like the home folder, before the user....

And after i was bored of this so i start Gparted, unmount, format in ntfs format...
(cuz it just for data...)

Now each time i reboot, the system stop, and i need to press F1, to see a message that display my raid device ok, and an other message to skip /media/video or mount manually.....But this /media/video doesn't exist at all cuz i format it! But i think somewhere there some piece of it??
And i can't unmount it, cuz it not mount anymore, but the system still recognize it!!??

I'm using kubuntu 12.10...
What do you think? 

Thank!
):P

---

### Post by ajgreeny on 2013-01-31
You will need to edit your fstab file to take account of the new NTFS partition with its new UUID.

Let's see the output of ```
sudo blkid -c /dev/null
``` and your current /etc/fstab file from ```
cat /etc/fstab
```Tell us which is the new NTFS partition and we'll tell you how to proceed.

---

### Post by Mascarade on 2013-01-31
sudo blkid -c /dev/null

/dev/sda5: LABEL="Video" UUID="249ED17813DAC901" TYPE="ntfs" 
/dev/sdb1: LABEL="Muzik" UUID="0E3707AB531F6B89" TYPE="ntfs" 
/dev/sdc1: UUID="c417d56a-2553-63d4-fb12-7e256da4b3ec" UUID_SUB="3c6e3b31-f992-b4a6-f4eb-9d643ed100e9" LABEL="Kubuntu:0" TYPE="linux_raid_member" 
/dev/sdc5: UUID="2c4b4a12-491f-4508-d6c0-920edec0de3f" UUID_SUB="474dbf51-d3a7-cc8b-973a-d0dd144343c8" LABEL="Kubuntu:1" TYPE="linux_raid_member" 
/dev/sdc6: UUID="79a172b3-1303-bfec-9e62-b0e9696df99a" UUID_SUB="df5a2c03-ca09-4121-c27b-edf63ce2ef2f" LABEL="Kubuntu:2" TYPE="linux_raid_member" 
/dev/sdc7: UUID="eaea29cc-aa5d-2329-708e-d31765aed3b5" UUID_SUB="921a55e9-a8be-3fea-1394-54d6da444510" LABEL="Kubuntu:3" TYPE="linux_raid_member" 
/dev/sdd1: UUID="c417d56a-2553-63d4-fb12-7e256da4b3ec" UUID_SUB="c445ca23-9e60-4f19-e477-2c1fc099773e" LABEL="Kubuntu:0" TYPE="linux_raid_member" 
/dev/sdd5: UUID="2c4b4a12-491f-4508-d6c0-920edec0de3f" UUID_SUB="31dcdcd9-052e-7de4-4bde-b34ee76ee887" LABEL="Kubuntu:1" TYPE="linux_raid_member" 
/dev/sdd6: UUID="79a172b3-1303-bfec-9e62-b0e9696df99a" UUID_SUB="39fc5c98-dd62-cd44-2b83-9ca9042c4cf9" LABEL="Kubuntu:2" TYPE="linux_raid_member" 
/dev/sdd7: UUID="eaea29cc-aa5d-2329-708e-d31765aed3b5" UUID_SUB="ae4cf8aa-f7bd-2e51-fbbb-f01fe7df04d8" LABEL="Kubuntu:3" TYPE="linux_raid_member" 
/dev/md3: UUID="19ba70ef-88b9-40bb-ab26-a1d13dd15651" TYPE="ext4" 
/dev/md2: UUID="c91fe897-9d5e-4806-a882-90657d9a3f79" TYPE="swap" 
/dev/md1: UUID="c870adbe-86b7-49ad-8aad-fc1b6845ec8e" TYPE="ext4" 
/dev/md0: UUID="fff7cf19-238f-4d38-9a55-0c42fab54e2e" TYPE="ext4" 
/dev/sr2: LABEL="Clickfree_System" TYPE="iso9660" 
/dev/sde1: LABEL="Backup" UUID="8C2847092846F22E" TYPE="ntfs"


cat /etc/fstab

/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    nodev,noexec,nosuid     0       0
#Entry for /dev/md1 :
UUID=c870adbe-86b7-49ad-8aad-fc1b6845ec8e       /       ext4    errors=remount-ro 0       1
#Entry for /dev/md0 :
UUID=fff7cf19-238f-4d38-9a55-0c42fab54e2e       /boot   ext4    defaults  0       2
#Entry for /dev/sda5 :
UUID=b64e6e57-9c6e-4931-a3dd-d5dec9aece1c       /media/Video    ext4      defaults        0       2
#Entry for /dev/sdb1 :
UUID=0E3707AB531F6B89   /media/Muzik    ntfs    defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177      00
#Entry for /dev/md3 :
UUID=19ba70ef-88b9-40bb-ab26-a1d13dd15651       /home   ext4    defaults  0       2
#Entry for /dev/md2 :
UUID=c91fe897-9d5e-4806-a882-90657d9a3f79       none    swap    sw0       0

Thanks for your help again :o)

---

### Post by ajgreeny on 2013-01-31
First backup fstab with ```
sudo cp /etc/fstab /etc/fstabbak
```just in case.

I am assuming the lines
```
#Entry for /dev/sda5 :
UUID=b64e6e57-9c6e-4931-a3dd-d5dec9aece1c       /media/Video    ext4      defaults        0       2
```
in your current fstab are those for the partition, now ntfs, that you want to mount automatically at boot.

Edit those lines to
```
#Entry for /dev/sda5
UUID=249ED17813DAC901 /media/Video/    ntfs-3g        auto,user,rw 0 0
```Save the file and then run ```
sudo mount -a
```If there is no error message, the partition will be mounted and all should be OK at next boot.

---

### Post by Mascarade on 2013-01-31
Hi again amigo :)

Just to be sure we are understanding each other....
my partition ntfs is ok, she mount automatically, the probleme is the ancian partition ext4 on the same drive that cause a probleme even if i format it whit gparted many time......the ext4 is not mounted.....

i try what you told me...
i backup the fstab
at the second command the konsole said that it is a directory and the last command said that uuid....does not exist?

let see:

mascarade@Kubuntu:~$ sudo cp /etc/fstab /etc/fstabbak
[sudo] password for mascarade: 
mascarade@Kubuntu:~$ #Entry for /dev/sda5
mascarade@Kubuntu:~$ UUID=249ED17813DAC901 /media/Video/    ntfs-3g        auto,user,rw 0 0
bash: /media/Video/: Is a directory
mascarade@Kubuntu:~$ UUID=249ED17813DAC901 /media/Video/    ntfs-3g        auto,user,rw 0 0
bash: /media/Video/: Is a directory
mascarade@Kubuntu:~$ sudo mount -a
mount: special device UUID=b64e6e57-9c6e-4931-a3dd-d5dec9aece1c does not exist

I just want to kill the ext4 ghostpartition :)

I try to reboot and i get the same message : /media/video is not ready or present....

not to strange?
:p

---

### Post by ajgreeny on 2013-01-31
Sorry but I think you completely misunderstood my post.
Does that ntfs partition automount at boot?  There is no fstab entry for it so it should not do so, but you should be able to mount it by clicking on it in dolphin or whatever filemanager you use.

Also, I was not meaning you to enter
```
#Entry for /dev/sda5 :
UUID=b64e6e57-9c6e-4931-a3dd-d5dec9aece1c       /media/Video    ext4      defaults        0       2
```in a terminal as you did, but merely quoting your current fstab where those lines point to the old ext4 partition, now ntfs, that you want to mount automatically at boot.

Edit those lines using ```
kdesu kate /etc/fstab
```in terminal, which will open fstab as root, and change them to
```
#Entry for /dev/sda5
UUID=249ED17813DAC901 /media/Video/    ntfs-3g        auto,user,rw 0 0
```Save the file and then run ```
sudo mount -a
```If there is no error message, the partition will be mounted and all should be OK at next boot.[/QUOTE]

---

### Post by Mascarade on 2013-03-05
Hi ajgreeny sorry for taking time to respons ;) But now i really understand fstab! All work fine ;)
The only thing is : if i have a partition like ntfs and i use gparted to delete and make a new ntfs drive why the partiton that is supposed to be delete still remaid in my /media???

There is my new fstab

#Entry for /dev/md0 :
UUID=79aef55b-dbcc-463b-b1b6-df7f9b88ea0d    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdc1 :
UUID=4dd8dcd4-6648-4c47-a4fa-a596e7de50a2    /boot    ext4    defaults    02
#Entry for /dev/sda1 :
UUID=1DDB403525E3D2AA    /media/Repair_Data      ntfs-3g   auto,user,rw       0       0
#Entry for /dev/sdb1 :
UUID=13FEEB97588C9CED    /media/Data    ntfs-3g    defaults,rw,user,auto,locale=en_CA.UTF-8    0    0
#Entry for /dev/md1 :
UUID=4c6114de-6b81-46ac-8317-50c6a70bf698    /home    ext4    defaults    02
#Entry for /dev/sdd5 :
UUID=2d463d94-c7fe-49ee-bf27-696d034f9728    none    swap    sw    0    0

 but i my /media i got my repair Data and Data partition (ntfs) and the old one that are not present in /etc/fstab....why?
Can i remove it?

---

