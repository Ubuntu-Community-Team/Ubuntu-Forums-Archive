---
title: "How do I auto Mount Partitions and Media at Startup?"
date: 2010-07-23
forum: Hardware
---

### Post by Jonners59 on 2010-07-23
All my machines have a various mix of Partitions and Media (built in hard drives) where I store documents and images, etc....  These do not start/mount when the machines starts up, I have to go to each and mount it manually, by selecting from Places or double clicking a link, or whatever....

How do I set them to load automatically when I boot up the machines?

PS.  I am not referring to the HOME folder, this does start automatically, this is the other media/partitions.

---

### Post by IcarusR on 2010-07-23
You need to add a line for each drive/partition to /etc/fstab something like this...

```
/dev/sdd1 ~/hdd ext3 rw 0 0
```

For help see manual pages for fstab & mount.

```
man mount
```

```
man fstab
```

---

### Post by Morbius1 on 2010-07-23
It's really a set of three templates. Each one specific to how the partition was formatted:

***STEP 1: Find out how the system sees your partitions***

In a Terminal:
```
 sudo blkid -c /dev/null
```This will output , for example, the following partitions that I  want to mount at boot:

/dev/sda1: UUID="DA9056C19056A3B3" LABEL="WinXP" TYPE="ntfs"
/dev/sda6: LABEL="COMMON" UUID="C4DB-C1B0" TYPE="vfat"
/dev/sdb6: LABEL="Data" UUID="f7927995-b098-42be-ada0-987857f5177a"  TYPE="ext3"

***STEP 2: Create mount points for your partitions to live in***. ***For example:***
In a Terminal:
```
sudo mkdir /media/WinC
sudo mkdir /media/WinD
sudo mkdir /media/Data
```***STEP 3: Add lines to /etc/fstab/ to have these partitions mount at  boot:***

Edit fstab as root by:
```
gksu gedit /etc/fstab
```Then add the following lines to fstab:

/dev/sda1 /media/WinC      ntfs     defaults,nls=utf8,umask=007,gid=46    0    0
/dev/sda6 /media/WinD      vfat    utf8,umask=007,gid=46 0        2
/dev/sdb6 /media/Data     ext3    defaults,noatime 0 2

***Step 4: Mount them*** ***by executing the new fstab***

In a Terminal:
```
sudo mount -a
```There are a great number of different options you can use with these  fstab entries depending on your particular needs. Some are only  applicable to specific filesystems, but for the most part this is a good  starting point. In fact the templates you see in step 3 are what  happens when you allow Ubuntu to set up these non-system partitions when  choosing the manual partitioning option during an install.

---

### Post by Jonners59 on 2010-07-23
Sorry Guys
You both lost me a bit here...

I did step 1 and got:
[HTML]/dev/sda1: LABEL="Applications" UUID="3AEAAC2DEAABE37D" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="ECC48DADC48D7A9A" TYPE="ntfs" 
/dev/sda4: UUID="457eafb1-fef4-4bb1-b4d2-983115c90e93" TYPE="ext4" 
/dev/sda5: UUID="79ff52fa-f0c0-49f4-95ff-f9de68549c71" TYPE="ext4" 
/dev/sda6: UUID="4fb34c44-3ecc-4092-a386-6d50077b4a49" TYPE="swap" 
/dev/sdb2: TYPE="swap" 
/dev/sdb3: UUID="b0ac51ce-8eca-4937-95d5-1702d993c17c" TYPE="ext4" 
/dev/sdb4: UUID="c1cbd04d-a2ff-41d0-bc3c-cdcb41a4898f" TYPE="ext4" 
/dev/sdb5: LABEL="Documents" UUID="C3BC446AB5B142DF" TYPE="ntfs" 
/dev/sdb6: LABEL="Backup" UUID="8E11BEEB85AE896D" TYPE="ntfs" [/HTML]

The One I want to mount here is
[HTML]/dev/sdb5: LABEL="Documents" UUID="C3BC446AB5B142DF" TYPE="ntfs" [/HTML]

I did step 2, but not sure if just copy paste was correct, but did it anyway...

Step 3...  This is my config:

[HTML]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb4 during installation
UUID=c1cbd04d-a2ff-41d0-bc3c-cdcb41a4898f /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb3 during installation
UUID=b0ac51ce-8eca-4937-95d5-1702d993c17c /boot           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=4fb34c44-3ecc-4092-a386-6d50077b4a49 none            swap    sw              0       0
/dev/sdb2       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/HTML]

Not sure if [HTML]UUID=c1cbd04d-a2ff-41d0-bc3c-cdcb41a4898f /               ext4    errors=remount-ro 0       1[/HTML] is anything to worry about!!!!

Please advise, as I don't want to really screw it all up.

And sorry for being a bit thick.

---

### Post by Morbius1 on 2010-07-23
For your specific partition:
> /dev/sdb5: LABEL="Documents" UUID="C3BC446AB5B142DF" TYPE="ntfs"Create a mountpoint, say ... WinDoc
```
sudo mkdir /media/WinDoc
```Then add this line in fstab :
```
 /dev/sdb5 /media/WinDoc      ntfs     defaults,nls=utf8,umask=007,gid=46     0    0
```After you save the fstab file you can mount the new entry in fstab by:
```
sudo mount -a
```

---

### Post by Jonners59 on 2010-07-23
You are great!!!  Worked PERFECTLY

I have another machine, the main one that this is required for...  If I get stuck will you help, please?  Won't be for a few weeks no-doubt.

PS any good on networking probs?

---

### Post by Jonners59 on 2010-11-19
> **Morbius1 said:**
> For your specific partition:
Create a mountpoint, say ... WinDoc
```
sudo mkdir /media/WinDoc
```Then add this line in fstab :
```
 /dev/sdb5 /media/WinDoc      ntfs     defaults,nls=utf8,umask=007,gid=46     0    0
```After you save the fstab file you can mount the new entry in fstab by:
```
sudo mount -a
```

How would I auto mount more than 1 ext, which I assume are Data drives.  I.e. I want to open these two:

[HTML]/dev/sdb1: LABEL="Backup" UUID="d499866a-0817-4001-a89b-d16977ec02c3" TYPE="ext4" 
/dev/sdb2: LABEL="Documents" UUID="34554d66-9ae8-40e4-808a-d3b22d06623d" TYPE="ext4" [/HTML]

I tried:
[HTML]/dev/sdb1 /media/Data     ext4    defaults,noatime 0 2
/dev/sdb2 /media/Data     ext4    defaults,noatime 0 2[/HTML]

But it only opened 1 deive (Backup, sdb1) the other could not open, saying is was already mounted.

Likewise if I have a number of ntfs , would I use 

sudo mkdir /media/WinC
sudo mkdir /media/WinD
sudo mkdir /media/WinE
etc

---

### Post by Morbius1 on 2010-11-19
> /dev/sdb1 /media/Data     ext4    defaults,noatime 0 2
/dev/sdb2 /media/Data     ext4    defaults,noatime 0 2The /dev/sdb1 and /dev/sdb2 parts are the actual physical partitions. The /media/Data part is the mountpoint for that physical device. Each physical device must have it's own unique mountpoint. So you might want to create another mountpoint for /dev/sdb2, say .... /media/DataDoc and then change the line in fstab to:
```
 /dev/sdb2 /media/DataDoc     ext4    defaults,noatime 0 2
```> Likewise if I have a number of ntfs , would I use 

sudo mkdir /media/WinC
sudo mkdir /media/WinD
sudo mkdir /media/WinE
etc     Yes

---

### Post by Jonners59 on 2010-11-19
> **Morbius1 said:**
> The /dev/sdb1 and /dev/sdb2 parts are the actual physical partitions. The /media/Data part is the mountpoint for that physical device. Each physical device must have it's own unique mountpoint. So you might want to create another mountpoint for /dev/sdb2, say .... /media/DataDoc and then change the line in fstab to:
```
 /dev/sdb2 /media/DataDoc     ext4    defaults,noatime 0 2
```Yes

Morbius
You're great.  You always bail me out!!  Well, almost.  Still have a networking issue, now on two machines.

---

### Post by Jonners59 on 2010-12-02
> **Morbius1 said:**
> The /dev/sdb1 and /dev/sdb2 parts are the actual physical partitions. The /media/Data part is the mountpoint for that physical device. Each physical device must have it's own unique mountpoint. So you might want to create another mountpoint for /dev/sdb2, say .... /media/DataDoc and then change the line in fstab to:
```
 /dev/sdb2 /media/DataDoc     ext4    defaults,noatime 0 2
```Yes

Morbius
COuld I call these mount points almost anything?  I.e. name them as per the intended partition.  So one might be WinJonners and another might be WinShared...?

Also, how do I change permissions on them, so that I own them, not root..  I want to share them and at present they will not allow me to.

---

### Post by CharlesA on 2010-12-02
You can change the place you have them mounted, yes.

For example, I have my array mounted to /array (due to convience and me being lazy).

```
UUID=05c730b5-680d-4d33-8e2e-76947d7a93fa       /array  ext4    noexec  0       0
```

Here's the permissions on that folder:

```
drwxr-xr-x 13 charles raid 4096 2010-11-25 08:55 /array/
```

---

### Post by searchfgold6789 on 2010-12-02
> **Jonners59 said:**
> 
COuld I call these mount points almost anything?  I.e. name them as per the intended partition.  So one might be WinJonners and another might be WinShared...?
Yes. You may have to personally create the directory though.
> 
Also, how do I change permissions on them, so that I own them, not root..  I want to share them and at present they will not allow me to.
replacing "defaults,noatime" with "defaults,noatime,user" will probably do the trick. If not, do a ```
sudo chown -R (your username) /directory/of/choice
```

---

### Post by Jonners59 on 2010-12-02
OK, this is becoming an absolute mess...  How do I start again....?

I have 3 hard drives and want to share with other users on the LAN (and VPN when I get to that point) 1 partition on one and 6 on the other....

---

### Post by CharlesA on 2010-12-02
The main hurtle will be that you'd have to have a mountpoint for each of the partitions. It can be anywhere, so you can make it in /media/ or /mnt/ or /some/folder/, if you want them to be organized.

The advice that Morbius gave you is fine.

Check [here]("https://help.ubuntu.com/community/Fstab") for info on what to put in fstab.

---

### Post by Jonners59 on 2010-12-02
> **CharlesA said:**
> The main hurtle will be that you'd have to have a mountpoint for each of the partitions. It can be anywhere, so you can make it in /media/ or /mnt/ or /some/folder/, if you want them to be organized.

The advice that Morbius gave you is fine.

Check [here]("https://help.ubuntu.com/community/Fstab") for info on what to put in fstab.
OK, been through this and even changes the mount points to reflect the actual partition label...  I can mount and view from my PC (server), but still unable to share them with either the virtual machine or other PCs/Laptops on the LAN!!!!!!!

---

### Post by CharlesA on 2010-12-02
It doesn't sound like it's a problem with the partitions being mounted, since you are able to access those partitions from the host.

---

### Post by Morbius1 on 2010-12-02
Go back to your other post and see if you can recreate whatever you did to get samba working back then.

As I recall your network consists of 2 routers, 2 switches, and who knows what else. I'm afraid this is beyond my pay grade ( if you're familiar with that expression).

---

### Post by Jonners59 on 2010-12-14
> **Morbius1 said:**
> Go back to your other post and see if you can recreate whatever you did to get samba working back then.

As I recall your network consists of 2 routers, 2 switches, and who knows what else. I'm afraid this is beyond my pay grade ( if you're familiar with that expression).
NOTHING is working...  I'm fed up.

---

### Post by Jonners59 on 2010-12-28
I have just installed 10.10 on a MS Windows XP machine using the CD

I have tried to create auto mounting for two FAT32 Directories; "DOCUMENTS" and "BACKUP"

I have created the mount points and updates fstab.cfg file, see below for entire text.  BUT the directories will not mount.  During the Boot I get a message stating that they were "unable to mount select S to Skip or M to manual mount.."..  The splash screen is sometimes slow enouph for me to read something like "do not have privileges to mount drive, need root..".. or something like that.  Difficult to read as it is quick, and has only shown up twice so far.

[HTML]
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
# Commented out by Dropbox
# UUID=f265dd6c-2e08-4943-bb50-c2e0889cb6bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=05a67348-47a1-43e4-9d95-cb937d86d60a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=f265dd6c-2e08-4943-bb50-c2e0889cb6bd / ext4 errors=remount-ro,user_xattr 0 1
/dev/sdb5 /media/Documents      vfat     defaults,noatime,user,nls=utf8,umask=000,gid=46     0 0
/dev/sdb1 /media/Applications      vfat     defaults,noatime,user,mask=000,fmask=111,gid=46     0 0
UUID=f352e8f1-f335-4dc4-b55b-0e2be6ca90b3 / ext4 errors=remount-ro,user_xattr 0 1[/HTML]

Can anyone help, please?

---

### Post by Morbius1 on 2010-12-28
> /dev/sdb5 /media/Documents      vfat     defaults,noatime,user,nls=utf8,umask=000,gid=46     0 0
/dev/sdb1 /media/Applications      vfat     defaults,noatime,user,[COLOR=Blue]mask=000[/COLOR],fmask=111,gid=46     0 0
The first line is OK but the second one is not:
There is no such option as "mask" it's "umask" and you really don't use umask and fmask in combination you use dmask and fmask in combination. The second thing is the use of "user" in the line. I know it's popular in this forum but it's not going to do anything because the only user at the time fstab is executed is root. So I would change the line to look like this:
```
/dev/sdb1 /media/Applications      vfat     defaults,noatime,dmask=0000,fmask=0111,gid=46     0 0
```BTW, when you make changes to fstab you can unmount the like you changed, for example:
```
sudo umount /media/Applications
```Then instruct the system to mount all over again with a :
```
sudo mount -a
```It will save you a reboot plus it will display any errors that are too fast to reed at boot time.

---

### Post by Jonners59 on 2010-12-28
Cheers Morbius
I'll have a bash at this tomorrow

---

### Post by matt_symes on 2010-12-28
Hi

```
UUID=05a67348-47a1-43e4-9d95-cb937d86d60a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
**UUID=f265dd6c-2e08-4943-bb50-c2e0889cb6bd / ext4 errors=remount-ro,user_xattr 0 1**
/dev/sdb5 /media/Documents      vfat     defaults,noatime,user,nls=utf8,umask=000,gid=46     0 0
/dev/sdb1 /media/Applications      vfat     defaults,noatime,user,mask=000,fmask=111,gid=46     0 0
**UUID=f352e8f1-f335-4dc4-b55b-0e2be6ca90b3 / ext4 errors=remount-ro,user_xattr 0 1**
```

You are trying to mount two root partitions. Do you really want to be doing that? 

What are the two partitions with UUID's of....

f265dd6c-2e08-4943-bb50-c2e0889cb6bd and f352e8f1-f335-4dc4-b55b-0e2be6ca90b3 ?

Kind regards

---

### Post by Jonners59 on 2010-12-29
OK
That worked they both mount, where-as before neither mounted.  I assume it was the mode change that did it.  fstab now looks like this:

[HTML]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
# Commented out by Dropbox
# UUID=f265dd6c-2e08-4943-bb50-c2e0889cb6bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=05a67348-47a1-43e4-9d95-cb937d86d60a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=f265dd6c-2e08-4943-bb50-c2e0889cb6bd / ext4 errors=remount-ro,user_xattr 0 1
/dev/sdb5 /media/Documents      vfat     defaults,noatime,dmask=0000,fmask=0111,gid=46     0 0
/dev/sdb1 /media/Applications      vfat     defaults,noatime,dmask=0000,fmask=0111,gid=46     0 0
UUID=f352e8f1-f335-4dc4-b55b-0e2be6ca90b3 / ext4 errors=remount-ro,user_xattr 0 1[/HTML]

> Matt Quote
You are trying to mount two root partitions. Do you really want to be doing that? I don't know.  All I want to do is get the two partitions (and SWAT) to auto mount at start up....

> Matt Quote
What are the two partitions with UUID's of....

f265dd6c-2e08-4943-bb50-c2e0889cb6bd and f352e8f1-f335-4dc4-b55b-0e2be6ca90b3 ?f265dd6c-2e08-4943-bb50-c2e0889cb6bd = Ubuntu install

f352e8f1-f335-4dc4-b55b-0e2be6ca90b3 = is a partition I setup to install GRUB (I have been having conflicting Grub issues on another machine and thought I would try creating a special place for it), but it did not work, so is a spare that I may well just delete.

---

