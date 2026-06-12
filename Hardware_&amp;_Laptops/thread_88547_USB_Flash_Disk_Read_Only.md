---
title: "USB Flash Disk Read Only?"
date: 2005-11-10
forum: Hardware &amp; Laptops
---

### Post by jeffreyvergara.NET on 2005-11-10
Hello, I have a Sandisk 256mb CRUZER mini, I've used it before in Window$ but when I used it in Linux it just became "Read Only" So I can only view files. I tried to "sudo nautilus" in the drive, but still it's Read Only. How can I make this Read+Write??? or is it broken?

---

### Post by devnulljp on 2005-11-10
You have to mount it rw, or make sure your user has read permissions.
Do you have it set to automount in /etc/fstab? If so, something like this might help:

```
/dev/sda1       /mnt/usb0       vfat    umask=002      0      0
```

make the change and then

```
sudo mount -a
```

---

### Post by jeffreyvergara.NET on 2005-11-10
hello, i got this error:

mount: special device /dev/sda1 does not exist


I have my 6 in 1 card reader plugin correctly, and I can read or write. the only problem is my USB Jump Drive (that what they call it,)

---

### Post by LCID Fire on 2005-12-17
I have a 12 in 1 card reader only mounting my cards (cf, mmc) readonly, too.
Either the driver has some shortcomings or some configuration is invalid.
Anybody any ideas?

---

### Post by TheEHMan on 2005-12-31
Follow the directions posted here:
[http://www.ubuntuforums.org/showthread.php?p=616396#post616396]("http://www.ubuntuforums.org/showthread.php?p=616396#post616396")

Worked like a charm for me.

---

### Post by truthfatal on 2006-01-03
I have a similar problem with my Centrios 256MB Memory Stick. on my new compy (maybe my old compy as well, I havn't tried it yet) 

***EDIT***
**FIXED***
The lazy way -- Insert USB key, run gParted, select /dev/sda, unmount /dev/sda through gParted's menus, Re-format the bugger!
It's probably NOT a good idea to do this on mp3 players or anything with important information on it.
***EDIT***

AMD Sempron 2600+ , 1024MB DDR400 ram , ASUS K8N-E

I don't know what information is relevant, but here's what I have

Immediatley after inserting the stick and it automounts:

```

truthfatal@tweaker2:~$ dmesg | tail
[4294968.488000] FAT: Filesystem panic (dev sda1)
[4294968.488000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[4294969.489000] FAT: Filesystem panic (dev sda1)
[4294969.489000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[4294969.489000] FAT: Filesystem panic (dev sda1)
[4294969.489000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[4294969.489000] FAT: Filesystem panic (dev sda1)
[4294969.489000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[4294969.489000] FAT: Filesystem panic (dev sda1)
[4294969.489000]     fat_get_cluster: invalid cluster chain (i_pos 0)

```

mtab & fstab:
```

truthfatal@tweaker2:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-10-386/volatile tmpfs rw,mode=0755 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
/dev/sda1 /media/usbdisk vfat rw,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

```
```

truthfatal@tweaker2:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

The files from my Fedora Core 4 Machine where the Stick works flawlessly.
when I do:
```
truthfatal@tweaker2:~$ ls /media/usbdisk
cgi-bin  error  hosts  html  httpd.conf  icons  index.html~  manual  mrtg  Music.tar.gz  network  nut-cgi-bin  usage  wordtrans
truthfatal@tweaker2:~$ mv /media/usbdisk/* ~
mv: cannot remove `/media/usbdisk/cgi-bin': Read-only file system
mv: cannot remove `/media/usbdisk/error': Read-only file system
mv: cannot remove `/media/usbdisk/hosts': Read-only file system
mv: cannot remove `/media/usbdisk/html': Read-only file system
mv: cannot remove `/media/usbdisk/httpd.conf': Read-only file system
mv: cannot remove `/media/usbdisk/icons': Read-only file system
mv: cannot remove `/media/usbdisk/index.html~': Read-only file system
mv: cannot remove `/media/usbdisk/manual': Read-only file system
mv: cannot stat `/media/usbdisk/mrtg': Input/output error
mv: cannot remove `/media/usbdisk/Music.tar.gz': Read-only file system
mv: cannot remove `/media/usbdisk/network': Read-only file system
mv: cannot stat `/media/usbdisk/nut-cgi-bin': Input/output error
mv: cannot stat `/media/usbdisk/usage': Input/output error
mv: cannot stat `/media/usbdisk/wordtrans': Input/output error

```

---

### Post by aimless on 2006-01-03
I have the same problem with an iRiver mp3 player.I know it's not a hardware issue because it worked fine under an earlier Mandriva system.Anyone have a quick and painless solution.Seems to be an issue because I've seen this problem in other posts on the forum.

---

### Post by jnorth on 2006-03-04
[QUOTE=truthfatal]
```

truthfatal@tweaker2:~$ dmesg | tail
[4294968.488000] FAT: Filesystem panic (dev sda1)
[4294968.488000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[4294969.489000] FAT: Filesystem panic (dev sda1)
[4294969.489000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[4294969.489000] FAT: Filesystem panic (dev sda1)
[4294969.489000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[4294969.489000] FAT: Filesystem panic (dev sda1)
[4294969.489000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[4294969.489000] FAT: Filesystem panic (dev sda1)
[4294969.489000]     fat_get_cluster: invalid cluster chain (i_pos 0)

```
...
```
truthfatal@tweaker2:~$ ls /media/usbdisk
cgi-bin  error  hosts  html  httpd.conf  icons  index.html~  manual  mrtg  Music.tar.gz  network  nut-cgi-bin  usage  wordtrans
truthfatal@tweaker2:~$ mv /media/usbdisk/* ~
mv: cannot remove `/media/usbdisk/cgi-bin': Read-only file system
mv: cannot remove `/media/usbdisk/error': Read-only file system
mv: cannot remove `/media/usbdisk/hosts': Read-only file system
mv: cannot remove `/media/usbdisk/html': Read-only file system
mv: cannot remove `/media/usbdisk/httpd.conf': Read-only file system
mv: cannot remove `/media/usbdisk/icons': Read-only file system
mv: cannot remove `/media/usbdisk/index.html~': Read-only file system
mv: cannot remove `/media/usbdisk/manual': Read-only file system
mv: cannot stat `/media/usbdisk/mrtg': Input/output error
mv: cannot remove `/media/usbdisk/Music.tar.gz': Read-only file system
mv: cannot remove `/media/usbdisk/network': Read-only file system
mv: cannot stat `/media/usbdisk/nut-cgi-bin': Input/output error
mv: cannot stat `/media/usbdisk/usage': Input/output error
mv: cannot stat `/media/usbdisk/wordtrans': Input/output error

```[/QUOTE]

I got the same thing on a USB drive enclosure that I have formatted as FAT32 for sharing purposes with M$ boxes.

The best thing would be to reformat, but if you need to keep data on the disk you can try running fsck (device) - in my case I ran:
```
sudo fsck -a /dev/sda1
```
--note 1 - fsck automatically switches to use .vfat if you have your fs formatted as fat32 and seemed to work as well or better than M$ check and repair feature but then I don't always know what I'm talking about...
--note 2 - the -a switch just sets it to auto repair, if you want to see the choices it gives you then run without the switch and you will be prompted at each error...

This worked for me just fine and didn't screw up any of my MP3's on the disk (around 100G worth).  

I wouldn't always recommend using my word of course, but if you are in desperation mode, well, it worked for me.

---

### Post by henriquemeira on 2006-10-08
I found a seemed problem.

I have a 5 in 1 usb reader. First, I had a Kingston 256MB MMC card, and work very fine. Just plug and play on USB port.

After, I buy an Adata 1GB MMC card, but it does not work. I edit one file, and "magically" all files and directories are changed to read-only. :-k 

Well, after several attempts, I got it work. I needed run fdisk, and format USB card. :twisted: 

Following the steps:

a) plug your usb card, and umount it:
  $ sudo umount /dev/sda1   #if it is on /dev/sda1

b) delete, and create a new partition:
  $ sudo fdisk /dev/sda    # just sda, not sda1
    
  b.1) choose 'd' to delete your current partition
  b.1.2) just follow default options

  b.2) choose 'n' to create a new partition
  b.2.1) choose 'p' to indicate primary partition
  b.2.2) just follow default options

  b.3) choose 't' to indicate file system 
  b.3.1) choose 'e': W95 FAT16 (LBA)

  b.4) choose 'a', to indicate it as bootable

  b.5) Now, important: you need turn off automount, before writing
       the partition table, so, just move /etc/mtab to /etc/mtab.stop
       in another terminal. :rolleyes: 
  b.5.1) choose 'w'
  b.5.2) Now, you can turn on automount, so, just move back
         /etc/mtab.stop to /etc/mtab .

c) mount and format usb card:

  $ sudo mount /dev/sda1
  $ sudo mkdosfs -n MyUsbCard /dev/sda1

Just do it! 8) 

FINISH! :mrgreen:

---

### Post by odzx on 2006-11-02
nothing seems to work for me.
this problem started for me a couple of weeks ago. i have a new usb HD that did mount automatically but as read only although i im the owner of the disk. reformatting helped and i was able to r/w. after a while things got back to to the previous state. unmounting and reconnecting usb also allows me to r/w but only for a short while (some times just for a couple of minutes) and then back to read only. rebooting... same result. i cant think of anything in particular that triggers this behavior.
fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=5be0bd0e-a411-420c-9a9b-44ee6ab89949 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=fe2d8dbf-296f-4112-b592-c7e3959f5837 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
sysfs /sys sysfs defaults 0 0
usbfs /proc/bus/usb usbfs defaults 0 0
none /dev/shm tmpfs defaults 0 0
none /dev/pts devpts defaults 0 0
```
any ideas on how to fix this ridiculous problem ones and for all?:confused:

---

### Post by Gavin2610 on 2008-06-03
Hi,



Do you guy know what to do? I aint that good on the pc so if anyone can like give me a lil breakdown (idiots guide)that wud be great. 

Thanks
Gavin

---

### Post by Sef on 2008-06-03
> When i try to delete or format anything this on my USB Stick it comes up with some thing like this..

You probably have a lock/unlock button on your usb.  Look for it and unlock it.

---

### Post by Gavin2610 on 2008-06-03
I have already had a look into that and there isnt one anywhere :S .

It is a Mikomo USB stick.

---

