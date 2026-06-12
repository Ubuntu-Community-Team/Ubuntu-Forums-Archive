---
title: "usb drive"
date: 2008-07-29
forum: Hardware
---

### Post by stompy11 on 2008-07-29
my flash drive won't work when I plug it in it says 
**Cannot mount volume.**
Invalid mount option when attempting to mount the volume.

now it used to work.

---

### Post by tuxxy on 2008-07-29
Have you tried to manually mount it

---

### Post by stompy11 on 2008-07-30
yeah same thing.

---

### Post by tuxxy on 2008-07-30
Have you recently upgraded to Hardy, if so it may be solved by editing your fstab, this post may help

[http://ubuntuforums.org/showthread.php?t=574988](http://ubuntuforums.org/showthread.php?t=574988)

---

### Post by stompy11 on 2008-07-30
sounds interesting
btw, I am new to ubuntu.
I will try to figure it out.

---

### Post by stompy11 on 2008-07-30
how do you fstab?

---

### Post by tuxxy on 2008-07-30
SHould be located at /etc/fstab/

Open a terminal and enter this command, it will open the fstab in text editor, make sure you know what you are doing before eidting the contents.

```
gedit /etc/fstab
```

---

### Post by stompy11 on 2008-07-30
this is what i got
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5fdc9443-6905-4eda-8de4-6403ceec046a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d6e7d9bc-8170-4e6f-a08c-cbd91414dcb6 none            swap    sw              0       0
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by stompy11 on 2008-07-30
yeah so i dont know what to do from here

---

### Post by stompy11 on 2008-07-30
some one please help me

---

### Post by lostdave on 2008-07-30
Stupid question...
you have tried said USB Drive on a different PC haven't you?

Try and comment out the last line of your fstab file : save and exit 
then type```
 sudo mount -a 
```
then try your usb stick again...if that doesn't work reboot, then try again...if that doesn't work...:: shrug ::

---

### Post by stompy11 on 2008-07-30
by comment out do you mean just deleting the last line

---

### Post by lostdave on 2008-07-30
put a # infront of it rather than delete.
That way if it does break somthing, you can easily reverse it

Dave

---

### Post by stompy11 on 2008-07-30
it says i dont have permission to save

---

### Post by lostdave on 2008-07-30
try
```

sudo gedit /etc/fstab

```

---

### Post by stompy11 on 2008-07-30
thanks it all works now :)

---

### Post by stompy11 on 2008-07-30
ok so now my secondary hdd wont mount

---

### Post by lostdave on 2008-07-30
not knowing the full setup of your particular system, it is hard to say...

---

### Post by stompy11 on 2008-07-30
ok I have two hard drives both in sata. primary is wd 150 gb raptor, second is 750 gb seagate. it was working right up until the fstab change, I tried to change it back but no use, i also restarted.

---

