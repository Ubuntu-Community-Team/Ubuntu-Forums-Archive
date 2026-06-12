---
title: "Can't mount NTFS USB harddrive"
date: 2009-02-07
forum: Hardware
---

### Post by Nihilism65 on 2009-02-07
I can't seem to get my USB harddrive to mount so I can read my files I have backed up from my Windows PC that recently died. I need to get my documents for work and things like my music files off of the drive. I ran into this post: [http://ubuntuforums.org/showpost.php?p=2942931&postcount=10](http://ubuntuforums.org/showpost.php?p=2942931&postcount=10) and tried to follow what he said to do but I can't seem to find the drive in my fstab file.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b25bdc75-40fb-4be2-9663-69cfec3fec60 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=d0267672-a3b8-4fd4-9ab4-455dbe1be49d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I'm not really sure what to do here and any help would be appreciated. Thanks for any help you can offer in advance. :D

---

### Post by taurus on 2009-02-07
Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That is a lower case letter L, not number 1.

---

### Post by Nihilism65 on 2009-02-07
> **taurus said:**
> Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That is a lower case letter L, not number 1.

I did as you said and got:
```
nihilism@nihilism-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3670    29479243+   7  HPFS/NTFS
/dev/sda2            3671        7296    29125845    5  Extended
/dev/sda5            3671        7206    28402888+  83  Linux
/dev/sda6            7207        7296      722893+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

```

So I tried:

```
nihilism@nihilism-laptop:~$ sudo mount -t ntfs-3g /dev/sda1 /media/NTFS_USB

```

It still won't read. 
I'm brand new to Ubuntu and Linux in general so please give as much detail in your responses as possible and please also excuse the delay in my posts. The laptop I am using has very poor specs and is currently updating so it is extremely laggy.

---

### Post by Nihilism65 on 2009-02-07
I have now also tried sdb1 and this is what I got in return:

```
nihilism@nihilism-laptop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/NTFS_USB
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/NTFS_USB -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/NTFS_USB ntfs-3g force 0 0

```

---

### Post by Nihilism65 on 2009-02-07
I still can't figure this out. I've been looking around through google and still cannot find any useful info. Any help is appreciated.

---

### Post by theozzlives on 2009-02-07
You got to properly dismount from Windows, go to windows and click the safely remove hardware icon by the clock.

---

### Post by taurus on 2009-02-07
> **Nihilism65 said:**
> I have now also tried sdb1 and this is what I got in return:

```
nihilism@nihilism-laptop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/NTFS_USB
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/NTFS_USB -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/NTFS_USB ntfs-3g force 0 0

```

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/NTFS_USB
df -h
```

---

### Post by Nihilism65 on 2009-02-07
Thanks a ton for all your help guys. Works like a charm now. Back to work now. :D

---

### Post by enterman on 2009-02-09
my hdd isnt even shown in the fdisk: ```
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00032db6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3647    29294496   83  Linux
/dev/sda2            3648        6079    19535040    f  W95 Ext'd (LBA)
/dev/sda3   *        6080        9039    23776200    7  HPFS/NTFS
/dev/sda5            3648        6079    19535008+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xc9c05c92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      969021   488386552+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46c146c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS
```

sdb and sdc are internal. Can anyone help?

---

### Post by enterman on 2009-02-12
> **enterman said:**
> my hdd isnt even shown in the fdisk: ```
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00032db6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3647    29294496   83  Linux
/dev/sda2            3648        6079    19535040    f  W95 Ext'd (LBA)
/dev/sda3   *        6080        9039    23776200    7  HPFS/NTFS
/dev/sda5            3648        6079    19535008+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xc9c05c92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      969021   488386552+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46c146c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS
```

sdb and sdc are internal. Can anyone help?
anyone?

---

### Post by kmac on 2009-02-12
Post output of 

```
lsusb
```

---

### Post by enterman on 2009-02-12
```
Bus 001 Device 005: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
Bus 001 Device 004: ID 046d:c221 Logitech, Inc. G15 Keyboard / Keyboard
Bus 001 Device 003: ID 046d:c041 Logitech, Inc. 
Bus 001 Device 002: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 4971:a002  
Bus 002 Device 007: ID 0dda:2026 Integrated Circuit Solution, Inc. USB2.0 Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by jocheem67 on 2009-02-12
Please specify your problem please...
Can you post the output of /etc/fstab

Sdb and sdc are internal, and your 2nd and 3rd harddisks? Using windows?

---

### Post by enterman on 2009-02-12
> **jocheem67 said:**
> Please specify your problem please...
Can you post the output of /etc/fstab

Sdb and sdc are internal, and your 2nd and 3rd harddisks? Using windows?
Alright, I have 3 internal hdds. One with linux and windows, one 500GB NTFS and one 250GB NTFS. I also have an external 250GB which is the one thats not being read by linux but works fine in windows. My fstab: 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
UUID=bc31b347-cc63-4b0d-ac7e-4aabad565132  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=4f6399da-4e5e-4a1f-a699-f98b8f478f0f  /home          ext3         relatime                    0  2  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb1                                  /media/sdb1    ntfs         nls=iso8859-1,umask=000     0  0  
/swapfile1 swap swap defaults 0 0
```

---

### Post by jocheem67 on 2009-02-13
What I miss here is a mountpoint for sdc, so you could create one yourself im /media..
You could use alt-f2 to go into nautilus as root: gksudo nautilus and create a folder sdc1 im /media.

Next you should edit your fstab.

By the way, it seems to me that the options for sdb aren't correct, in fstab..

Here's mine:


[QUOTE]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=50d3cf2c-1bee-4c1f-9652-b7219b2d124c /               ext3    relatime,errors=remount-ro,data=writeback 0       1
# /dev/sdb1
UUID=32DCB0F4DCB0B407 /media/Backup   ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=C808636E08635B08 /media/Windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=09f14c26-e98c-4867-950c-268c5767e216 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[QUOTE/]

The uuid is not really necessary to use , you can just specify your disk with /dev/sdb1 or /dev/sdc1 ( there is a command for getting your uuid, but you should google for it )

As you see I've got two ntfs points, one is a disk the other a partition, which doesn't really matter. The fstab options are just the defaults.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

A useful link.

---

### Post by howlingmadhowie on 2009-02-13
to find the uuid of a partition, go to /dev/disk/by-uuid
and enter

ls -l

---

### Post by enterman on 2009-02-13
I dont fully understand what to add to fstab exactly. sdc1 is my internal 250GB according to gparted.

---

### Post by jocheem67 on 2009-02-13
Something like:

/dev/sdc1 /media/sdc1 ntfs defaults,umask=007,gid=46 0       1

Mind you, you should first make the folder sdc1 in /media

The same counts for sdb1....

---

### Post by enterman on 2009-02-13
ok I did what you said and now my internal 250GB is auto starting, not what I had in mind. Im not THAT good with linux sorry but I created the folder and added what you said to fstab.

EDIT: I have no idea if this is helpful but this is the result of a cat /proc/partitions:

```
major minor  #blocks  name

   8     0   72613056 sda
   8     1   29294496 sda1
   8     2          1 sda2
   8     3   23776200 sda3
   8     5   19535008 sda5
   8    16  488386584 sdb
   8    17  488386552 sdb1
   8    32  244198584 sdc
   8    33  244196001 sdc1
   8    48  244198584 sdd
   8    49  244196001 sdd1
```
sda1 and 3 are ubuntu. sda5 is windows. sdb1 is my internal 500GB NTFS hdd. sdc1 is my internal 250GB NTFS hdd. I would assume sdd1 is my external 250GB? I tried adding a sdd1 folder in media and added it to fstab but it still isnt shown at all.

---

### Post by jocheem67 on 2009-02-14
Your internal drive is starting now , the 250 gb..that's good isn't it? Or did you have anything else in mind...
Sorry, I didn't understand that you're also having probs with an external one. It's read by windows but not by ubuntu? Did you properly unmount it from Win? Otherwise ubuntu won't mount it.

Little tip, it might be handy to install gparted:
"sudo apt-get install gparted" the gnome part. editor. It'll give you a good insight of your drives and partitions.

---

### Post by enterman on 2009-02-14
> **jocheem67 said:**
> Your internal drive is starting now , the 250 gb..that's good isn't it? Or did you have anything else in mind...
Sorry, I didn't understand that you're also having probs with an external one. It's read by windows but not by ubuntu? Did you properly unmount it from Win? Otherwise ubuntu won't mount it.

Little tip, it might be handy to install gparted:
"sudo apt-get install gparted" the gnome part. editor. It'll give you a good insight of your drives and partitions.
yes yes I already have gparted, it isnt shown in that either. I did try properly unmounting it from windows but to no avail. Sorry I didnt make it so clear lol. What else can I do since gparted doesnt even show its existence (probably would of been helpful to say that several posts ago). Thanks for trying to help btw.

EDIT: just to make sure, I loaded up the live cd environment and it isnt shown at all in that either.

---

### Post by jocheem67 on 2009-02-15
Okay, your external usb drive doesn't mount in ubuntu but does in Windows.
It is sdd, that's for sure now....

Hmmmmm, did you try to google the name of the disk icm with ubuntu? Did you try another usb-port?

I think by the way that you don't have to watch fstab for an external...but am not totally sure of that.
To be honest, it seems that I'm out of suggestions now....

Cheers.

---

### Post by enterman on 2009-02-15
> **jocheem67 said:**
> Okay, your external usb drive doesn't mount in ubuntu but does in Windows.
It is sdd, that's for sure now....

Hmmmmm, did you try to google the name of the disk icm with ubuntu? Did you try another usb-port?

I think by the way that you don't have to watch fstab for an external...but am not totally sure of that.
To be honest, it seems that I'm out of suggestions now....

Cheers.
Ive tried other USB ports. Sorry for being ignorant but, icm?

---

### Post by HunkirDowne on 2009-02-15
> **howlingmadhowie said:**
> to find the uuid of a partition, go to /dev/disk/by-uuid
and enter

ls -l

Or to save the list, from 'home' (or wherever you want to save the file):
ls -l /dev/disk/by-uuid > uuid.txt

Now I have the list I have been wanting for days now.  THANKS!!

---

### Post by HunkirDowne on 2009-02-15
> **enterman said:**
> Ive tried other USB ports. Sorry for being ignorant but, icm?

Questions and Comment:

What is 'icm'?

If the external drive does not show up in gparted or 'fdisk -l' (assuming the latter is done from root or sudo), then I would say that it is entirely unrecognized prompting the following questions some of which may appear insulting but are not intended that way.

(1) drive has external power supply and it's turned on, right?
(2) running 'fdisk -l' from sudo or root ('sudo fdisk -l'), right?
(3) do you perhaps have an ieee1394 port (aka "firewire")?
(4) something to try for temporary access before adding to fstab:

sudo mkdir /media/NTFS_USB
sudo mount -t ntfs-3g /dev/sdd1 /media/NTFS_USB -o force

the first command assumes the directory has not already been made
the second command will force mount an ntfs drive that has not been shutdown properly (essentially, it resets the dirty flag).

Caveat: the above may not work since it doesn't show up in fdisk.  The drive address ('/dev/sdd1') I parsed from your '/proc/partitions' post.  Really don't know why it is showing up in '/proc/partitions' and not 'fdisk -l'.

Nevertheless, give the above a try and shout back the results.

HTH -- you never know.  It's better to be lucky than good sometimes.  ;-)

---

### Post by enterman on 2009-02-15
> **HunkirDowne said:**
> 
(1) drive has external power supply and it's turned on, right?
(2) running 'fdisk -l' from sudo or root ('sudo fdisk -l'), right?
(3) do you perhaps have an ieee1394 port (aka "firewire")?
(4) something to try for temporary access before adding to fstab:

1. Of course :P
2. Yes but I will repost at the bottom of this post
3. It has firewire on it but im using USB ;)
4. here is the result: ```
enterman@enterman-desktop:~$ sudo mkdir /media/NTFS_USB
enterman@enterman-desktop:~$ sudo mount -t ntfs-3g /dev/sdd1 /media/NTFS_USB -o force
ntfs-3g: Failed to access volume '/dev/sdd1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

```

here is my fdisk -l again (this is a rerun of it, not the one I posted yesterday): 
```
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00032db6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3647    29294496   83  Linux
/dev/sda2            3648        6079    19535040    f  W95 Ext'd (LBA)
/dev/sda3   *        6080        9039    23776200    7  HPFS/NTFS
/dev/sda5            3648        6079    19535008+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xc9c05c92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      969021   488386552+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46c146c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

```

---

### Post by HunkirDowne on 2009-02-15
I find it extremely strange that it DOES appear in /proc/partitions but does NOT appear in fdisk.  RATS!!

The only other thing I can think of is that you might try is accessing ntfs-3g directly:

ntfs-3g /dev/sdd1 /media/NTFS_USB -o force

If that doesn't work, you may look up the ntfs-3g help online: 

[http://ntfs-3g.org/support.html](http://ntfs-3g.org/support.html)

You may have an answer or you may have a new issue.

---

### Post by enterman on 2009-02-15
tried that command, still nothing. I redid cat /proc/partitions and it produced the exact same results as on page 2. Ive only used ubuntu for 2 months and of course, I have to be the one to find a new issue lol... ><. One thing about this hdd I never mentioned (probably not helpful), it used to be internal and it used to be the hdd linux was installed on but then a friend of mine gave me a raptor drive so I took this drive out and put it back in its usb enclosure it came with and formated it (from windows, it has never ever been able to be read from linux). I also will say for anyone that wonders, I have 0 issues with any other kind of usb hdd (flash drives, memory card readers etc all work 100% fine). Thanks for trying.

---

### Post by jocheem67 on 2009-02-19
"icm" = in comibination with ( sorry I was using the Dutch variant )....

Indeed it looks like you found a new issue.
I wonder , could it be that an internal drive, when put in an external housing, just hasn't got the specs for being usb?

---

### Post by HunkirDowne on 2009-02-20
> **jocheem67 said:**
> 
Indeed it looks like you found a new issue.
I wonder , could it be that an internal drive, when put in an external housing, just hasn't got the specs for being usb?

I have several internal HDDs that have seen the inside of an external housing.  Never had a problem accessing the drives in Win or Linux (or Mac, for that matter.  Usual filesystems restrictions apply (e.g. Win doesn't read ext2 without a special driver and why would I want Win to see ext2/3/4? :^).

---

### Post by enterman on 2009-02-23
> **jocheem67 said:**
> "icm" = in comibination with ( sorry I was using the Dutch variant )....

Indeed it looks like you found a new issue.
I wonder , could it be that an internal drive, when put in an external housing, just hasn't got the specs for being usb?
this particular drive I purchased external (IE, came inside the enclosure it currently resides in), I just decided I wanted it internal at one point but have sense put it back in its enclosure.

---

