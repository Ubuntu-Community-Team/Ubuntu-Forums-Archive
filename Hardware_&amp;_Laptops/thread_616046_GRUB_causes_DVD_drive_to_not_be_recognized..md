---
title: "GRUB causes DVD drive to not be recognized."
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by Battlemarz on 2007-11-17
I have tried several different installs with Gusty and even tried Fedora to make sure it wasn't a distro related problem and whenever i use GRUB as the boot loader my DVD drive is unseen by linux and by my XP install.

Fixing the MBR in XP brings the drive back and LILO does not cause the drive to go missing. I would like to know if someone knows what causes GRUB to not initialize the DVD drive as i would much rather use GRUB as opposed to LILO.

Drive is a Pioneer DVR-k16rs and so far the only fix i have found involves using LILO, but i have yet to get LILO booting to an external hard drive whereas GRUB does it easily and would like to both be able to boot form external drive and use DVDs.

---

### Post by logos34 on 2007-11-17
I don't think this has anything to do with the bootloader per se, although I could be wrong.  Most likely it's due to a wrong fstab entry or missing device links.  Post the output for the following:

cat /etc/fstab

and

ls -l /dev | grep dvd

(they should be pointing to same drive as cdrom and cdrw do.)

---

### Post by Battlemarz on 2007-11-18
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb4
UUID=853b9a71-a952-459f-8726-afd671367804 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=b5322dc9-16ac-49e0-ae7f-bd6da8d08edf /boot           ext3    defaults        0       2
# /dev/sda1
UUID=C6046E6F046E6283 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb3
UUID=7fb01d52-0219-42d2-8192-aee1363f324a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

ls -l /dev | grep dvd returns nothing

Also, when attempting to mount DVD drive i get "mount: special device /dev/scd0 does not exist"

---

### Post by logos34 on 2007-11-18
you should have something like this:

> $ ls -l /dev/ | grep dvd
lrwxrwxrwx 1 root   root           3 2007-11-18 16:58 **dvd -> scd0**
lrwxrwxrwx 1 root   root           3 2007-11-18 16:58 **dvdrw -> scd0**

$ ls -l /dev/ | grep cd
lrwxrwxrwx 1 root   root           3 2007-11-18 16:58 **cdrom -> scd0**
lrwxrwxrwx 1 root   root           3 2007-11-18 16:58 **cdrw -> scd0**
brw-rw---- 1 root   cdrom    22,   0 2007-11-18 10:58 **scd0**

so maybe you just need to create symlinks to 'x-special/device-block' scd0 in /dev folder

**sudo ln -s /dev/scd0 /dev/dvdrw**

etc.  Do that for each one

---

### Post by meierfra on 2007-11-18
> whenever i use GRUB as the boot loader my DVD drive is unseen by linux and by my XP install.


logos34: There must be something else going on if XP no longer sees the DVD drive.

---

### Post by logos34 on 2007-11-18
> **meierfra said:**
> logos34: There must be something else going on if XP no longer sees the DVD drive.

well, any ideas?

The debian installer recognized the optical drive, otherwise there'd be no fstab entry.  But apparently there's no 'scd0' in the /dev folder (i.e. error message).  Just drops off the radar screen.

lshw -C disk 

would show whether or not the cd/dvd device is still being detected at all.  

And why would grub cause windows not to see it?

---

### Post by meierfra on 2007-11-18
```
well, any ideas?
```

 Just wanted to make sure  you noticed the XP doesn't recognize the DVD drive
(although you seemed to be  one of the few people around here who take their  time to read  a thread carefully, so I seriously doubt that you hadn't noticed)


Well, maybe one idea:

>  Fixing the MBR in XP and LILO does not cause the drive to go missing. 

Could it be that there is some information about the DVD in the MBR, or maybe in the first 63 sectors of the harddrive?
One of the differences between LILO  and  Grub is, that  Grub uses   the first few sectors to install the stage 1.5 files. On the other hand the  stage 1.5 files don't seem to be really necessary.  So if there is a way to install grub to the MBR but not install the 1.5 files, that might be worth a try.  But I admit, this is a long shot.

---

### Post by logos34 on 2007-11-18
actually I was fixated on the linux side, so I'm glad you reminded me of the xp part.

> One of the differences between LILO and Grub is, that Grub uses the first few sectors to install the stage 1.5 files. On the other hand the stage 1.5 files don't seem to be really necessary. So if there is a way to install grub to the MBR but not install the 1.5 files, that might be worth a try. But I admit, this is a long shot.

didn't know that...although I thought 1.5 was necessary...never tried installing without the stage1.5 file so I have no idea how this would work.

I wonder if GAG would be an option (and boot from USB, like the guy wants)?

---

### Post by meierfra on 2007-11-18
Battlemarz: Did you try installing grub to the MBR of the external drive?

(Edit: Posted this before I saw Logos34 preceding post)

---

### Post by meierfra on 2007-11-18
> I didn't know that...although I thought 1.5 was necessary...never tried installing without the stage1.5 file so I have no idea how this would work.

It should work without the stage1.5. I often install grub to a partition and then the stage1.5 files are not used.

---

### Post by Battlemarz on 2007-11-18
I have not yet tried installing GRUB to the external, I am able to boot from it so i suppose i will try that once i get time to reinstall. I'll update tomorrow on whether i am able to boot GRUB from external and still have DVD drive active.  
On another note, if i do use GRUB on external drive, will it still be able to see my XP install and choose to boot from it? Or will i have to change the BIOS boot order when i want to boot XP opposed to Ubuntu?

And thanks for the replies, hopefully this can get figured out soon, i know I have seen at least two other people having this problem with GRUB so its not just me doing something goofy.:)

I will also try GAG tomorrow if booting to the MBR of external doesn't work.

---

### Post by meierfra on 2007-11-18
You can add Window's to the grub menu. 

Is Ubuntu currently install on the external drive? Then you just would have to reinstall grub and edit /boot/grub/menu.lst.

If you are doing a fresh install of ubuntu, I recommend to disconnect all other  hard drives during the install. Ubuntu/Grub sometimes gets confused with the hard drives, when you try to install grub to an external  drive.
 
Obviously you will have to set  the bios to  boot from the internal hard drive.  

The only disadvantage of disconnecting the other hard drives is that you will have to manually add windows to the grub menu once you successfully booted into ubuntu:

In a terminal type
```
gksudo gedit /boot/grub/menu.lst
```

to open the file "menu.lst"

add this to the end of the file

> 
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


This assume that you only have one hard drive other than the ubuntu drive and that  windows is on the first partition of the internal drive. Otherwise you have to modify the numbers accordingly.

---

### Post by Battlemarz on 2007-11-18
Thanks Meierfra, that will save me some time. I have a feeling though that it will still not solve my problem of being able to see my DVD drive.

---

### Post by meierfra on 2007-11-29
> I have a feeling though that it will still not solve my problem of being able to see my DVD drive.


I have come to the same conclusion. My theory that the problem is caused by the stage1.5 files is nonsense ([ see this thread, start at post #6]("http://ubuntuforums.org/showthread.php?t=528216#6")) 

Anybody knows how grub could cause the DVD drive to disappear in Windows? Is a boot loader also in charge of loading the DVD drive?

---

### Post by vonchiz on 2008-01-24
I had this same problem and couldn't get anyone to answer my posts so I'm searching for all with the same problem.  It was a bear to fix, but here's how I did it.

From what I could tell, grub doesn't play nice with some removable laptop drives.  I tried several 3rd party boot loaders and either the problem replicated or Grub wouldn't boot linux.  

Step 1.  Replace Grub with Lilo as loutlined here
[http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)
I used the apt-get option to install Lilo, the directions are good.
MAKE SURE you install Lilo on your Ubuntu partition and not on your MBR.

Step 2.  Install GAG as my bootloader.  Very straightforward.  Linux won't boot if you have your bootloader installed on your MBR.

If you know how to install grub on your linux partition and not MBR, it would work also.  I got sick of #($%ing around with it and switched to Lilo.

Hope this helps.

---

### Post by akiragtr on 2008-06-24
I have the same problem (Lenovo 3000 N200). My cdrom is detected as /dev/scd0 only if I use acpi=off. But at Windows it is still not detected (off course).

I'll try to install LILO right now.

---

### Post by akiragtr on 2008-07-06
LILO fixed my problem.

---

