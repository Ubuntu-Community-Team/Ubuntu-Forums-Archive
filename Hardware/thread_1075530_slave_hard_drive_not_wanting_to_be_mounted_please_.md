---
title: "slave hard drive not wanting to be mounted please help"
date: 2009-02-20
forum: Hardware
---

### Post by aiden707 on 2009-02-20
hi
i have ubuntu server 8.10 with xubuntu desktop installed, i bought a second hand hard drive on ebay which is set up and fine in my bios, (also i tried reinstalling ubuntu server and the instalation process recogized the drive and gave me the option to use it for the installation) I didnt install on it as i want it to be installed useing ntfs so i can use samba to share it with a windows client pc. i have tried useing "mount manager 0.2.4" i can see the hdd in the file tree but have no option to do anything just see info:
type :disk
product:ST380011A
major:8
minor:16
 so i followed these instructions useing the command line
** I suggest you format the 250Gb volume as ext3 instead of ext2 **

1. Create a folder, where you want to mount your 250 GB volume
Code:

sudo mkdir /media/Data

2. Connect the drive to your PC and find the device name using
Code:

sudo fdisk -l

* I assume fdisk reports the new 250 GB volume as /dev/hdb1

3. Edit /etc/fstab
Code:

gksudo gedit /etc/fstab

4. Add this line to the end of the file
Code:

/dev/hdb1  	/media/Data  	ext3  	defaults  	0 2

5. Save and Exit.

6. To mount the new partition, type
Code:

sudo mount -a

If this works, the partition should mount automatically next time you reboot.

7. /media/Data will be owned by root. If you would like to change that
Code:

sudo chown -R user_name:group_name /media/Data

* Usually group_name is same as your user_name

Now, create a shortcut in your $HOME directory to /media/Data.

EDIT: Be sure to change /dev/hdb1 to whatever appropriate in your set up, as reported by fdisk from Step 2.
__________________
all this works fine i know what my hdd is called (dev/sdb) so changed that bit in gedit but when save the line
/dev/sdb  	/media/Data  	ext3  	defaults  	0 2
and when i type sudo mount -a
get this message:

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

so i tried in gedit again with:
/dev/sdb        /media/Data     ntfs    defaults       0  2

bu got this error:

The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

i know i am useing right /dev/sdb/ cos it called that in mount manager and when i use "sudo fdisk -l" cos the drive is second hand i dont know what file system is on it>If there is a way to format the drive to make mounting easyier thats fine, please any help greatly apreciated as i cant find the answer on forum posts.

---

### Post by taurus on 2009-02-20
Post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
id
```
By the way, you have to use /dev/sdb1 instead of /dev/sdb if you want to mount your second harddrive.

---

### Post by aiden707 on 2009-02-20
ok 
sudo fdisk -l      gets this:
@ubuntuX:~$ sudo fdisk -l

Disk /dev/sda: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10371037

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2382    19133383+  83  Linux
/dev/sda2            2383        2491      875542+   5  Extended
/dev/sda5            2383        2491      875511   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d4d4d4c

   Device Boot      Start         End      Blocks   Id  System

and sudo blkid     gets this:

a@ubuntuX:~$ sudo blkid
/dev/sda1: UUID="eecaf6d2-c48e-437a-906b-7cc76f34c984" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="306db6dd-136a-463b-967c-adae1f52fe24" 

cat /etc/fstab         gets this :

ubuntuX:~$ cat /etc/fstab

UUID=eecaf6d2-c48e-437a-906b-7cc76f34c984 / ext3 defaults 0 1
UUID=306db6dd-136a-463b-967c-adae1f52fe24 swap swap sw 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 noauto 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 noauto 0 0

df -h          get this;
@ubuntuX:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G  3.4G   14G  20% /
tmpfs                 973M     0  973M   0% /lib/init/rw
varrun                973M  304K  972M   1% /var/run
varlock               973M     0  973M   0% /var/lock
udev                  973M  2.8M  970M   1% /dev
tmpfs                 973M     0  973M   0% /dev/shm


id gets this ;
@ubuntuX:~$ id 
uid=1000(a) gid=1000(a) groups=4(adm),20(dialout),24(cdrom),46(plugdev),111(sambashare),115(lpadmin),116(admin),1000(a)

thanks for trying to help

---

### Post by taurus on 2009-02-20
> **aiden707 said:**
> 
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d4d4d4c

   Device Boot      Start         End      Blocks   Id  System


You have not create a partition and format your second harddrive, 80GB.  Therefore, you need to do that first before you can use it.  One option is to install gparted.  Then, run gparted and create a new partition on /dev/sdb (/dev/sdb1) that takes up the whole disk space and format it to ext3.

```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```
Once all of that is done, then you can add an entry in /etc/fstab to have it mount automatically each time you boot.

---

### Post by aiden707 on 2009-02-20
ok thanks will do that but with gparted can i format in ntfs? cos would prefer so my windows pc can then also use it.

---

### Post by Therion on 2009-02-20
> **aiden707 said:**
> ok thanks will do that but with gparted can i format in ntfs?
Yes, you can.

---

### Post by aiden707 on 2009-02-20
ok i have used gparted to make the partion in ntfs(and it worked as it shows up in mount manager) so in gedit /etc/fstab    i put this line:
/dev/sdb1 /media/Data                     /ntfs defaults 0 2 
but after reboot cant see HDD i very new to ubuntu but think cant see it cos made a mistake in this line ( or could be i dont know where /media/Data is located!)
/dev/sdb1 /media/Data                     /ntfs defaults 0 2

---

### Post by taurus on 2009-02-20
I would make the entry for /dev/sdb1 (ntfs filesystem) to look like this in /etc/fstab, assuming you're in the US.

```
/dev/sdb1   /media/Data   ntfs-3g  defaults,locale=en_US.UTF-8  0  0
```

Then, make sure you have created that new mount point or it won't be able to mount it.

```
sudo mkdir /media/Data
sudo mount -a
df -h
```

---

### Post by aiden707 on 2009-02-20
ok  in gedit /etc/fstab put your line :
/dev/sdb1   /media/Data   ntfs-3g  defaults,locale=en_US.UTF-8  0  0

then in the terminal typed :
sudo mount -a
 which worked cos i didnt get an error message, have rebooted but cant find the mounted place /media/Data

---

### Post by taurus on 2009-02-20
```
sudo fdisk -l
df -h
```

---

### Post by aiden707 on 2009-02-20
sorry been stareing at screen for too long missed your last set of instructions have done now and looked like this :
@ubuntuX:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G  3.4G   14G  20% /
tmpfs                 973M     0  973M   0% /lib/init/rw
varrun                973M  300K  972M   1% /var/run
varlock               973M     0  973M   0% /var/lock
udev                  973M  2.8M  970M   1% /dev
tmpfs                 973M     0  973M   0% /dev/shm
/dev/sdb1              75G   67M   75G   1% /media/Data
 am rebooting now

---

### Post by aiden707 on 2009-02-20
ok sorry didnt read all your instructions at first have done all and rebooted in terminal got this :
a@ubuntuX:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G  3.4G   14G  20% /
tmpfs                 973M     0  973M   0% /lib/init/rw
varrun                973M  300K  972M   1% /var/run
varlock               973M     0  973M   0% /var/lock
udev                  973M  2.8M  970M   1% /dev
tmpfs                 973M     0  973M   0% /dev/shm
/dev/sdb1              75G   67M   75G   1% /media/Data
a@ubuntuX:~$ 


so i can see it is mounted somewhere just i cant find cos i new to linux

---

### Post by taurus on 2009-02-20
> **aiden707 said:**
> ok sorry didnt read all your instructions at first have done all and rebooted in terminal got this :
a@ubuntuX:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G  3.4G   14G  20% /
tmpfs                 973M     0  973M   0% /lib/init/rw
varrun                973M  300K  972M   1% /var/run
varlock               973M     0  973M   0% /var/lock
udev                  973M  2.8M  970M   1% /dev
tmpfs                 973M     0  973M   0% /dev/shm
**[COLOR="Blue"]/dev/sdb1              75G   67M   75G   1% /media/Data[/COLOR]**
a@ubuntuX:~$ 

so i can see it is mounted somewhere just i cant find cos i new to linux

/dev/sdb1 is now mounted to /media/Data.  If you want to access /dev/sdb1, you need to use its mount point--/media/Data.

```
ls -la /media/Data
```

---

### Post by aiden707 on 2009-02-20
ok found out where media/data is mounted took a while still getting used to linux way.  thanks a lot for your help
aiden

---

### Post by taurus on 2009-02-20
Keep in mind that Unix/Linux is case sensitive so /media/Data is _not_ the same as /media/data.

---

### Post by aiden707 on 2009-02-20
will remeber that thanks

---

