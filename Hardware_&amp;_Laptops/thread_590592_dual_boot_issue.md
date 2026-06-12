---
title: "dual boot issue"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by mrukus on 2007-10-24
just got dual boot to work.  when i partitioned the harddrive during the linux install i gave linux 10G, xp10G and left the other 60 or so for both systems to use, which is what i wanted.  windows only sees its windows partion with the 60 G, which is fine, idc if windows can't read the linux partition, but ubuntu can only read its own partition and the windows partition, its not seeing the large spare memory file.  i formatted it in fat32, i thought ubuntu could read that......there were no error messages upon install and both os boot just fine. just not recognizing that partition.....

---

### Post by mrukus on 2007-10-25
help anybody?

---

### Post by taurus on 2007-10-25
Did you remember to mount that third partition, vfat, before you tried to access it?

```
sudo fdisk -l
```

---

### Post by mrukus on 2007-10-25
i ran that command, and this is what i got. i don't think i did, somebody tried to help me but assumed that i was a linux master.....i had no clue what he was saying...




Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        2491     9767520   83  Linux
/dev/sda3            2492        2734     1951897+  82  Linux swap / Solaris
/dev/sda4            2735        9729    56187337+   b  W95 FAT32

---

### Post by taurus on 2007-10-25
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda4   /media/sda4   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sda4
sudo mount -a
df -h
```
You should see your FAT32 partition mounted to /media/sda4 from the output of the last command.

---

### Post by mrukus on 2007-10-25
mrukus@mrukus-laptop:~$ sudo mkdir /media/sda4
mkdir: cannot create directory `/media/sda4': File exists

---

### Post by mrukus on 2007-10-25
i found this file, this might be what its refering too, can i just replace this line with the one you told me too

# /dev/sda4
UUID=4844-5A9E  /windows        vfat    defaults,utf8,umask=007,gid=46 0

---

### Post by taurus on 2007-10-25
> **mrukus said:**
> mrukus@mrukus-laptop:~$ sudo mkdir /media/sda4
mkdir: cannot create directory `/media/sda4': **File exists**

It just means you already have /media/sda4 so continue with the rest of the commands then.

```
sudo mount -a
df -h
```

---

### Post by taurus on 2007-10-25
> **mrukus said:**
> i found this file, this might be what its refering too, can i just replace this line with the one you told me too

# /dev/sda4
UUID=4844-5A9E  /windows        vfat    defaults,utf8,umask=007,gid=46 0

When you reformatted /dev/sda4, you changed the UUID so you need to replace the **UUID=4844-5A9E** with **/dev/sda4** now.

So, you can make it look like this 

```
/dev/sda4  /windows   vfat    defaults,utf8,umask=007,gid=46  0  0
```
if you wish.

---

### Post by mrukus on 2007-10-25
mrukus@mrukus-laptop:~$ sudo mount -a
mrukus@mrukus-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.2G  2.4G  6.4G  28% /
varrun                379M  104K  378M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb            379M   96K  378M   1% /proc/bus/usb
udev                  379M   96K  378M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1             9.8G  2.4G  7.5G  24% /media/sda1
/dev/sda4              54G   32K   54G   1% /windows
tmpfs                 379M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile
/dev/sda4              54G   32K   54G   1% /media/sda4

---

### Post by mrukus on 2007-10-25
whoops, i meant to write this up there, this is what i saw, this isn't the big one it looks like its the one that i put linux on.

---

### Post by taurus on 2007-10-25
> **mrukus said:**
> mrukus@mrukus-laptop:~$ sudo mount -a
mrukus@mrukus-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.2G  2.4G  6.4G  28% /
varrun                379M  104K  378M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb            379M   96K  378M   1% /proc/bus/usb
udev                  379M   96K  378M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1             9.8G  2.4G  7.5G  24% /media/sda1
**[COLOR="Blue"]/dev/sda4              54G   32K   54G   1% /windows[/COLOR]**
tmpfs                 379M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile
**[COLOR="Blue"]/dev/sda4              54G   32K   54G   1% /media/sda4[/COLOR]**

You need to decide where you want to mount /dev/sda4 because you have it mount twice, one to /windows and one to /media/sda4!  So, edit /etc/fstab again and remove one line from it.  Save it and reboot.

```
gksudo gedit /etc/fstab
```

---

### Post by mrukus on 2007-10-25
allright, i rebooted and there is no difference the hdd still isn't being seen, this is what i have in my gedit page

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=4642d6b4-7ca6-4e15-9bc9-72b97c3a6698 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=CC701A20701A11B6 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
[COLOR="Blue"]# /dev/sda4
UUID=4844-5A9E  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1[/COLOR]
# /dev/sda3
UUID=4b345134-369b-469e-95b9-72a43b1cd518 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

should i replace that one so its being mounted on /media/sda4?

---

### Post by taurus on 2007-10-25
You need to look at my post #9 again.  In short, you need to replace the UUID thing with /dev/sda4.

---

### Post by mrukus on 2007-10-25
sorry about that. i did what you said in nine, then redid the other two commands you told me to do at the begining. but it still isn't showing up. heres what my stuff looks like now

mrukus@mrukus-laptop:~$ sudo mount -a
mrukus@mrukus-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.2G  2.4G  6.4G  27% /
varrun                379M  100K  378M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb            379M   96K  378M   1% /proc/bus/usb
udev                  379M   96K  378M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1             9.8G  2.4G  7.5G  24% /media/sda1
/dev/sda4              54G   32K   54G   1% /windows

and my other thing looks like this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=4642d6b4-7ca6-4e15-9bc9-72b97c3a6698 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=CC701A20701A11B6 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
/dev/sda4  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=4b345134-369b-469e-95b9-72a43b1cd518 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


thanks a bunch tarus for helping me out, sorry for all the trouble, i really appreciate it.

---

### Post by taurus on 2007-10-25
> **mrukus said:**
> sorry about that. i did what you said in nine, then redid the other two commands you told me to do at the begining. but it still isn't showing up. heres what my stuff looks like now

mrukus@mrukus-laptop:~$ sudo mount -a
mrukus@mrukus-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.2G  2.4G  6.4G  27% /
varrun                379M  100K  378M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb            379M   96K  378M   1% /proc/bus/usb
udev                  379M   96K  378M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1             9.8G  2.4G  7.5G  24% /media/sda1
**[COLOR="Blue"]/dev/sda4              54G   32K   54G   1% /windows[/COLOR]**



Actually, it's mounted to /windows.  What happens when you run this command from a terminal?

```
ls -la /windows
```

---

### Post by mrukus on 2007-10-25
mrukus@mrukus-laptop:~$ sudo ls -la /windows
total 36
drwxrwx---  2 root plugdev 32768 1969-12-31 19:00 .
drwxr-xr-x 22 root root     4096 2007-10-25 00:27 ..

thats all i got.  when i was installing ubuntu, the only options were /dos and /windows for that partition

---

### Post by taurus on 2007-10-25
> **mrukus said:**
> mrukus@mrukus-laptop:~$ sudo ls -la /windows
total 36
drwxrwx---  2 root plugdev 32768 1969-12-31 19:00 .
drwxr-xr-x 22 root root     4096 2007-10-25 00:27 ..

thats all i got.  when i was installing ubuntu, the only options were /dos and /windows for that partition

Basically, you can mount /dev/sda4 to anywhere you want.  Right now, you have it mounted to /windows so if you want to write stuff to that partition, you have to write to /windows.  Since it's a new partition, there shouldn't be anything in there right now.  

You are all set.

---

### Post by mrukus on 2007-10-25
so its not showing up under my computer because theres nothign written to it?  but i can still read and write to it in linux right?

---

### Post by mrukus on 2007-10-25
i just tried to save a picture off the web and it isn't one of my choice as a location

---

### Post by taurus on 2007-10-25
Yes, you can read and write to it.  If you want to have an icon on your desktop for that partition, then you need to edit /etc/fstab and replace the **/windows** with **/media/sda4**.  

Then reboot.

---

### Post by mrukus on 2007-10-25
will windows still be able to read it?

---

### Post by mrukus on 2007-10-25
one last question you might no the answer to before i leave, after i updated my ubuntu after installing it, my grub offers me 4 different verisoions of ubuntu, 2 of which are restore versions. is one with the updates and the other without?  thanks a bunch man i really really appreciate this.  now i will be off searchign for drivers and learning new commands and try to tackle the task of learning linux while studying molecular and cell biology at college......fun times

ps. is it easy to rename the drives so they aren't sda4 and sda1, if its intense don't worry abotu it, i need to head off to bed soon, thanks a bunch man.

---

