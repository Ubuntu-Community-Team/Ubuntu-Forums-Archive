---
title: "Help with a Frakkin' USB flash drive"
date: 2006-10-15
forum: Hardware &amp; Laptops
---

### Post by Chickenfoot on 2006-10-15
Help me, Spock, Help me,

I have a Memorex 1gb stick. My Dapper LTS will not see it.

My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/sda1 /media/usbdrive vfat iocharset=utf8,umask=0000   0   0
usbfs /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

My fdisk-l looks like this:

chickenfoot@spanky:~$ sudo fdisk -l
Password:

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       38346   308014213+  83  Linux
/dev/hda2           38347       38913     4554427+   5  Extended
/dev/hda5           38347       38913     4554396   82  Linux swap / Solaris

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14945   120045681    7  HPFS/NTFS

I created a directory, media/usbdrive as my mount point. When i tpye:

chickenfoot@spanky:~$ sudo mount /dev/sda1 /media/usbdrive

I get:

mount: you must specify the filesystem type

How do I do this? Someone please help me connect the dots.

---

### Post by Kateikyoushi on 2006-10-15
You can't mount it because it is not the sda1 device.
The fdisk -l did not list it. Can you see it in another OS ?

Can you find it if you list "dmesg" ?

---

### Post by NeoLithium on 2006-10-15
I found this post on another board, which hopefully can help you out:

Open a terminal or console, su to root, and:
 # ls -l /var/tail/messages
 
 Then plug in your USB drive.
 
 You should see (after a slight delay) some messages like this:
 Nov 6 18:19:41 venice kernel: usb 1-2: new full speed USB device using uhci_hcd and address 3
 Nov 6 18:19:41 venice kernel: scsi3 : SCSI emulation for USB Mass Storage devices
 Nov 6 18:19:44 venice usb.agent[22682]: usb-storage: already loaded
 Nov 6 18:19:46 venice kernel: Vendor: Generic Model: USB SD Reader Rev: 2.00
 Nov 6 18:19:46 venice kernel: Type: Direct-Access ANSI SCSI revision: 00
 Nov 6 18:19:46 venice kernel: SCSI device sda: 31360 512-byte hdwr sectors (16 MB)
 Nov 6 18:19:46 venice kernel: sda: Write Protect is off
 Nov 6 18:19:46 venice kernel: SCSI device sda: 31360 512-byte hdwr sectors (16 MB)
 Nov 6 18:19:46 venice kernel: sda: Write Protect is off
 Nov 6 18:19:46 venice kernel: /dev/scsi/host3/bus0/target0/lun0: p1
 Nov 6 18:19:46 venice kernel: Attached scsi removable disk sda at scsi3, channel 0, id 0, lun 0
 Nov 6 18:19:47 venice scsi.agent[22727]: sd_mod: loaded successfully (for disk)
 
 So, you can see here that the flash drive is sda.
 Assuming you only have one partition on the drive (most likely)
 you will be interested in partition #1.
 
 Make somewhere to mount it:
 # mkdir /media/USBflash
 
 Mount it manually:
 # mount /dev/sda1 /media/USBflash
 
 All things being equal, the partition type will be automatically
 detected, and the contents of the partition will be available at /media/USBflash.
 
 I suspect that you'll find the flash is a fat(16) partition formatted
 as vfat (long filenames).
 So to be able to write to the flash drive as a user (rather than root)
 you will need to add a umask to the mount option:
 # mount -o umask=002 /dev/sda1 /media/USBflash
 
 To unmount it (make sure you wait for it!!!!)
 # umount /media/USBflash
 
 to make this as easy as "$ mount /media/USBflash"
 # echo " /dev/sda1 /media/USBflash vfat user,umask=002 0 0" >> /etc/fstab

---

### Post by Chickenfoot on 2006-10-15
Gentleman,

thank you for the quick response. I am now reading the info you both graciously provided...

---

### Post by Chickenfoot on 2006-10-15
Hey Neo,

For the first part I get:

chickenfoot@spanky:~$ sudo ls -l /var/tail/messages
Password:
ls: /var/tail/messages: No such file or directory
chickenfoot@spanky:~$

I've made the folder: mkdir /media/USBflash

here it is in fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/sda1 /media/USBflash vfat iocharset=utf8,umask=0000   0   0
usbfs /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

But when I try to mount, I get this:

chickenfoot@spanky:~$ mount /dev/sda1/media/USBflash
mount: can't find /dev/sda1/media/USBflash in /etc/fstab or /etc/mtab

But didn't i already put it into fstab?

---

### Post by Chickenfoot on 2006-10-15
Holy MAckeral!!! It works!! Thank you all for helping this stumbling, bumbling n00B!!!

You guys ROCK!!
=D>

---

### Post by Kateikyoushi on 2006-10-15
put a space between the mount point and the device

```
/dev/sda1 /media/USBflash
```

---

### Post by Chickenfoot on 2006-10-15
SO now, do I have umount every time?

Or do I just pull out and go?

---

### Post by NeoLithium on 2006-10-15
try to use this command:
```

mount /dev/sda1 /media/USBflash

```
There should be a space between sda1 and /media.
And someone beat me to it.

Depending on the packages you have installed with GNOME, it may be automountable. Check out PREFERENCES-> REMOVABLE DRIVES and see if you can set it up in there :)

---

### Post by Chickenfoot on 2006-10-15
Also,

what would the command be to have the USB flash drive autodetected when I plug in?

---

### Post by Chickenfoot on 2006-10-15
thanks Neo, 

I will make the correction now.

---

### Post by louistan3 on 2006-10-15
how is it that my flash drive gets automounted and ubuntu adds a shortcut on the desktop instantly.. then i just right click and click eject to umount... how come yours cant or doesnt do that? just curious cause i thought they added that automounting thing in dapper...so i think yours should work the same way.. :D

---

### Post by Chickenfoot on 2006-10-15
Hey guys,

Sadly, I still cannot write to my flash drive MY fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/sda1 /media/USBflash auto rw,exec,noauto,user,exec,iocharset=utf8,umask=0000   0   0
usbfs /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

I've had the flash drive RW, user & exec. But still cannot write to it. So, what am I doing wrong?

---

### Post by Chickenfoot on 2006-10-15
Hey Louistan,

Let me tell 'ya, this switch to linux from XP has not be easy, to say the least. My Lexmark printer is a paperweight, it took forever to understand how to mount my xp drive, lots of reading with the ipod, and my flash drive still won't work. But it's worth it. I feel like Joe Pantialone in the Matrix...Why did I take that stupid pill, I could have just lived out my days in sweet, blissful ignorance...

The truth is that Linux makes me feel like my IQ drops dramaticlly, everytime I open up Ubuntu. You go on the forums. You read the post and they don't SEEM too complicated. Then all of a sudden, I've become a chimpanze, banging on a keyboard. I mean, I have spent ALL day trying to get my silly little flash stick to work. But when I look back, and I see all of the effort, and time I've invested, I still come up with the same conclusion. A bad day with Linux is still better than any day with Win****!

Now, having said that, waaaaaahhhhhh!!!!!

---

### Post by TiredBird on 2006-10-15
If you're still wrestling with this problem you might look at the ownership and permissions on the mount point. My guess is that because /media is owned by root, you probably had to use 'sudo' to create the directory /media/USBflash, in which case, unless you've already changed it, is now owned by root, (because when you used 'sudo' you took on the image of 'root'. Then you mount the stick on that point and instead of having the permission you put in fstab it has the permission and ownership of the mount point.

Also, there are ways of making sure that stick always has the same name assigned to it, regardless of the order in which you plug in your USB devices. If you put the 'persistent' name in your fstab, it will always mount. If you're using the Gnome desktop you can set an 'automount' provision that will take care of that too.

---

### Post by Chickenfoot on 2006-10-15
TiredBird,

Thanks for the response.

You wrote:

[COLOR="Red"]my guess is that because /media is owned by root, you probably had to use 'sudo' to create the directory /media/USBflash, in which case, unless you've already changed it, is now owned by root, (because when you used 'sudo' you took on the image of 'root'. Then you mount the stick on that point and instead of having the permission you put in fstab it has the permission and ownership of the mount point.[/COLOR]

You are correct sir! I did, indeed, use sudo. So, how do I change the  permission and ownership of said mount point?  How do I change the most uncooperative Mr.  /media/ USBflash  ?


Any help would be greatly apprciated!

---

### Post by TiredBird on 2006-10-15
Please follow this carefully. If you do exactly as it says it should work. 

(1) dismount the USB stick from the mount point. I'm not sure this is necessary but it always has been for me.

(I assume you checked the ownership on the mountpoint after my post and found it to be 'root'.)

(2) from a terminal:

```
sudo chown yourloginname:yourloginname /media/USBflash
```

(Of course you will have to change 'yourloginname' to whatever you logged in with.)

Then you can remount the flash drive.

A few notes: (read carefully - IMPORTANT!)

I presume that what you are mounting is formatted as fat32, at least that's the way the Memorex Travel Drives are sold. (I have three of them.) _Fat32 has no ownership or permissions associated with it other than simple read and write._ 

When you mount such a partition on Linux, you have to tell Linux what to do about the permissions. You do that either in the mount command with the -o options or in fstab if you have it defined there. (fstab is used by mount which doesn't expect you to enter anything it can find in fstab.)

The important options for mounting fat32 are 'user', 'users', and 'uid'. 

If you use option 'user', only the mounter can dismount it and if it was mounted at startup or with the use of 'sudo' or by a number of other means, the owner will be 'root'. However, the 'user' option does permit a non-root user to mount and umount the device. It just has to be the same for both the mount and umount.

'users' (with the 's' on the end) allows anyone to umount it regardless of who mounted it so be careful about whether you are using 'user' or 'users'. There is a difference. I would think that if you are using the computer personally as a desktop type computer, 'users' (with an 's') is what you want.

Without the 'uid=' option, a fat32 device will take on the ownership of the mount point or the mounter, I don't remember which. In any event, it's usually not what you want so use the 'uid=' option to assign yourself as the owner (unless you want it to be 'root' or someone else). 

You will find that in addition to your login name, you also have a number assigned, which if you were the installer, is probably 1000. Assuming that is the case, add 'uid=1000' to the list of options in your fstab for the USB stick. That makes you the owner of the files as well as any new ones you create. 

It is possible between the ownership and permission of the mount point and the options in fstab to get what you want but you have to set it up right.

---

### Post by Chickenfoot on 2006-10-15
Hey Tirebird,

Thank you so much for the replies. Here's ehat I got:

My stab now looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1 /media/ windows ntfs nls=utf8,umask=0222 0 0
/dev/sda1 /media/ USBflash vfat rw,iocharset=utf8,umask=0000   0   0
usbfs /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0

When i go to unmount media /USBflash, I get this:

chickenfoot@spanky:~$ sudo umount /media/ USBflash
umount: /media/: not mounted
umount: USBflash: not found


I type int that line you gave me, I get this:

chickenfoot@spanky:~$ sudo chown chickenfoot:chickenfoot /media/USBflash

BUT, when I try to remount, I get this:

chickenfoot@spanky:~$ sudo mount /media/ USBflash
mount: you must specify the filesystem type

What to do?

Chickenfoot

---

### Post by Chickenfoot on 2006-10-15
Sorry, I posted incorrect FSTAB.

Hee is the correct one:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1 /media/ windows ntfs nls=utf8,umask=0222 0 0
/dev/sda1 /media/ USBflash vfat rw,users,uid=1000,iocharset=utf8,umask=0000   0   0
usbfs /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0

---

### Post by Chickenfoot on 2006-10-15
SOrry for not doing this more efficiently...

Here is my fisk -l output:

chickenfoot@spanky:~$ sudo fdisk -l

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       38346   308014213+  83  Linux
/dev/hda2           38347       38913     4554427+   5  Extended
/dev/hda5           38347       38913     4554396   82  Linux swap / Solaris

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14945   120045681    7  HPFS/NTFS

Disk /dev/sdb: 30.0 GB, 30005820928 bytes
255 heads, 63 sectors/track, 3647 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          10       80293+   0  Empty
/dev/sdb2              11        3648    29222235    b  W95 FAT32

Disk /dev/sda: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3936     1007600    e  W95 FAT16 (LBA)
chickenfoot@spanky:~$

/dev/sda1 is the Usb Flash

---

### Post by TiredBird on 2006-10-16
I wrote a rather scathing reply a few minutes ago but I guess the moderators thought I was being too harsh and deleted it. Maybe I was.

Anyway, you've got some things that you need to fix.

It seems that somehow you keep getting extra spaces inserted where they don't belong. Let's start with fstab.

The format for each line is supposed to be: device name, mount point, filesystem type, options, dump and pass. None of the items can contain a space. A space or tab character is used to separate items. (I would recommend the tab character and get all items lined up so you can see that everything is included and nothing extra has crept in.

Specifically, I see two problems in your fstab:

> /dev/hdc1 /media/ windows ntfs nls=utf8,umask=0222 0 0

It looks as if the space between '/media/' and 'windows' should not be there. I don't think this has anything to do with your USB stick problem but it needs to be fixed.

> /dev/sda1 /media/ USBflash vfat rw,users,uid=1000,iocharset=utf8,umask=0000 0 0

Again, it appears as if an extra space has crept in after '/media/'. I think it should be '/media/USBflash' without any space.

Get those two things fixed and post a copy of the revised fstab.

I'll be watching for your post. Then we'll continue.

---

### Post by geekchic9 on 2006-10-16
This may be a stupid question, but...why doesn't the OP just install Edgy? Everything automagically works when I use my USB flash drive in Edgy. No file editing needed.

---

### Post by TiredBird on 2006-10-16
It appears from your fdisk output that you may have another USB disk. It appears to be a 30GB external drive. On your printout it is called /dev/sdb. 

If this is indeed the case, whether your flash drive is called /dev/sda or /dev/sdb is going to be determined by the sequence in which your system recognizes your plug ins. (We'll solve that problem later but first things first.) 

In the meantime, just to be sure, everytime you need to use a command that deals with the flash drive directly, do a 'sudo fdisk -l' first to make sure you're calling it by the right name. OK? (If you don't do this and end up making a mistake, you could cause some unintended damage to the other drive.)

---

### Post by TiredBird on 2006-10-16
To geekchick9:

Not sure. Probably because it hasn't been released yet. I don't know what his intentions are but I intend to stay with Dapper for the forseeable future. I have enough trouble trying to get things to work without having to deal with something that is unproven.

---

