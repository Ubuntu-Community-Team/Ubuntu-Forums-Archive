---
title: "Can't mount usb hard drive"
date: 2008-10-07
forum: Hardware
---

### Post by aewing30 on 2008-10-07
I'm using Ubuntu 8.04 and when i plug my western digital external hard drive in i get an error saying can't mount generic volume device. Please help. Thanks

---

### Post by Ubuntiac on 2008-10-07
I had a problem like this that first came in when I upgraded to Hardy through to Intrepid. I don't know if the fact my laptop has no CD drive has anything to do with it, but here's what the problem (and fix) for me was:

The file /etc/fstab (which says how drives should mount) had a line like this:
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Which essentially means that the second drive (b1) will always mount as a cdrom drive (which it isn't, it was a usb key). When it tried to read the "cd" file format and found a usb key file format it spat out an error.

The simple fix was to:

1. open a console and type:
```
sudo cp /etc/fstab /etc/fstab.backup
```
To back up the fstab file (which is *very* important to your system). Then,

2. Type:
```
sudo nano /etc/fstab
```
To edit it. 

3. Then just type # before the /dev/sdb1 line to make it look like this:
**#**/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Note: you may have a different drive letter (eg /dev/sd**c**1)

4. Press Crtl + X, then Y, then Enter to save.

After this my problem was fixed! (I had to remove and replace the drive). You may also want to check that your CD / DVD drive (if you have one) works properly.

Hope this helps! It did for me... \o/   :-D   \o/

---

### Post by LightningLixxx on 2008-10-07
I'm having a similar problem with my Maxtor OneTouch4 Mini but I just can't get it to automount on startup. Here's my scenario: I started with Vista, then recently I decided to dual-boot with Ubuntu. My external hd always worked fine in Vista, and when I installed Ubuntu, it worked fine there too. It always automatically mounted upon startup. I did a little cleaning up in Vista and uninstalled the unnecessary Maxtor drive management software and then the next time I booted up Ubuntu, I had to manually mount the drive. I reinstalled the management software but it didn't seem to reverse the damage. I've googled the subject and have found quite a few answers to similar questions, all of them being slightly different. I've tried quite a few things in fstab and none of them seem to be working. 
I mean, it's not the end of the world to have to open up the terminal and type sudo mount /dev/sdb1 /media/"OneTouch4 Mini" when I start up but it would be nice not to have to.
I tried entering a # before the line like Ubuntiac said but that isn't working. When I take it off and type in "sudo mount -a" (as per the advice of someone, somewhere) I get a message saying that line 10 of fstab is bad. When I edit the line with # this message doesn't come up but the device doesn't mount either.

---

### Post by WWSmith36 on 2008-10-07
What is on the hard drive you are mounting?  If this drive was previously used by windows it might be dirty.

Most of the time when external drives that previously worked in linux and then do not work after using windows is caused by improper shutdown in windows. Simplest thing to do is to go back to windows and disconnected the drive using the Safely Remove Hardware icon in the system tray, and then cleanly shut down windows.

If this does not solve your problem, then with the drive connected open a terminal from menu Application-> Accessories-> Terminal and type these commands and paste the output here

sudo fdisk -l
sudo mount

---

### Post by LightningLixxx on 2008-10-07
First of all let me say I don't mean to hijack the thread but it seemed better to post in a related thread rather than make a new one.

Anyway, WWSmith36, I really thought that would work but it didn't. I keep mostly music, videos, and assorted document files on my external hd. Oh and note that I can manually mount the drive and can access files and everything, the only problem is it won't automount on startup.

Here is the output from those two commands:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfce6c2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6005    48235131    7  HPFS/NTFS
/dev/sda2            6006        9526    28282432+   5  Extended
/dev/sda3            9527        9730     1627136    7  HPFS/NTFS
/dev/sda5            6006        9375    27069493+  83  Linux
/dev/sda6            9376        9526     1212876   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd1b4c56d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

```
```
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

```
I'm guessing it's probably obvious but the drive in question is sdb1.

Thank you for the help by the way.

---

### Post by cool_penguin on 2008-10-29
Thanks a lot Ubuntiac. Your solution worked for me. I feel that if one installs Ubuntu using a Live USB instead of a Live CD, they might experience this problem like I did. Not any more. Thanks to you. My problem is now solved simply by commenting out the line that you mentioned in fstab. 

Keep up the good work. 

Cheers,
Harry

---

