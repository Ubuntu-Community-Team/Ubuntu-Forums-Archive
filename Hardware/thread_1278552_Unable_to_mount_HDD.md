---
title: "Unable to mount HDD"
date: 2009-09-29
forum: Hardware
---

### Post by Quintino on 2009-09-29
Hello everyone,

I tried to find my answer on some older post, but I wasn't successful.
I got an issue when I try to mount my internal HDD. Actually I boot ubuntu from my usb key.
The first time I was able to access my hard drive (with XP on it...). I used some progams to watch some videos. I shut down my computer and since I restarted it I can't mount it anymore.
The error message says: " unable to mount the volume 'HDD'. Details mount: according to mtab,/dev/sda1 is already mounted  on /media/HDD "

I got the exact same problem with my external hard drive : "unable to mountthe volume 'HDD Portable Quentin' Details mount : according to mtab,/dev/sdc1 is already mounted on media/HDD Portable Quentin ". I remember that I used Rhythmbox to listen to music on this hard drive.

Thank you for help. If by any chance, you would know how to avoid such troubles in the future, I would be glad to take your advice.

---

### Post by AlanQ on 2009-09-29
Ubuntu will detect and try to mount drives that it finds.
Can you confirm that your HD _is_ mounted on /media/HDD ?

---

### Post by Quintino on 2009-09-29
Sorry, I'm newbie, 
how to confirm that it is mounted on /media/HDD?

---

### Post by AlanQ on 2009-09-29
Applications > Accessories > Terminal

At the prompt type df and press <Return/Enter>

Do you see /dev/sda1 under Filesystem and /media/HDD under Mounted on ?

---

### Post by Quintino on 2009-09-30
I don't think I see that. Here is what i see:

> ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                  1030928      2392   1028536   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                  1030928      2392   1028536   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                  1030928         0   1030928   0% /lib/init/rw
varrun                 1030928       112   1030816   1% /var/run
varlock                1030928         0   1030928   0% /var/lock
udev                   1030928       148   1030780   1% /dev
tmpfs                  1030928       624   1030304   1% /dev/shm
rootfs                 4031680   3684368    142512  97% /
/dev/sdb1              7812148   4811680   3000468  62% /cdrom
/dev/loop0              691328    691328         0 100% /rofs
tmpfs                  4031680   3684368    142512  97% /tmp
df: `/media/HDD': No such file or directory
tmpfs                  1030928      2392   1028536   1% /lib/modules/2.6.28-11-generic/volatile
df: `/media/HDD Portable Quentin': No such file or directory
tmpfs                  1030928      2392   1028536   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                  1030928      2392   1028536   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                  1030928      2392   1028536   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                  1030928      2392   1028536   1% /lib/modules/2.6.28-11-generic/volatile


---

### Post by AlanQ on 2009-09-30
Three things:

1) Exactly what are you typing when you try to mount a hard disk?
   What exactly is the error message?

2) As you did with the output of **df**, please post the output from 
   **cat /etc/fstab** and **cat /etc/mtab**.

3) Start the Synaptic Package Manager
   (System > Administration > Synaptic Package Manager)
   In the package list, find **nfsbooted**.
   Right-click nfsbooted and click **Properties**.
   What does it say next to **Status:** ?

---

### Post by Quintino on 2009-10-01
1) When I try to mount a disk, I just left-click on it, or I right-click and then select "mount volume"

2) for cat /etc/fstab, here is what the console says:
>  ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0and for cat /etc/mtab:
> ubuntu@ubuntu:~$ cat /etc/mtab
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
rootfs / rootfs rw 0 0
/dev/sdb1 /cdrom vfat rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sda1 /media/HDD fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sdc1 /media/HDD\040Portable\040Quentin fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ubuntu 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/fuse /home/ubuntu/.gvfs fuse rw,nosuid,nodev,user=ubuntu 0 03) synaptic package manager tells me that "nfsbooted" is not installed

Hope it'll help, thanks a lot

---

### Post by Quintino on 2009-10-02
So shall I install nfbooted?

---

### Post by AlanQ on 2009-10-02
Hi Quintino, sorry for the delay.

> So shall I install nfbooted?
No. nfbooted can _cause_ problems like the one you are experiencing.

To explain my thoughts here:
/etc/fstab is the file that tells the computer what disks and filesystems to mount. Yours is surprisingly sparse.
/etc/mtab shows the disks and filesystems that are currently mounted.

These two lines in your mtab are interesting:
```
/dev/sda1 /media/HDD fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

/dev/sdc1 /media/HDD\040Portable\040Quentin fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

```

Start a terminal again (Applications > Accessories > Terminal).
Type **cat /etc/mtab** <Enter/Return> and make sure that those two lines are still there.
Then type **ls -al /media/HDD**. What is the output?
(Don't forget that filenames in Ubuntu are case-sensitive -- *hdd* is _not_ the same as *HDD*).

---

### Post by cmcanulty on 2009-10-02
I am having similar problem can't mount flash drives ext HD or anything have tried all file systems, numerous tweaks, terminal commands, ntfs-3g, ntfs config tool, storage device manager,nfs booted, I am totally frustrated. I can't evemn reinstall as I lost all my backups trying to fix ext drives. Everything works in a windows machine so hardware is OK

---

### Post by AlanQ on 2009-10-02
cmcanulty:

What happens when you issue a mount command (with and without sudo) from a terminal prompt?

Do you have problems even trying to mount GNU/Linux native filesystems (eg ext3) or only when trying to mount FAT and NTFS?

Can you mount CDs?

>...trying to fix ext drives.
What was your attempted fix?

---

### Post by cmcanulty on 2009-10-02
Yes I can mount CDs but not ntfs, fat 32, ext3, flash drives, ext HDs. Rarely something mounts for a few minutes and then unmounts. If I only could get a decent backup (impossible without mounts) I would do a clean reinstall but I have 81GB I can't lose. I lost backups on 2 ext HDs trying to fix this.

---

### Post by AlanQ on 2009-10-02
Looks like the things you can't mount are all connecting via USB.
Could be software if you're a tweaker, but I suspect hardware.
Have you tried all of the USB ports on your machine?
Might be worth installing a USB PCI card.
eg [http://www.amazon.co.uk/Belkin-USB-Hi-Speed-5-Port-Card/dp/B000K7UN82/ref=dp_cp_ob_ce_title_0](http://www.amazon.co.uk/Belkin-USB-Hi-Speed-5-Port-Card/dp/B000K7UN82/ref=dp_cp_ob_ce_title_0)

I'm guessing you just have one Ubuntu partition for **/** (apart from swap).
If you had one for **/** and one for **/home** you could (carefully) reinstall the OS.

Do you have another machine to which you could transfer the files you need via you local ethernet network?

Alternatively, if the problem is software only, buy a new HD, install it into the machine and install Ubuntu.
Then put the HD with your important files into a hard disk drive enclosure and access the files that way.
eg [http://www.amazon.co.uk/Belkin-Hi-Speed-External-Drive-Enclosure/dp/B0001GYNJ2](http://www.amazon.co.uk/Belkin-Hi-Speed-External-Drive-Enclosure/dp/B0001GYNJ2)

---

### Post by cmcanulty on 2009-10-03
I got backed up by using the live CD which would mount the ext HD so I am going to reinstall Ubuntu, do you suggest I try the beta Karmic or 9.04? Just hope I can get the wireless going again as that was a nightmare

---

### Post by AlanQ on 2009-10-04
Well that narrows it down to a software bug -- glad the live CD worked.

I'd suggest sticking with 9.04: even although a beta Ubuntu is most likely to be very stable, you don't want to be grappling with beta-bugs as well as any wireless difficulties.

Post back how you get on.
Good luck.
Alan

ps
What version did you have installed?
Which live CD did you use?

---

### Post by Quintino on 2009-10-05
when I type cat /etc/mtab, here is what i get:
> ubuntu@ubuntu:~$ cat /etc/mtab
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
rootfs / rootfs rw 0 0
/dev/sdb1 /cdrom vfat rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
**/dev/sda1 /media/HDD fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0**
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
**/dev/sdc1 /media/HDD\040Portable\040Quentin fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0**
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ubuntu 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/fuse /home/ubuntu/.gvfs fuse rw,nosuid,nodev,user=ubuntu 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0So these two lines still are there

2) when I type ls -al /media /HDD or ls -al/media/HDD

> ubuntu@ubuntu:~$ ls -al /media/HDD
ls: cannot access /media/HDD: No such file or directory
ubuntu@ubuntu:~$ ls -al /media/ HDD Portable Quentin
ls: cannot access HDD: No such file or directory
ls: cannot access Portable: No such file or directory
ls: cannot access Quentin: No such file or directory
/media/:
total 8
drwxr-xr-x  2 root root 4096 2009-10-05 14:40 .
drwxr-xr-x 35 root root 4096 2009-10-05 16:07 ..
-rw-r--r--  1 root root    0 2009-10-05 16:09 .hal-mtab
-rw-------  1 root root    0 2009-10-05 14:39 .hal-mtab-lock
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ ls -al /media/HDD\040Portable\040Quentin
ls: cannot access /media/HDD040Portable040Quentin: No such file or directory3) after having typed ls -al /media/HDD\040Portable\040Quentin, I've had another error message : 
> **Unable to mount HDD Portable Quentin**
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

---

### Post by AlanQ on 2009-10-05
[FONT="Courier New"]
First of all, do be careful what you type.
Both of these are wrong:
> when I type ls -al /media /HDD or ls -al/media/HDD

I know it's difficult when you're a newbie but do get into the habit of trying to understand a command before you type it. You can get into big trouble if you don't. It's at least partly my fault for not explaining what I was telling you to type.

Many (maybe most) commands follow the pattern [command] [options] [file].
The 'options' modify the behaviour of the command.

In the case of **ls -al /media/HDD**, 
The command is **ls** (_l_i_s_t the files in a folder)
The options are **a** and **l** (l = list with some detail, a = show all files)
The file is **/media/HDD**.
[/FONT]

Now, back to the problem...
(before we start, just a reminder, everything is case-sensitive -- '**I**' is not the same as '**i**')

Some more background information:
Back in *the good old days*, Unix/Linux/etc systems only mounted what the user told them to -- either directly via the mount command or semi-automatically via /etc/fstab.
Now their is auto-mounting, the HAL daemon, FUSE, and UUIDs. Most of the time they make life easier but, as with all automation and abstraction, sometimes it goes wrong.

The next thing to try is to see if you can manually unmount both drives and then mount them the way you want them.

To do this you will need to run the commands as *root* (otherwise known as *SuperUser*). You will use the **sudo** command to temporarily change your identity from ubuntu (an ordinary user) to root (the most powerful administrator). This means that you must be extra careful about what you type. root is (almost) all-powerful and can destroy everything!

Note:
In your listings I see **ubuntu@ubuntu:~$**.
The first **ubuntu** is your user name. The **ubuntu** after the **@** is the name of your computer. The **~** tells me that you are in your home directory (/home/ubuntu) and the **$** tells me that you are an ordinary user (you are not root).

To make sure the drives are unmounted:
```
sudo umount /dev/sda1
```
```
sudo umount /dev/sdc1
```

Yes, the command is **umount** not u_n_mount.

After the first command (sudo umount /dev/sda1) the system will prompt you (ask) for your password. Type in your usual password (the one you use to log in) and press <Enter/Return>. Nothing will be displayed as you type -- not your password or even asterisks (*).

Unless their is a big delay between typing each command, it will not prompt you for your password for the second command.

Type /cat/mtab again to make sure they have gone.

If they have, try to mount the internal drive:
We're going to avoid /media/HDD and create a new directory (folder) for the drive.
Type ```
sudo mkdir /media/InternalHD
```
sudo: temporarily become root
mkdir: _m_a_k_e _dir_ectory

Now type ```
sudo mount /dev/sda1 /media/InternalHD
```
mount: mount a device on a directory
/dev/sda1: the _dev_ice to mount
/media/InternalHD: the directory

Now type ```
mount
```
Should give the same output as **cat /etc/mtab**
Is /dev/sda1 mounted on /media/InternalHD ?

Try ```
ls -l /media/InternalHD
```
Can you see the files in your hard disk?

---

### Post by Rayve on 2009-10-06
AlanQ,

I'm having a similar problem, but I just wanted to say a quick thanks for the detailed response above.  Helped me understand quite a bit!

But I'm still not sure what to do with my external hard drive.  I'm currently running a very small Linux partition on my main Windows machine (about 18g through the Wubi setup, getting used to Linux and learning some before I switch completely at the end of the year), and the rest of my interal HDD is with Windows.  I have a Seagate external hard drive connected via a USB.  It is recognized in Windows, so I know it's just an issue with me learning how to mount it in Linux, but I'd like to use it to back things up.

I've read various entries in forums and online, and so far I've tried the following:

```
sudo mkdir /mnt/seagate1
sudo mount /dev/sdb1 /mnt/seagate1
```The make directory worked (I see [only] seagate1 when I do ls /mnt), but it wants to know the file type of my Seagate, which I have no clue about ... any ideas how I might find that out, and then how to mount from there?  Thanks!

Oh, I don't mind mounting it each time I start up.  I don't need it all the time, so I'd rather it not mount automatically.

EDIT: I think I managed to answer one question myself, heh.

Here's what I did: 

```
candice@ubuntu:~$ sudo fdisk -l
[sudo] password for candice: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04282ece

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1957    15719571    c  W95 FAT32 (LBA)
/dev/sda2   *        1958       60801   472664430    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8dff05d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    c  W95 FAT32 (LBA)
```Then I saw it said FAT32 by the only other hard drive that could be my external.  I looked it up to be sure that FAT32 = vfat for Linux purposes, so I didn't try to mount the wrong file type.  Then, I did

```
sudo mount -t vfat /dev/sdb1 /mnt/seagate1
```And it asked for my password, and now my mount command shows:

```
candice@ubuntu:~$ mount
/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/candice/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=candice)
/dev/sr0 on /media/Civ IV Complete type udf (ro,nosuid,nodev,uhelper=hal,uid=1000)
/dev/sdb1 on /mnt/seagate1 type vfat (rw)
```Yay, it's there!  Only thing is... I tried doing 

```
vim /etc/mtab 
```so I could edit it and make it noauto, but it said I was editing a read only file.  Do I just need to chmod, or is there something else I should do?

Also, I can do ls /mnt/seagate1 and I see all my files, but when I click on "Computer" in Places, it shows up as USB Drive and when I click on it, it says there is no media and it can't mount it.

---

### Post by AlanQ on 2009-10-07
Rayve
Well done finding out the format of your HDs, and thanks for your thanks.

On your last two questions.
**Don't do vim /etc/mtab**.
mtab shows what is currently mounted and should not be edited.

The file you want is **/etc/fstab**.
First of all, take a backup copy of /etc/fstab and put it somewhere safe.
Secondly, are you happy using vim? It takes some getting used to.
The reason it's opening read-only is because, being a system file, it's owned by root.
So, to edit it you need to type ```
sudo vim /etc/fstab
``` You can replace *vim* with *gedit* (GNU text editor).
[Note1: For anyone who needs telling -- Never edit text files with a word processor unless you really know what you are doing.
Note2: Ubuntu 9.04 appears to come with *vi* only, and not *vim* -- easily added from the repository.]

I would recommend that you add the new entry to the bottom of the file and precede it with an informative comment. Something like:
```
# Added by Ray 2009-10-07 to tell system that external USB HD is VFAT (FAT32) but stop it automounting.
/dev/sdb1    /mnt/seagate1    vfat    user,noauto    0    0
```

_Reading from left to right:_
*device*: /dev/sdb1
*mount point*: /mnt/seagate1
*file system type*: vfat
*mount options*:
  user = allow ordinary user to mount the disc
  (Don't need sudo to mount it. This should (might) solve your "no media and it can't mount it" problem)
  noauto = don't mount the device automatically when the system boots
*Instruction to dump*: 0 = don't backup this filesystem
*Instruction to fsck*: 0 = don't perform automatic checks on this filesystem
(type **man fstab** in a terminal for more details)

Once you've saved this file and exited the text editor (*<Esc>:wq* in vi or vim) type ```
mount -a
``` = mount _a_ll filesystems mentioned in /etc/fstab.

Now try ```
ls /mnt/seagate1
```
If you don't see the files on your Seagate drive, try ```
mount /dev/sdb1
``` or ```
mount /mnt/seagate1
``` It should recognise and respond correctly to either. This is what you will have to do each time you want to mount the drive from now on _OR_ by double-clicking *USB Drive* in *Places > Computer*.

Then **ls /mnt/seagate1** _OR_ open the drive under *Places*.

The next thing we can do is get clever and use UUIDs in /etc/fstab...

---

### Post by Rayve on 2009-10-09
AlanQ,

You're awesome. :)  I was able to mount the external HDD through editing /etc/fstab and see the contents via ls /mnt/seagate1, but it showed up as sdf1 instead of the sdb1 it was the other day - is that because I turned it off and then back on?  Will I need to check 

```
sudo fdisk -l
```

each time I start up Ubuntu and then edit /etc/fstab if the name has changed?  And should I have the external turned on before I do so, or is it okay to turn it on once in Ubuntu?

Also, it doesn't show up in "Places", that's why I'm thinking maybe it needs to be turned on before Ubuntu loads.

Thanks so much for your time and answers.

---

### Post by AlanQ on 2009-10-12
Thanks, Rayve -- Sorry for the delay -- I'm not awsome, just too school for cool.

The following is based upon my current understanding -- it may contain some small errors in detail but nothing major -- technical stuff I've done before after some research so I know it works. [COLOR="DarkRed"]I would be pleased for corrections to be posted here, however minor, from anyone following this thread.[/COLOR]

A little background on device names:
All devices such as hard disks need a location in /dev for them to be accessible.
Hard disks are typically either /dev/hd* (hda, hdb, hdc, etc) or /dev/sd*.
Historically, all hd were (typically) ATA drives (now called PATA to distinguish them from SATA).
And all sd were (typically) the faster SCSI disks.
But, the machine I'm using as I type this has an old PATA disk which is /dev/sda.

As I mentioned in post #17 of this thread, the simplicity of *mount what I tell you where I tell you* has been blurred by things like the automounter -- an attempt to turn the flexibility of Linux into the *everything is just there* of Windows. But I am surprised that it's overriding your /etc/fstab settings _and_ then not putting it in 'Places'. I have noticed that 9.04 isn't as 'stable' in this regard compared to 8.10 .

Turning-off-and-then-back-on is indeed most likely what is prompting an automount.

The *which /dev is it today?* problem that you have identified is solved using UUIDs that I mentioned in my last post:

/dev/sdb, for example, could be any hard disk attached to the system internally or externally.
So, if you swap your Windows formatted (FAT32/vfat) partition with a Linux formatted (ext3) one and it happens to be allocated by the kernel to /dev/sdb1, the line */dev/sdb1    /mnt/seagate1    vfat    user,noauto    0    0* in /etc/fstab will cause the system to try to mount it as FAT32, and fail.

A Universally Unique Identifier (UUID) does exactly what it says on the tin.
In the /etc/fstab file you can directly replace the */dev* part with *UUID=* .
The UUID of your FAT32 partition will be universally unique so, when following the instructions in /etc/fstab, Linux will only try to mount that *one-and-only-in-the-world* partition in the manner specified.
Depending upon which version of Ubuntu you have, if you look in /etc/fstab you should see automatically generated UUIDs for your main HD partition(s).

Next question, how to find the UUID of a partition.
```
sudo vol_id --uuid /dev/sdb1
```
The output will be a long string something like edaed3a2-6e84-41ad-c73a-2aa62a54c3b8 .
Now, in /etc/fstab, you can replace */dev/sdb1* with *UUID=edaed3a2-6e84-41ad-c73a-2aa62a54c3b8*

Then type *sudo mount -a* or reboot.
With luck you should find that when you plug in your drive with the FAT32 partition it is correctly mounted (it will still be assigned to a device file such as /dev/sdb1).

Good luck.

---

### Post by Quintino on 2009-10-13
Sorry for the long long delay. school & work for the last days, and it's only the beginning...
I used your method AlanQ and now I m able to access both my internal & external hard drives, so big big thanks for your attention

I still have some questions: when I used the sudo command, terminal didn't ask for a password like "root". Is it normal?
second, my external hard drive strangely and spontaneously changed location from /dev sdc1 to /dev/sdb1??? is it a bug?
To avoid such detection problems, shall I everytime unmount my internal & external harddrives before shutting down my computer?

I have other issues with Ubuntu, this time with my graphic card (Geforce 6200) & my external monitor pluged on VGA, so I think I'm gonna make a new post in the appropriate forum

---

### Post by Rayve on 2009-10-13
> **Quintino said:**
> 
I still have some questions: when I used the sudo command, terminal didn't ask for a password like "root". Is it normal?
second, my external hard drive strangely and spontaneously changed location from /dev sdc1 to /dev/sdb1??? is it a bug?
To avoid such detection problems, shall I everytime unmount my internal & external harddrives before shutting down my computer?


Quintino,

If you've just used the ```
 sudo 
``` command recently, it will not ask you for your password again.  If it's the first time you've used sudo in a while, then I'm all out of ideas.  

I'm having the same issue with my drive changing locations, see AlanQ's post above for a reply on that, which I'm going to try out here in a bit and will post back with results.

Also, someone correct me on this, but I thought I'd read it was always good practice to umount any external drive (not necessarily your internal) before you shutdown, the same way you would tell Windows to "stop" running the external drive so you could "Safely Remove Hardware".

Here's hoping we both get up and running successfully!

---

### Post by AlanQ on 2009-10-13
Quintino, you're welcome.

As Rayve said, check out my post #21 above regarding /dev/sdc1 becoming /dev/sdb1. The kernel assigns a device to whichever device file it 'chooses'.

Rayve:

The shutdown process involves the computer running a set of scripts. Amongst these are instructions to synchronise all filesystems (sync = make happen all pending writes) and unmount everything that's mounted -- so you should be safe.

Having said that, I always unmount external drives before shutting down.
And I manually *sync* before I *umount*.
Which is quick to do and quite reasonable for the chronically paranoid :)
And, of course, you have to do this (via a terminal or by clicking an icon) before you switch-off/remove a device anyway.

---

### Post by Rayve on 2009-10-13
AlanQ,

Thanks so much for sticking with this.  I think I'm close to getting the hang of this!

My only issue now is the UUID (still not seeing it in the Places folder, but I figure that may come once the UUID is sorted out).

```
 candice@ubuntu:~$ sudo vol_id --uuid /dev/sdf1
unknown or non-unique volume type (--probe-all lists possibly conflicting types)
candice@ubuntu:~$ sudo vol_id --uuid /dev/sdf1 --probe-all
candice@ubuntu:~$ 

```It's in /dev/sdf1 again today.  :P

I think I have the command wrong for --probe-all.  I've tried doing a search of the forums but so far haven't found anything else that matches my issue here.

EDIT:  I found this in another thread, the same UUID I imagine?

```

candice@ubuntu:~$ sudo blkid
/dev/loop0: UUID="8362ad9c-b9ec-48b0-bbe7-daad3fc39c0b" TYPE="ext3" 
/dev/sda1: LABEL="HP_RECOVERY" UUID="2B72-1CC3" TYPE="vfat" 
/dev/sda2: UUID="D0EC7E96EC7E7696" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/sdf1: LABEL="CANDICE" UUID="0000-0F49" TYPE="vfat" 

```

---

### Post by AlanQ on 2009-10-13
*blkid* -- smart, I've never before discovered that one.

--probe-all doesn't work for me either.
Note: Typically all options (things starting *-* or *--*) go before the device/file.

That ext3 loop device suggests you are running the system from a CD... yes?

And those short UUIDs are stretching the bounds of my ignorance.

What version of Ubuntu are you running?
Are you running from the live CD?

---

### Post by Rayve on 2009-10-13
> **AlanQ said:**
> *blkid* -- smart, I've never before discovered that one.

--probe-all doesn't work for me either.
Note: Typically all options (things starting *-* or *--*) go before the device/file.

That ext3 loop device suggests you are running the system from a CD... yes?

And those short UUIDs are stretching the bounds of my ignorance.

What version of Ubuntu are you running?
Are you running from the live CD?

Nope - I installed via a LiveCD and then used Wubi to make it a partition of my main hard drive (I think that's how it was, I have the memory of a gnat some days - I know I used LiveCD to just run via boot up to mess with Linux for about a week and see what I thought of it, and then decided to do a side-by-side so I could dual-boot and see how it ran all my programs etc so I used Wubi for that).  I don't even have a CD in either of my drives at the moment.

I am running 9.04, Jaunty.

The short UUIDs threw me also, since I expected them to be longer.  Maybe that was why vol_id --uuid didn't like it?  

If necessary, I can move everything from my external back to my main internal HDD and reformat my external completely and then move everything back - it will take some time as I'd have about 60GB to move, but it is an option if it comes down to that.  I'm not completely adverse to that.

EDIT:

Browsing more forums, I found this great post by bodhi.zazen on [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131) "How to fstab" and it had this great excerpt:

> 
[SIZE=2]**Mount point.**[/SIZE]
This is where the partition is mounted or accessed within the "tree" (ie /mnt/hda1). 
You can use any name you like.
In general
[LIST=1]
[*]/mnt Typically used for fixed hard drives HD/SCSI. [COLOR=darkred]If you mount your hard drive in /mnt it will NOT show in "Places" and your Desktop.[/COLOR]
[*]/media Typically used for removable media (CD/DVD/USB/Zip). [COLOR=navy]If you mount your hard drive in /media it WILL show in "Places" and your Desktop.[/COLOR]
[/LIST]
Hmm... so I did 

```

sudo umount /mnt/seagate1

```and then checked "mount" to make sure it was done.  It didn't show up, so per the directions of "How to fstab" I did

```

candice@ubuntu:~$ sudo mkdir /media/seagate1
candice@ubuntu:~$ sudo mount -t vfat /dev/sdf1 /media/seagate1

```I checked "mount" once more, and sure enough, there was my new /media/seagate1 line.  

When when I clicked on Places, boom, my external drive was displayed with the "120 GB Media" name from the drop down.  Yay!  I can now see all of my files on my external drive in a graphical fashion.  That will make moving/copying/etc much easier!

vol_id --uuid still gives me the non-unique error and won't show me a UUID, but now that I know how to mount it, I don't mind checking 

```

sudo fdisk -l

```

each time I need to mount it.  I'd still like to find out the UUID, don't get me wrong, but it isn't critical.  

AlanQ, bodhi.zazen and Ubuntuforums... you're all awesome.  :D

---

### Post by AlanQ on 2009-10-13
Result! I've learnt something too -- now I know why Ubuntu insists on sticking things in /media instead of the good old /mnt .

The fact that you are on a Wubi install might explain the UUID problem but I don't know why.

Ubuntu installed by Wubi still runs as an independent OS, with independent access to the hardware including the USB.

With a Wubi install, Ubuntu is installed in a Windows filesystem and does not have a partition of its own.

Worth noting, from [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php) "Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem".

Try running a live CD and see if blkid or vol_id gives a better result.

And, as a next step, you might be ready for a 'real' dual boot with Ubuntu on its own partition...

:)

---

