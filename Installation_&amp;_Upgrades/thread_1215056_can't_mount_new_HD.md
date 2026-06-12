---
title: "can't mount new HD"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by renihanc on 2009-07-16
[SIZE=2]**what am I doing wrong**???[/SIZE] 			 		   		 		 		[SIZE=2]can't access 2nd HD  heres what i got

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=1788b772-47b4-477c-aa1d-b4120c9d0d2e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=12866ed1-bfc2-4535-a14f-61b07a9db708 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1    /media/stgdrv    ext3,defaults        0    0


heres my fdisk if that helps

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x79627962

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       30401   109989022+   5  Extended
/dev/sda5           16709       29839   105474726   83  Linux
/dev/sda6           29840       30401     4514233+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux


then somone suggested;


/dev/sdb1 /media/stgdrv ext3 relatime 0 1

in fstab.... could not mount.

then i tried in terminal

chris@chris-desktop:~$ sudo mount -t ext3 /dev/sdb1 /media/stgdrv
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so




yes I have rebooted each time after changing fstav


anyone else got any suggestions ????[/SIZE]

---

### Post by merlinus on 2009-07-16
Hi again.  If you don't mind my saying so, it would be best if you had kept all this in one thread, rather than three.  Then folks searching for help for similar problems will have an easier time following what to do.

I suggest you try to run chkdsk <drive letter>: /f in windows (substitute the actual drive letter, probably d), as that may fix the problem.  Then shut down windows, fire up ubuntu, and see if you can mount it.

---

### Post by iponeverything on 2009-07-16
If its a new drive, have you formated it?

```
mkfs.ext3 /dev/sdb<your partion here>
```

---

### Post by lukeiamyourfather on 2009-07-16
If its a new drive that has never been used it'll need to be formatted and partitioned first. I'd suggest using GParted for that. Its not part of the default installation (why, FGS?) but can be installed with:

```
sudo apt-get install gparted
```

Once its installed it can be run with:

```
sudo gparted&
```

Close the terminal and continue on. Format the drive as needed and it'll even add the necessary entry to /etc/fstab so it mounts at boot to wherever you want. I usually use the terminal when possible but for adding a new drive its much easier to use GParted. Cheers!

---

### Post by merlinus on 2009-07-16
Did you guys look at the results of sudo fdisk -l?  Obviously sdb1 is formatted!!!

---

### Post by renihanc on 2009-07-16
it's not a new drive, but is a drive I had used. I use gparted and formatted it in ext3. Windows will not recognize because it's in ext3. 


man.... I thought this was gonna be a simple thing that I had not done, but I'm even stumping you guys.  


anybody else got any ideas ????

thanks everyone... I do appreciate your effort !!!!

---

### Post by merlinus on 2009-07-16
From the error messages whilst trying to mount it, there would seem to be problems, e.g. bad blocks. The hdd may now have defects.

You can try running fsck on it (use the man pages for options), but if there is nothing important on it, why not reformat with gparted and see what happens?

---

### Post by renihanc on 2009-07-16
I had reformatted it. It was originally my boot drive so i repartioned it and the reformatted it. Will try again though.

---

### Post by lukeiamyourfather on 2009-07-16
> **merlinus said:**
> Did you guys look at the results of sudo fdisk -l?  Obviously sdb1 is formatted!!!

Gold star for asserting your dominance, but that doesn't actually help the original poster.

Grab the UUID of the disk from GParted and use it with this line in your /etc/fstab since its already formatted. Using the UUID is more "fool proof" if you ask me since that doesn't change if drives are removed or rearranged.

```
UUID=YOUR_UUID_GOES_HERE     /WHATEVER_PATH_YOU_WANT     ext3     defaults     0     3
```

The last digit, 3, is the order in which the drives are checked if the system doesn't shutdown properly. So if its your second drive put a 2, or third drive put a 3, etc. If you don't want it checked then put a 0 if I remember right. Somebody correct me if that's wrong. 

If it still doesn't mount I'd try it in another system to see if its the hardware, or maybe try to format it and partition it again. Cheers!

---

### Post by merlinus on 2009-07-16
I hate to rain on your parade, but I seriously doubt that changing to UUIDs will resolve the problems indicated in an earlier post in this thread whilst the OP was trying to manually mount the partition:

[SIZE=2]mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error

Of course, I could easily be completely mistaken.  :)
[/SIZE]

---

### Post by renihanc on 2009-07-16
ok !!!!!!!  got it mounted..... 

I reformatted and rebooted but that didn't do it.

so I did this;

sudo mount -t ext3 /dev/sdb1 /media/stgdrv

it then mounted but i can't copy or move files to it.  I get...

Error opening file '/media/stgdrv/


I believe i'm half way there...... sweeeeeet ....

now what do I do ????

---

### Post by merlinus on 2009-07-16
Excellent!

```
gksu nautilus
```

Navigate to the mountpoint, rightclick, properties, permissions.  Change to your liking.

---

### Post by renihanc on 2009-07-16
I don't mean to sound stupid (but i am).

I typed

gksu nautilus

it flashed starting administrative application and the stopped. 

is this an app i need to dl ???

I go to that /media/stgdrv    and it is grey (won't allow me to change)

were almost there..... I can feel it !!!

---

### Post by merlinus on 2009-07-16
Nautilus is the file browser for ubuntu.  gksu nautilus should open it with root privileges, so you can change permissions.  It will ask for your password.

Alt+F2 will open a window where you can type gksu nautilus.

You can also try

```
gksudo nautilus
```

---

### Post by renihanc on 2009-07-16
YOU ARE THE MAN !!!!!! 


it works..... i realllllly appreciate everybodies input !!!!
one final question .......


when i reboot will i have to remount or change fstab at all ??


thanks again everyone.

---

### Post by merlinus on 2009-07-16
What is the current listing for /dev/sdb1 in /etc/fstab?

---

### Post by renihanc on 2009-07-16
here it is

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=1788b772-47b4-477c-aa1d-b4120c9d0d2e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=12866ed1-bfc2-4535-a14f-61b07a9db708 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1    /media/stgdrv    ext3,relatime    0    1

or do i need to change to this ????

/dev/sdb1 /media/stgdrv ext3 defaults 0 2

thanks

---

### Post by merlinus on 2009-07-16
At this point, since you changed permissions, you might simply try rebooting and see if the drive mounts automatically.

If it does not, then change it.

---

### Post by renihanc on 2009-07-16
thanks again for the help. I want to tell you that i appreciate you helping out newbies like myself. THAT is the reason I switched to Ubuntu. give your self an "attaboy" you did good.

sincerely

Chris

---

### Post by merlinus on 2009-07-16
Glad things are working.  Have fun, and post back if you run into difficulties.

---

