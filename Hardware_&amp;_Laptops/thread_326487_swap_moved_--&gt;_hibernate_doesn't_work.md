---
title: "swap moved --&gt; hibernate doesn't work"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by straki on 2006-12-27
dear community! :p 

I used the gparted Live-CD to grow my windows ntfs partition and so I had to move my ubuntu-swap. 

First hibernate said "Can't allocate memory" or something similar,

and now it says

wsusp: cannot find swap device, try swapon -a. 

Typing swapon -a in a console outputs 

swapon: cannot stat /dev/disk/by-uuid/38c6fe0b-5a65-41ab-8bb5-79426dc9ca8e: No such file or directory

Here is my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=2d6456a4-7769-43d0-af60-4747a18d6328 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda4
UUID=f5ce981b-f4e2-4694-b1e9-6f92f515d79b /home           ext3    defaults      
  0       2
# /dev/hda1
UUID=1A54ED3154ED1075 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46
 0       1
# /dev/hda2
UUID=38c6fe0b-5a65-41ab-8bb5-79426dc9ca8e none            swap    sw            
  0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

and here the output of parted -- print

Disk /dev/hda: 79.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  11.7GB  11.7GB  primary  ntfs         boot 
 2      11.7GB  13.8GB  2147MB  primary  linux-swap        
 3      13.8GB  20.1GB  6317MB  primary  ext3              
 4      20.1GB  79.6GB  59.5GB  primary  ext3 

(the 3rd is the root partition, 4 is for /home)

thank you. I really appreciate any kind of help!

---

### Post by taurus on 2006-12-27
Every time you move or resize swap, the UUID would change so the current one in /etc/fstab is not valid anymore.  Therefore, you need to edit your /etc/fstab

Applications -> Accessories -> terminal
```
gksudo gedit /etc/fstab
```
and remove this line
```

UUID=38c6fe0b-5a65-41ab-8bb5-79426dc9ca8e none swap sw  0  0

```
and replace it with
```

/dev/hda2   none   swap   sw   0   0

```
and save it.  Then, remount the whole thing with
```
sudo mount -a
free
```

---

### Post by straki on 2006-12-27
thanks for the quick reply.

I did the changes to /etc/fstab and ran 

```
sudo mount -a
free
sudo swapon -a
```

and now I can hibernate again!!! YAAAAY!!! :mrgreen: 

All right. I'm going to hibernate now. Good night! And thanks a lot!

---

### Post by taurus on 2006-12-27
Well, it's the right season to hibernate too.  Make sure you eat a lot before you go and find yourself a corner to hibernate...

---

### Post by groggyboy on 2007-01-19
:p 

(thanks, it helped me too)

---

### Post by ryofire on 2008-04-09
WOOT!! you just made my life easier too. \\:D/

---

### Post by TerpInHotLanta on 2008-04-25
I'm actually surprised that you were able to hibernate again following those steps being that you didn't mention editing the /etc/initramfs-tools/conf.d/resume file.

Here are steps to definitely get hibernate working after using GParted

1) ```
sudo vol_id --uuid /dev/sda2 
```

(or whatever your swap partition is -- if you don't know, use sudo fdisk -l)


2) ```
sudo nano /etc/fstab
```

edit your /etc/fstab file so that the swap line looks like
```
#/dev/sda2
UUID=422690ed-1266-47d4-a2a7-d54370f184d4	none	swap	sw	0
```

Note: you'll need to update the UUID with whatever was spit-out in step #1

3) edit your /etc/initramfs-tools/conf.d/resume file so it looks like
```
RESUME=UUID=422690ed-1266-47d4-a2a7-d54370f184d4
```

using the UUID that you got in step 1)

(This is the file that tells the computer where to look for the previous desktop state [i.e. swap-space] upon resuming from hibernate -- just thought I'd clarify for those who are n00bs/suspicious of random commands and files)

4) ```
sudo update-initramfs -u
```
(this updates the boot-up scripts with the new information)

5) Restart your system and you should be good to go

Hope this helps people who were stuck as I was after using GParted.

-Charlie

---

