---
title: "Trouble mounting NTFS volume"
date: 2005-03-25
forum: Hardware &amp; Laptops
---

### Post by thedreampolice on 2005-03-25
First off I would like to say HI as this is my first post in the Ubuntu forums. I recently Switched from MEPIS and am really enjoying Ubuntu. I hope I can learn enough to contribute something useful to the community.  Now the trouble I have a XP dual boot system with one drive (master hda) as the XP drive and the Ubuntu drive (slave hdb) the second, for some reason I just cant browse the NTFS partition. I have searched the help and tried the commands but they dont seem to work. Any suggestions? Thanks in advanced!

---

### Post by Dachnaz on 2005-03-25
As far as permissions go, NTFS is a horribly broken filesystem. You are going to have to format the drive to be able to do anything as a user yet. However, I was able to copy all of the stuff off my NTFS disk before I formatted. Here's how *I* did it.

1.) If you don't have one yet, you will need a superuser password. In your console, type 
```
$ sudo passwd
```
The console will ask you for a Password, which is your first user's password. Enter that, hit enter, and then it will prompt for a password. After you set a password...
2.) Hit CTRL+ALT+F1. But not yet, because this will take you out of XWindows. First read directions or print them out.
3.) After getting to that command line outside of X, after logging in to your user and then the su, type
```
ps aux|fgrep x
```
This will list your XWindows processes. Type
```
kill <process number>
```
until there are no more processes left that it will let you kill. 
4.) Then type
```
ps aux|fgrep dm
```
and kill all of those (that you can). 
5.) Then type
```
startx
```
This will log you straight in to X, bypassing the login screen, as the root. 
6.) Now you can go to your NTFS hard drive and drag the files to somewhere on another hard drive. 
7.) Before you exit from X, go into your console and cd to the directory where you copied the files to. Type
```
chown <your username here> *
```
This will change all the files in the folder with your stuff to be accessable by your user. 
8.) Now log out of X and log in on the command line as su, and type
```
shutdown -r now
```
This will reboot your computer and take you to the login screen. 
9.) Log in as the normal user and enjoy your files. :)

I hope this helps you. It worked for me!

---

### Post by Buffalo Soldier on 2005-03-25
Have you tried the guide at [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

Or was there any problem? If yes, any info such as error message?

---

### Post by thedreampolice on 2005-03-25
Yes I did try that, it said that partition did not exist. Mepis did mount this fine however. Hmmm. Any other thoughts?

---

### Post by Buffalo Soldier on 2005-03-25
Mind sharing the content of your */etc/fstab* file and output of *sudo fdisk -l* ?

---

### Post by thedreampolice on 2005-03-26
Sure here is fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

and fdisk

Disk /dev/hda: 13.6 GB, 13601193984 bytes
255 heads, 63 sectors/track, 1653 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1653    13277691    7  HPFS/NTFS

Disk /dev/hdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         747     6000246   83  Linux
/dev/hdb2             748         784      297202+   5  Extended
/dev/hdb5             748         784      297171   82  Linux swap / Solaris


I  really dont understand fstab to well. Any thoughts?

---

### Post by Buffalo Soldier on 2005-03-26
Try adding this line to your fstab file.```
/dev/hda1       /media/windows    ntfs    user,umask=0222      0       0
```
If you find yourself not able to edit your fstab file. Go to the console and type **sudo gedit /etc/fstab**. It will then ask for a password. Just enter your user password.

After editing and saving your fstab file. Type```
sudo mkdir /media/windows
sudo mount -a
```at console.

---

### Post by thedreampolice on 2005-03-26
SWEET! That worked! Thanks. BTW Why did I have to do that. Why didnt my fstab file have that? I just really want to understand how all this works. Thanks again.

---

### Post by Buffalo Soldier on 2005-03-26
What I've given is exactly what is available at [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs) :)

Why? I guess that's the flexibility we like in using linux :)

---

### Post by thedreampolice on 2005-03-26
lol, I guess I just needed a bit more hand holding. Thanks again for the help!

---

### Post by Buffalo Soldier on 2005-03-26
Don't thank me. Just remember to return the favour to the next newbie :)

---

### Post by thedreampolice on 2005-03-26
ok will do!

---

### Post by zarathustra on 2005-03-26
I've had problems mounting my NTFS drive. It has no Windows installation on it, it was a secondary hard drive. It now appears in Ubuntu, but I can't mount it. Says it's already mounted or busy  :???:

---

### Post by Buffalo Soldier on 2005-03-26
Again. Mind sharing the content of your */etc/fstab* file and output of *sudo fdisk -l* ?

---

### Post by zarathustra on 2005-03-27
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb        /mnt/windows     ntfs    user,umask02222  0 0


> Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7326    58846063+  83  Linux
/dev/hda2           24420       24792     2996122+  82  Linux swap / Solaris
/dev/hda3            7327       24419   137299522+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           2       10011    80405325    f  W95 Ext'd (LBA)
/dev/hdb5               2       10011    80405293+   7  HPFS/NTFS


Here they are.

---

### Post by Buffalo Soldier on 2005-03-27
Follow instrucstion as previous post. But for the the lines to add to your fstab file I'm not quite sure. Try either one of these:```
/dev/hdb1       /media/windows    vfat    user,umask=0000      0       0
```or```
/dev/hdb5       /media/windows    ntfs    user,umask=0222      0       0
```

---

### Post by zarathustra on 2005-03-27
It says it can't find /dev/hdb in either /etc/fstab or etc/mtab.

---

### Post by zarathustra on 2005-03-27
It's ok, I got it to work. Many thanks :)

---

### Post by Buffalo Soldier on 2005-03-27
Cool :) How did you get it to work? Other's with the same problem will be very interested to know your solution.

---

### Post by zarathustra on 2005-03-28
I put in the last line you suggested. It worked after I tried restarting Linux (I have Gnome panel telling me all the media I have mounted, and my second hard drive appeared and I tried mounting it with the panel but it never worked. I didn't think restarting would help much!).

---

