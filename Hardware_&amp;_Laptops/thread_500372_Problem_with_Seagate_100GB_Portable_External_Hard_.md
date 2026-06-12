---
title: "Problem with Seagate 100GB Portable External Hard Drive"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by Elf on horseback on 2007-07-13
Note I am a total Ubuntu newbie been working on it for less then 24 hours so far

My problem is I can't mount my  Seagate 100GB Portable External Hard Drive ([link]("http://www.amazon.com/Seagate-Portable-External-Drive-ST9100801U2-RK/dp/B0006TIF2K/ref=pd_bbs_6/103-1278100-6146224?ie=UTF8&s=electronics&qid=1184349577&sr=8-6"))  
I have looked all over Ubuntu forums and google and I can't find what I am doing wrong.

I am running Feisty Fawn, full install, so no Windows.
Its on a Sony FS-980 laptop.  

i have looked at this thread ([http://ubuntuforums.org/showthread.php?t=390147](http://ubuntuforums.org/showthread.php?t=390147)) and i tried going in to ```
gksudo gedit /etc/fstab
``` and adding the following code to the very end of the file
```

/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0  0
/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0  0
```

Then  I tried to mount the drive using,
```
sudo mkdir /media/hda1 /media/sda1
sudo mount -a
df -h
```

But I got the following error message

```
mkdir: cannot create directory `/mnt/harddrive': Permission denied
```

But using the following command I can see the following info
```

~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12161    97683201    c  W95 FAT32 (LBA)

```

The 100GB is my external and the 80GB is my internal HDD

I posted about as much info I hope helped, and thanks for any help.

---

### Post by lisati on 2007-07-13
Could be 'coz the external drive ifat32 There are a couple of workarounds but the relevant links elude me for the moment.

---

### Post by merlinus on 2007-07-13
As lisati said, (paraphrase) you are trying to mix apples and oranges.

Can you post:

```

cat /etc/fstab

```-merlin

---

### Post by Elf on horseback on 2007-07-13
```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ab0718ab-56db-446d-b847-521d79c0ef73 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b531b069-16bc-4186-a691-56e7984c3025 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/hda1   ntfs   nls=utf8,umask=0222    0       0
/dev/sda1       /media/sda1   ntfs   nls=utf8,umask=0222    0       0

```

All I really want to do is be able to access the info on the HDD.  about 70GB of dif things on there, way too much for burning to DVDs.  After I get the info off I can format the HDD (not sure how to do that either).  Thank you so much for the fast replys.

---

### Post by merlinus on 2007-07-13
Delete this line from /etc/fstab:

/dev/sda1 /media/sda1  ntfs  nls=utf8,umask=0222 0 0

sda1 is already mounted as /

then change

/dev/hda1 /media/hda1   ntfs   nls=utf8,umask=0222 0 0

to

/dev/hda1 /media/hda1 vfat [B]iocharset=utf8,umask=000 0 0

[/B] You can edit the file by entering this in a terminal:

```

gksudo gedit /etc/fstab

```You may also need to create the mountpoint:

```

sudo mkdir /media/hda1

```

Restart, and see what happens.  If the drive mounts, you should find it via Nautilus in

filesystem/media/hda1

-merlin

---

### Post by Elf on horseback on 2007-07-13
first i changed the code you told me to

next i tried   and I got 
```
mkdir: cannot create directory `/media/hda1': File exists
```
so I moved on to the last step

when I went in to gconf-editor and I did not see the HDD in question.  If thats not where you ment, thats what google / ubuntu forum told me was Nautilus.  All that was listed there was 
Apps
Desktop
Schemas
System

thats it.

---

### Post by merlinus on 2007-07-13
You are looking at the gconf editor, not Nautilus, which is the default file manager.

Try:

 Places/Home Folder/File System/media/hda1.

-merlin

---

### Post by hardyn on 2007-07-13
Fat32 works just fine...

you have something interesting going on with  sda2 and sda5, two paritions occupying the same space... but we'll assume this isn't your trouble.

generally you do not have to add anything to the fstab file, and it will be detected an mounted automatically.
im pretty sure your trouble is in the fstab file, could you please post the whole fstab file?

remember that in feisty the drives are sda, so your hda statement isn't likely going to work; and if you are adding sda statements below sda statements, im sure that is going to play havoc with things as well.

---

### Post by Elf on horseback on 2007-07-13
Tried:
Places/Home Folder/File System/media/hda1.
and there was nothing in that folder and I did have the HDD hooked up

---

### Post by merlinus on 2007-07-13
Yep, hardyn is right.  You will have to change hda1 to sdb1 in /etc/fstab.

-merlin

---

### Post by Elf on horseback on 2007-07-13
cat /etc/fstab is
```
~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ab0718ab-56db-446d-b847-521d79c0ef73 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b531b069-16bc-4186-a691-56e7984c3025 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /media/hda1 vfat iocharset=utf8,umask=000 0 0
/dev/sda1       /media/sda1   ntfs   nls=utf8,umask=0222    0       0

```
If thats not it please tell me what to do.

---

### Post by merlinus on 2007-07-13
Change the hda1 line to :

/dev/sdb1 /media/sdb1 vfat iocharset=utf8,umask=000 0 0

and delete the /dev/sda1 line (the last line)

You may need to create the mountpoint:

```

sudo mkdir /media/sdb1

```but try rebooting after editing /etc/fstab.

-merlin

---

### Post by Elf on horseback on 2007-07-13
ok I still get 
```
mkdir: cannot create directory `/media/sdb1': File exists
```

my cat /etc/fstab now reads

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ab0718ab-56db-446d-b847-521d79c0ef73 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b531b069-16bc-4186-a691-56e7984c3025 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /media/hda1 vfat iocharset=utf8,umask=000 0 0
/dev/sdb1 /media/sdb1 ntfs nls=utf8,umask=0222 0 0
```

is there some way i can run this drive through an ubuntu to just "fix the formating" but keep the info on it?

---

### Post by merlinus on 2007-07-13
> 
/dev/hda1 /media/hda1 vfat iocharset=utf8,umask=000 0 0
/dev/sdb1 /media/sdb1 ntfs nls=utf8,umask=0222 0 0


Change the first line to:

/dev/sdb1 /media/sdb1 vfat iocharset=utf8,umask=000 0 0

and delete the last line.

AFAIK, formatting will destroy all data.

-merlin

---

### Post by Elf on horseback on 2007-07-14
ok after tring and trying again i keep failing so i'm just going to go to another PC and move all the info to DVDs, whats the best way to format it and what would I use to do the formating with?

BTW fstab is 
```
/dev/sdb1 /media/sdb1 vfat iocharset=utf8,umask=000 0 0
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ab0718ab-56db-446d-b847-521d79c0ef73 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b531b069-16bc-4186-a691-56e7984c3025 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /media/hda1 vfat iocharset=utf8,umask=000 0 0
```

---

### Post by merlinus on 2007-07-14
Once again, the last line of your fstab is incorrect.  Please look over my last few posts to see what it should be.

hda1 needs to be changed to sb1, according to the results you posted from:

sudo fdisk -l

If you are wanting to format the drive, you can use the gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If you are wanting to use the drive for sharing files between windows and ubuntu, you can format it as ntfs, and then install ntfs-3g to write to it from ubuntu.

-merlin

---

### Post by Elf on horseback on 2007-07-14
my fstab looks like```
 /dev/sdb1 /media/sdb1 vfat iocharset=utf8,umask=000 0 0
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ab0718ab-56db-446d-b847-521d79c0ef73 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b531b069-16bc-4186-a691-56e7984c3025 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sb1 /media/hda1 vfat iocharset=utf8,umask=000 0 0

```
what next, still not working and there already is a folder at /media/sb1 and it will not let me delete it.

---

### Post by Elf on horseback on 2007-07-14
correction this is my fstab
```
/dev/sdb1 /media/sdb1 vfat iocharset=utf8,umask=000 0 0
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ab0718ab-56db-446d-b847-521d79c0ef73 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b531b069-16bc-4186-a691-56e7984c3025 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sb1 /media/sb1 vfat iocharset=utf8,umask=000 0 0

```

---

### Post by merlinus on 2007-07-14
Can yous see the folder (File System/media/sb1) in Nautilus?  Is there anything in it?

-merlin

---

### Post by Elf on horseback on 2007-07-14
I rebooted and opened up /media/sb1 and there is nothing in that folder.  Thats also with the HDD attached and on

---

### Post by merlinus on 2007-07-14
What is the output of:

```

mount

```

-merlin

---

### Post by Elf on horseback on 2007-07-14
mount output is the following```

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
```

---

### Post by Elf on horseback on 2007-07-14
fstab is ```

$ cat /etc/fstab
/dev/sdb1 /media/sdb1 vfat iocharset=utf8,umask=000 0 0
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ab0718ab-56db-446d-b847-521d79c0ef73 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b531b069-16bc-4186-a691-56e7984c3025 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sb1 /media/sb1 vfat iocharset=utf8,umask=000 0 0
```

---

### Post by merlinus on 2007-07-14
Clearly your external drive is not mounted, despite being referenced in /etc/fstab.  Let's try to do it manually:

```

sudo mount /dev/sdb1 /media/sdb1 -t vfat -o umask=000

```

Then look for it with Nautilus.

-merlin

---

### Post by Elf on horseback on 2007-07-14
ohh my gosh, it worked, thank you so very much merlin for sticking with me to get this done.  I can't say thank you enough.  Do you have any idea what i should do next, given i am just starting out on Ubuntu?

---

### Post by bluknight on 2007-07-14
If you do not want to edit /etc/fstab (which is dynamically maintained by the system), leave everything as it is and start an application called kwikdisk (under system monitoring). If you see /dev/sdb2 among the listed media then on a terminal just type:
sudo mkdir /mnt/sdb2
sudo mount /dev/sdb2 /mnt/sdb2

and youre all set.

---

### Post by Elf on horseback on 2007-07-14
after that this seems like a stupid question, how do i put a short cut on my desktop for that folder

---

### Post by merlinus on 2007-07-15
First of all, go to System/Preferences/Removable Drives and Media and make sure the appropriate boxes are ticked.

Then:

Alt-F2
gconf-editor
apps/Nautilus/desktop

Tick the box for volumes_visible.

-merlin

---

### Post by Elf on horseback on 2007-07-15
When I booted up my laptop this morning I went in to System/Preferences/Removable Drives and Media and found the following boxes already ticked

- Mount removable drives when hot-plugged
- Mount removable media when inserted
- Browse removable media when inserted

and when i went in to gconf-editor, the box for volumes_visible was already ticked.  Also there is not one icon on my desktop.  Yet, I seem to remember a filesystem icon on my desktop when I ran the live CD, its not there now . . .

---

### Post by merlinus on 2007-07-15
Did you check gconf-editor --

apps/Nautilus/desktop 

to make sure the various boxes were ticked?

Also, you can make a launcher on the desktop that will open that partition in Nautilus.

Right-click on the dekstop, Select create launcher.

Name it whatever you wish.

For command:

nautilus /media/sdb1

-merlin

---

### Post by Elf on horseback on 2007-07-15
i unpluged it and it stop showing up, so i rebooted and it shows up again.  I am taking all the info I need and putting it on my laptop HDD.  when i get done with that I am just going to reformat it NTFS and install that NTFS plug in for Ubuntu and I'm hopping that will make it so i can just plug it in and it pops up, I hope

---

### Post by Elf on horseback on 2007-07-15
I have gotten it to the point that i plug it in and it comes up on my desktop.  But it will not let me write to the drive i get the following error message
```
Error while copying to "/media/disk".
You do not have permissions to write to this folder.
```

My fstab reads at the moment
```
UUID=###########    /media/sda1     auto     defaults     0     0
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ab0718ab-56db-446d-b847-521d79c0ef73 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b531b069-16bc-4186-a691-56e7984c3025 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sb1 /media/sb1 vfat iocharset=utf8,umask=000 0 0
```
any ideas?

---

### Post by merlinus on 2007-07-16
Interesting, because according to /etc/fstab is is mounted as /media/sdb1.

(I assume you are referring to your fat partition?)

You might try this:

```

sudo chown -R username:username /media/sdb1

```

and

```

sudo chown -R username:username /media/disk

```

username is your login id

-merlin

---

### Post by Elf on horseback on 2007-07-16
just so you know, it is not a fat32 drive any more.  i got it up and running long enough to remove the data i had on there.  then i used gpart and formated it off the live CD.  then i installed NTFS-3G and thats where i am at right now. There a better format, to format my drive with?

---

### Post by Elf on horseback on 2007-07-16
i ran the code you asked me to and 
```
sudo chown -R username:username /media/sdb1
```
came out okay

```
:~$ sudo chown -R will:will /media/disk
chown: changing ownership of `/media/disk': Read-only file system
```
had that error

---

### Post by merlinus on 2007-07-16
At this point, I suggest you backup the data and format the drive as ntfs.  It may be that vfat does not deal well with permissions.

Keep me posted....

-merlin

---

### Post by Elf on horseback on 2007-07-16
last night i did get the vfat working and the new problem is with NTFS, that kinda the problem, i cant right to the NTFS part now, i can see it but i can write to it.

---

### Post by merlinus on 2007-07-16
```

sudo apt-get install ntfs-3g ntfs-config

```then:

```

sudo ntfs-config

```Tick the appropriate boxes, and reboot.

-merlin

---

### Post by Elf on horseback on 2007-07-16
I installed NTFS-3g and config ed it.  then i looked in gpart for ubuntu and i was i messed up theformating and it is ext3 part and it grays out NTFS.  as in i can't do NTFS

---

### Post by merlinus on 2007-07-16
Maybe we need to do a review....

How is the external drive formatted?

Please explain further about the gparted portion of your last post?

If you are wanting to format the external as ntfs, then it has to be unmounted first in order for gparted to work.

-merlin

---

### Post by Elf on horseback on 2007-07-16
the external drive now works and i can write to it.  the problem seems to be I was trying to use Gpart from Ubuntu not the live CD.  I stuck in the live CD and it let me do the part in NTFS (still don't get why i cant use it in Ubuntu to format it NTFS).  So i am hopeing that will do it for the external hard drive, thank you again for your time and engery you put in to this merlin.

---

### Post by merlinus on 2007-07-16
Great news!  Glad it is working.

I believe the reason gparted in ubuntu could not format the drive is because it was mounted and in use.  

That's why I use the gparted live cd to do all of my formatting and partitioning.

All the best...

-merlin

---

