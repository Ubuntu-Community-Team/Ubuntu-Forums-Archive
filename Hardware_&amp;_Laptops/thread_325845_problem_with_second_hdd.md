---
title: "problem with second hdd"
date: 2006-12-26
forum: Hardware &amp; Laptops
---

### Post by goodall on 2006-12-26
Just got a new 500GB SATA HDD for christmas, along with an external hdd enclosure (needed as im running a small form factor box) now bearing in mind im a noob when it comes to linux,  i did try following a rough guide on formattign it, partitioning it and using it etc... well i can mount the drive and it shows up on my desktop, however when i try and use it, odd things happen, such as files or folders disappearing aftter a reboot, and also files just not wanting to write to the disk (I/O error) i was hoping somone could give me a bit of a hand, in solving the problem, or even telling me how to start again and get it right. 

PS, i am wanting to use a fat32 file system rather than ext3 as i wish to plug the external hdd into a friends windows machine occasionaly.

---

### Post by dannyboy79 on 2006-12-26
what did you use to format it? it's possible that files are disappearing when you reboot because if you didn't add a fstab entry then you'll have to remount it each time you start up your computer! what are the permissions on the folders that you are trying to write to?? what options are you using to mount the fat32 or vfat partition? there is another thread that talks about trouble wrtiing to vfat in this forums, just use the search function and find it. if you post the info I need as well as the output from sudo fdisk -l, as well as sudo cat /etc/fstab. I can help ya. make sure you do the fdisk command after you have the external drive plugged in and powered on. not neccessarily mounted. oh yeah, also please do a sudo mount and post that output as well. thanx

---

### Post by goodall on 2006-12-26
i formatted in the teminal, it sounds like the fstab entry will be the problem, in the premissions it says im the owner of the files/folers, and that i can read write and execute, however groups and others can do none of these.

```
Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32       19929   159830685    5  Extended
/dev/hda5              32       19929   159830653+  8e  Linux LVM

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux


```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0    1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

```
/dev/mapper/Ubuntu-root on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/hda1 on /boot type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/data type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

```

thanks for the help so far

---

### Post by dannyboy79 on 2006-12-27
most likely that's it, just add this entry in your fstab

/dev/sda1       /media/data        vfat   rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0       2

The  sixth  field,  (fs_passno),  is  used by the fsck(8) program to
       determine the order in which filesystem checks are  done  at  reboot
       time.   The  root filesystem should be specified with a fs_passno of
       1, and other filesystems should have a fs_passno of 2.   Filesystems
       within a drive will be checked sequentially, but filesystems on dif&#8208;
       ferent drives will be checked at the same  time  to  utilize  paral&#8208;
       lelism available in the hardware.  If the sixth field is not present
       or zero, a value of zero is returned and fsck will assume  that  the
       filesystem does not need to be checked.

if i were you though, I would randomly check your fat filesystem using fsck once in awhile. never do this to a mounted filesystem though, umount it first. good luck

---

### Post by goodall on 2006-12-30
still no luck even with that fstab entry, i have had a play around with the fstab and tried setting it up myself from a guide i found, but the best result i got was that i was able to use the drive as i would have liked, however the test folder i had used was still there, and couldnt be deleted r have files placed in it. also now i get told that my device is read only somtimes.

---

### Post by dannyboy79 on 2007-01-02
post your new fstab entry so I can see what you are trying. if you use what I posted you should have no problems as I don't have any issues writing to it! let me know.

---

### Post by goodall on 2007-01-02
current fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1 /media/data vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid =1000,umask=077,iocharset=utf8 0 2

```

hdd doesnt mount automaticaly, and when viewed through a sudo nautilus, it is displayed as 465.8GB volume, and when i try to acces it i get the error Unable to mount the selected volume. [mntent]: line 10 in /etc/fstab is bad

mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab


when looking in the disks manager the drive is set as inaccesable and pressing enable does nothing

also could you explain the quiet, shortname, uid, gid, umask and iocharset options please

---

### Post by dannyboy79 on 2007-01-02
ok, I just relooked at my fstab and this is what is states:
/dev/hdb1       /home/daniel/fat32      vfat    rw,uid=1000,gid=1000,iocharset=utf8,umask=0000  0       0

I don't know where I got that other stuff from that I suggested? also, make sure that after each entry you hit the tab button once, then start typing the next thing. so you would type /dev/sda1 and then hit tab, then type /media/data and so on. if you want to learn about the various mount options just do either man fstab or man mount within a terminal and you can read all about it. i could explain it but it's better for to learn it yourself. plus I just noticed that you posted your sudo fdsik -l and it states that sda1 is formatted as linux. so this means that you formatted it either ext2 or ext3 I believe so instead of putting vfat you need to make it whatever you formatted it as most likely ext3. I will tell you though, if your goal was so that you could store data on this drive and be able to reference it from windows on a dual boot machine, I would have used fat32. i have heard about a driver for windows though that allows windows to be able to access ext3 partitions so could look into that. let me know what happens. also, after the last entry on the last line of your fstab, hit enter so the cursor goes to the next line. also, after update your fstab you don't need to reboot, just type in sudo umount /dev/sda1 and it'll say sda1 not mounted. then do sudo mount -a and it'll attempt to view your fstab and mount everything within your fstab which should then mount your new sda1 drive.

---

### Post by goodall on 2007-01-03
hmmm, not sure whats going on with this hdd, definitely formatted it under vfat, but more wierd things are going on now, the sda has became sdb now, not sure how, and more stuff isnt working, what is the best way to completely start over with this hdd, and just go with ext3, as it seems load of people have problems with vfat, hooking the hdd up to a windows box would have been nice, but isnt essential, just getting it working would be awesome.

---

### Post by dannyboy79 on 2007-01-03
it depends really, if you have gparted installed then go to a terminal and type in gksudo gparted and then when the gui comes up, just basically delete your parititon you don't want, create a new one and then format it as ext3. or you could stick with fat32 by formatting it using a windows machine. you said you used the command line b4 to format it, what exactly did you type in do you remember? here are some tutorials if you need help and still want to use the command line. they talk about qtparted, this is just another gui for partitioning but it uses the qt libraries instead of gnome libraries. good luck

---

### Post by goodall on 2007-01-04
deleted everything in gparted, and tried to make a new partition using all available space, but got this message 8 minutes in

mke2fs 1.38 (30-Jun-2005)
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while  creating root dir

now my hdd has 1 partition but the filesystem is unknown, and is sdb rather than sda, any idea whats going on?

---

### Post by goodall on 2007-01-10
can anyone help?? dont want to have wasted the cash.

---

