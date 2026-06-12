---
title: "Windows drive in Linux machine?"
date: 2005-01-31
forum: Hardware &amp; Laptops
---

### Post by domzo on 2005-01-31
Hi,

I've got a drive (currently not in a machine) that contains some files I need to keep. It has Win98 installed on it, although the OS won't boot up. I know the files are ok as I can see them in DOS/SafeMode.

If I put this drive in my Linux box will I be able to get to the files? Do I need to go through any mounting process to see the drive? If so.. any tips?? I don't want to reformat the drive yet as I need the files...

Cheers
domzo

---

### Post by tim1 on 2005-01-31
This shouldn't be a problem if you follow these steps:

1) Put the harddrive in your computer
2) Boot up Ubuntu
If you have only one partition on the new harddrive there will be a new device called hdb1 in the /dev folder, if you have more there will be hdb2, hdb3 etc.
3) create a new folder whrere you want to mount the harddrive ( for example /mnt/win98), you'll need sudo for that
4) mount the harddrive with the following command:

sudo mount -t vfat /dev/hdb1 /mnt/win98

greets, tim

---

### Post by CowPie on 2005-01-31
[QUOTE=domzo]Hi,

I've got a drive (currently not in a machine) that contains some files I need to keep. It has Win98 installed on it, although the OS won't boot up. I know the files are ok as I can see them in DOS/SafeMode.

If I put this drive in my Linux box will I be able to get to the files? Do I need to go through any mounting process to see the drive? If so.. any tips?? I don't want to reformat the drive yet as I need the files...

Cheers
domzo[/QUOTE]
Yes, put in in your /etc/fstab with your favourite text editor:

/dev/hda1       /media/c        vfat    umask=000        0      0

Then sudo mdkir /media/c

Then mount -a

Or for one-time usage you can do 
   mount /dev/hda1 -t vfat /media/c 
but ensure /media/c exists!

Where it says hda1, that's just for me, maybe your hard drive is different.

---

### Post by domzo on 2005-01-31
Thanks both of you - I'll give that a whirl.

---

