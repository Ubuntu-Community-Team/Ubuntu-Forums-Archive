---
title: "WD USB HD problems"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by clarke.rainey on 2005-05-09
Well when I first bought the HD it was formatted as Fat32 LBA out of the box... when I would plug it in, it would automount, an icon would appear on my desktop, and the user that I use would have ownership of the drive... I recently formatted it as EXT3 and all of the previous usability dissapeared... now that I have formatted it back to fat32 LBA, I have to manually mount the drive and each time its owner is always root and I cannot use GUI to move files from my home directory into it and it has become very annoying... does anyone have any idea how to get it back to being how it was in the first place?.. do I need to format it on a windows machine as fat32 instead of doing it through linux?.. any ideas that you have would be very helpful because I am meeting up with my brother in Europe while he has leave from Iraq and he wants all the TV shows and such that he has missed while gone that I have sitting on my computer for him and he uses Windows on his laptop... 

Thanks alot!..

---

### Post by lt_kije on 2005-05-09
Can you post your /etc/fstab for us? I bet you need to modify that file, especially if you're having trouble mounting the drive as a regular user.

lt_kije

---

### Post by clarke.rainey on 2005-05-09
Um... this is going to make me sound really stupid... but I did a restart of gnome without restarting the computer and it works now... I just found it automounted on my desktop... kinda scary but I won't doubt it much... I am going to do some tests to see if this was a one time thing or a permanent solution...

---

### Post by clarke.rainey on 2005-05-13
Well the problem is back... and now it is also affecting my 20GB USB mp3 player that has always worked correctly... and I saw that you said that you wanted to see my fstab... but what does the fstab have to do with drives that are constantly pluged and unplugged but not always plugged in at boot?..

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           reiserfs defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdb1       /mnt/120GB              reiserfs defaults       0       2
/dev/hdc1       /mnt/80GB               reiserfs defaults       0       2
/dev/hdd1       /mnt/200GB              reiserfs defaults       0       2
```

---

