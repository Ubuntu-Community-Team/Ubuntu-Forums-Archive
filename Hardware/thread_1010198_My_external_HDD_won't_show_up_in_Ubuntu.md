---
title: "My external HDD won't show up in Ubuntu"
date: 2008-12-13
forum: Hardware
---

### Post by The Clown on 2008-12-13
Hi,

I'm not sure if this should go here or in Absolute Beginner Talk, so forgive me if this is posted int he wrong place. I just installed Ubuntu 8.10 about 3 days ago, and I'm loving it so far. The only issue I have is that I have an external HDD that has a lot of my media on it. (songs, videos, etc.) My flash drive was autodetected by Ubuntu and an icon was placed on the desktop until I ejected the drive, so I thought the same would be true with my external HDD, but that's not the case at all.

Is it because the HDD is formatted with NTFS and not FAT32 like my flash drive is? Will I have to reformat the drive in FAT32 to have it read by Ubuntu, and if I do that, will it still be read by Vista when I want to boot to that?

Thanks in advance for your help.

---

### Post by taurus on 2008-12-13
You don't have to reformat your external harddrive.  Just make sure that when you are finished using it in windows, use the Safely Remove Hardware (a little icon in the bottom right) to unmount the drive first instead of just unplugging it.  

So, boot up windows and safely unmount your external harddrive.  Then, Ubuntu shouldn't have any problem mounting it.  Otherwise, you can still mount it by hand from a terminal.

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by brandon88tube on 2008-12-13
Yeah, I had a similar problem when I ended up shutting off my external hard drive without safely removing it, though it hadn't happened to me before when I did it with my USB drive. If it doesn't even appear in the list of devices then try to leave it on and shutdown(not a restart) make sure your drive is on and start up Ubuntu.

---

### Post by The Clown on 2008-12-13
Hmm...I used safely remove in Windows, but it's still not showing up on Ubuntu.

The output from fdisk -l is as follows:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   de  Dell Utility
/dev/sda2   *          14        1319    10485760    7  HPFS/NTFS
/dev/sda3            1319       15546   114277368    7  HPFS/NTFS
/dev/sda4           15547       19458    31415748+   f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown
/dev/sda6           15547       18977    27559476   83  Linux
/dev/sda7           18978       19130     1228941   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by taurus on 2008-12-13
Make sure the external drive is powered on and plugged in.  Then, post the output of this command from a terminal.

```
dmesg | tail
```

---

### Post by The Clown on 2008-12-14
[ 7561.117598] sd 5:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 7561.117610] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[ 7561.118845] sd 5:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 7561.118857] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[ 7561.119840] sd 5:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 7561.119852] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[ 7561.120839] sd 5:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 7561.120851] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information
[ 7561.121842] sd 5:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 7561.121854] sd 5:0:0:0: [sdb] Add. Sense: No additional sense information

---

### Post by taurus on 2008-12-14
Can you access all your files (music, movies, etc.) on that external harddrive from windows?

---

### Post by The Clown on 2008-12-14
Yes, the drive works perfectly in Vista.

---

### Post by taurus on 2008-12-14
Make sure the drive is plugged in.  Then see if you can mount it from a terminal with

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

### Post by The Clown on 2008-12-14
After typing the first line into the prompt, I get the error message mkdir: cannot create directory `/media/sdb1': File exists

---

### Post by taurus on 2008-12-14
> **The Clown said:**
> After typing the first line into the prompt, I get the error message mkdir: cannot create directory `/media/sdb1': File exists

It just means that you already have /media/sdb1 so it's not really an error.

Now what happens when you type in the second command to mount it?

---

### Post by The Clown on 2008-12-14
ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

Seems to conflict the terminal's previous sentiment that sdb1 existed...

---

### Post by taurus on 2008-12-14
What about

```
lsusb
```
What is the brand name and model of your external drive?

---

### Post by The Clown on 2008-12-14
I'm not sure the model, because I bought this HDD used from someone online. I know it's a Seagate HDD in an Ultra Mini Portable Disk enclosure.

---

### Post by taurus on 2008-12-14
I recall hearing a while back that some Seagate USB harddrives don't work well with Linux!  I think there is a firmware to fix that problem but not sure since I lost track of it.

---

### Post by The Clown on 2008-12-14
So will I just not be able to use this drive on Ubuntu, then? Is the hardware just not compatible?

---

### Post by brandon88tube on 2008-12-14
Have you tried using this drive on other computers? Also you can check what kind of hard drive it is by opening the enclosure and looking at the label on the drive. It will give you the serial number etc. Be careful when opening it, make sure you discharge yourself before touch anything inside. You don't want to give your hard drive a static shock.

---

### Post by The Clown on 2008-12-14
Yeah, I've used this drive on 3 different computers. I remember it being a particular pain in the *** to set up on Windows XP...I had to mess around in the device manager and the registry to get it working...so it's probably the drive more than any particular OS. In fact, oddly enough, Vista was the only OS to just accept it right away.

After opening the enclosure, apparently I was wrong about it being a Seagate drive, lol. It's a Maxtor drive, DiamondMax 10, model 6L200R0 PATA 133 HDD, 3.5 Series.

---

### Post by brandon88tube on 2008-12-14
Not sure on this, but you should probably keep the serial number to yourself and not give it out. Also you might want to register the hard drive at the manufacturer's website in case it is still under warranty.

---

### Post by LostAngel on 2008-12-14
I too am having an issue...I get the same error the above user got with:
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1

Also, I see my device listed when I do lusb

Bus 007 Device 004: ID 059b:0176 Iomega Corp. Hi-Speed USB-to-IDE Bridge Controller

---

### Post by brandon88tube on 2008-12-14
Have you tried forcing it to mount?
```
sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs -o force
```

---

### Post by Rekka on 2008-12-14
I am also having this same issue with my additional HD. The only difference is my HD is internal SATA. I have attempted everything up to this point but I'm still unable to see my additional HD on my linux partition.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1             142G  2.3G  133G   2% /
varrun                1.3G  100K  1.3G   1% /var/run
varlock               1.3G     0  1.3G   0% /var/lock
udev                  1.3G   60K  1.3G   1% /dev
devshm                1.3G     0  1.3G   0% /dev/shm
lrm                   1.3G   39M  1.2G   4% /lib/modules/2.6.24-22-generic/volatile
/dev/sdb1             466G  255G  212G  55% /media/sdb1
/dev/sda1             466G  239G  228G  52% /media/sda1


I've gotten this far, but have no clue where to go from here. Any help?

---

### Post by raucous on 2008-12-14
im having the same problem.

---

### Post by brandon88tube on 2008-12-14
Have any of you tried what I said with using the option force? Let me know if you have, otherwise I have no clue if it is working for you or not.

---

### Post by Rekka on 2008-12-14
> **brandon88tube said:**
> Have any of you tried what I said with using the option force? Let me know if you have, otherwise I have no clue if it is working for you or not.

I have... Getting error message 

fuse: failed to access mountpoint /media/hd-ntfs: No such file or directory

---

### Post by brandon88tube on 2008-12-14
> **Rekka said:**
> I have... Getting error message 

fuse: failed to access mountpoint /media/hd-ntfs: No such file or directory

You are a different case as the command given is for USB devices. You could try and change the location to make it your second hard drive.

---

### Post by Rekka on 2008-12-14
> **brandon88tube said:**
> You are a different case as the command given is for USB devices. You could try and change the location to make it your second hard drive.

would you be so kind to tell me how to do so?

---

### Post by brandon88tube on 2008-12-14
> **Rekka said:**
> would you be so kind to tell me how to do so?

I don't want to give you the wrong info so I'm going to link you to some Ubuntu documentation that may help. [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by Rekka on 2008-12-14
thanks for the article.... unfortunately, it wasn't much help... could anyone point me in the right directions?

---

### Post by LostAngel on 2008-12-14
I tried forcing, and got this:

ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

---

### Post by albinootje on 2008-12-14
> **The Clown said:**
> After typing the first line into the prompt, I get the error message mkdir: cannot create directory `/media/sdb1': File exists

That's a harmless message that you can ignore.

---

### Post by The Clown on 2008-12-19
Sorry for the lull in responses...finals week and all.

lsusb gives:

Bus 007 Device 002: ID 0000:0000  
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Trying a force mount gives:

ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

Which, again, seems to conflict the terminal's previous sentiment that sdb1 already exists.

---

### Post by albinootje on 2008-12-19
> **The Clown said:**
> 
Trying a force mount gives:

ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

Which, again, seems to conflict the terminal's previous sentiment that sdb1 already exists.

Can you post the output of :
```

sudo fdisk -l
dmesg|grep sd

```

It is possible, when using more than 1 usb-disk or usb-stick, that it "moved" to /dev/sdc1 or /dev/sdd1

---

### Post by The Clown on 2008-12-19
> **albinootje said:**
> Can you post the output of :
```

sudo fdisk -l
dmesg|grep sd

```

It is possible, when using more than 1 usb-disk or usb-stick, that it "moved" to /dev/sdc1 or /dev/sdd1

First command:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   de  Dell Utility
/dev/sda2   *          14        1319    10485760    7  HPFS/NTFS
/dev/sda3            1319       15546   114277368    7  HPFS/NTFS
/dev/sda4           15547       19458    31415748+   f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown
/dev/sda6           15547       18977    27559476   83  Linux
/dev/sda7           18978       19130     1228941   82  Linux swap / Solaris

Partition table entries are not in disk order

Second command:

> [12932.950308] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.951305] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.951309] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.952307] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.952311] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.953310] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.953314] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.954677] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.954680] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.955677] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.955681] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.956733] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.956737] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.957680] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.957683] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.958680] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.958683] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.959676] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.959679] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.960681] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.960685] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.961679] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.961683] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.962677] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.962681] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.964182] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.964186] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.965180] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.965184] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.966177] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.966181] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.967184] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.967187] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.968181] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.968185] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.969181] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.969185] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.970180] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.970184] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.971181] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.971185] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.972180] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.972184] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.973181] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.973185] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.974304] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[12932.974308] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[12932.975304] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 


It goes on like that for quite a while.

---

### Post by The Clown on 2008-12-20
Is there nothing I can do now?

:(

---

### Post by albinootje on 2008-12-20
> **The Clown said:**
> Is there nothing I can do now?

:(

Does your usb disk work in other machines and/or at friends ?

And can you shorten the repititive output in the #34 posting a bit ? Thanks.

---

### Post by The Clown on 2008-12-20
Yeah, I've used it on a bunch of different machines. It works in Windows and Mac, but not Ubuntu.

---

### Post by albinootje on 2008-12-20
> **The Clown said:**
> Yeah, I've used it on a bunch of different machines. It works in Windows and Mac, but not Ubuntu.

Can you file a bug-report about this at [http://launchpad.net](http://launchpad.net) ?

---

### Post by The Clown on 2008-12-20
> **albinootje said:**
> Can you file a bug-report about this at [http://launchpad.net](http://launchpad.net) ?

Sure.

---

### Post by dmainou on 2008-12-21
Hi Guys,

Same situation: External USB 320 GB Seagate drive working perfectly under vista (which I'll never ever touch again). It has my life in it as it contains the backup I did before switching to kubuntu2 days ago.

Sorry fro the engrish..... as it is my 2nd language....

sudo mount:

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda4 on /boot type ext3 (rw,relatime)
/dev/sda5 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
[COLOR="Blue"]/dev/sda1 on /media/VistaOS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/external type vfat (rw)[/COLOR]



sudo fdisk -l:


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf95434fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3882    31182133+   7  HPFS/NTFS
/dev/sda2            3883        4125     1951897+  82  Linux swap / Solaris
/dev/sda3            4150       14593    83891430    5  Extended
/dev/sda4            4126        4149      192780   83  Linux
/dev/sda5            5403       14593    73826676   83  Linux
/dev/sda6            4150        5402    10064659+  83  Linux

Partition table entries are not in disk order

[COLOR="Blue"]Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    c  W95 FAT32 (LBA)[/COLOR]


sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs -o force
[COLOR="Blue"]ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.[/COLOR]

So its there but I don't know how to mount it. I think I know my problem... it seems to be a fat32 format and I'm trying to mount an ntfs drive... could you please help me?

Thanks

---

### Post by albinootje on 2008-12-21
> **dmainou said:**
> 
/dev/sdb1 on /media/external type vfat (rw)[/COLOR]

So its there but I don't know how to mount it. I think I know my problem... it seems to be a fat32 format and I'm trying to mount an ntfs drive... could you please help me?


It seems to be mounted correctly on /media/external already.
Can you verify that ?

Or do need to have /dev/sdc1 mounted ?
That is not in your "mount" output as posted.

What gives :
```

sudo mkdir /media/sdc1
sudo mount /dev/sdc1 /media/sdc1 -t vfat

```

---

### Post by Tsume on 2008-12-21
I've got the same problem as most of the people here, same message spammed all up in my dmesg, same Iomega bridge controller as one poster had...

None of these mount commands are going to work because /dev/sdb and /dev/sdb1 etc etc don't exist, there is only sda which is the main ide drive inside the laptop.  How should I post the bug report?  I don't know what information to include in it.  I do know that if I post the report "my drive isnt working with ubuntu 8.10 fix it" with no information for the developers it will most certainly not be fixed :)

Edit:  Bug report is here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302960](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302960)  Everyone comment / nominate so it gets noticed and fixed :)

---

### Post by dmainou on 2008-12-22
> **albinootje said:**
> It seems to be mounted correctly on /media/external already.
Can you verify that ?

Or do need to have /dev/sdc1 mounted ?
That is not in your "mount" output as posted.

What gives :
```

sudo mkdir /media/sdc1
sudo mount /dev/sdc1 /media/sdc1 -t vfat

```

Thanks a lot.... I got done with vista and decided to try kubuntu. Lovingi it with the exception of this little mishap.

Was able to mount it and able to browse it through terminal and by digging into root. Unable to edit as root owns it.

Was unable to make it appear into the main screen of dolphin.

How do I make it to auto mount and editable by my user and be shown on dolphin? 

Thanks

D

---

### Post by bnleez on 2008-12-22
I am having similar problems.  This is what I am getting when I try to force a mount:

~$ sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs -o force
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

Any advice?

---

