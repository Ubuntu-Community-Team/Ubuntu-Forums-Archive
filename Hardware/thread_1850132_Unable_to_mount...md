---
title: "Unable to mount.."
date: 2011-09-25
forum: Hardware
---

### Post by sk8rjess on 2011-09-25
my laptop has dual hard drives. one is a 60gb ssd with 2 30gb partitions for ubuntu and windows, and the other is a 750gb storage drive. 
i formatted the 750gb in ubuntu, and it was working fine.
since i'm running ssd, in windows i have all my program files and stuff on my 750gb drive.it seems after i've done this, when i'm on ubuntu and try to access the drive it shows up as 2 partitions, and tells me 

```
Unable to mount Storage

Error mounting: mount exited with exit code 12: NTFS signature is missing.
Failed to mount '/dev/sdd2': Invalid argument
The device '/dev/sdd2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

i've wiped the drive clean, and tried it all again but did the exact same thing. 

what's the cause, and how can i fix this?

---

### Post by dave01945 on 2011-09-25
are you sure /dev/sdd2 is the correct drive and what is the exact command you are using to mount

---

### Post by sk8rjess on 2011-09-26
here's what i have
[http://img195.imageshack.us/img195/3669/screenshotcok.png](http://img195.imageshack.us/img195/3669/screenshotcok.png)

i haven't tried mounting from command line, but i have just tried clicking it in file explorer and using the disk utility.

it's a brand new drive, and i've formatted it and totally wiped it twice. no idea why ubuntu goes crazy over it

---

### Post by dave01945 on 2011-09-26
i would say try to mount it from command line and see what is say's.

to do that first you need to make a directory to mount it under

```
sudo mkdir /media/storage
```

then to mount it

```
sudo mount /dev/sdc1 /media/storage
```

then let us know what happens

also looking at that it does look like there may be a problem with the partition table because the numbers add up to be more than 750GB but try the above commands if they don't work it may be a good idea to try to format with the command line if you need help with that let us know

---

### Post by sk8rjess on 2011-10-02
well the device you listed(sdc1) isn't the correct one, so what i did was

```
sudo mount /dev/sdb /media/storage
The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.

```

and there's the message i got. now i'm able to view the files properly, but still can't seem to get rid of the 2 random "storage" devices.
[http://img847.imageshack.us/img847/787/screenshotqz.png](http://img847.imageshack.us/img847/787/screenshotqz.png)

---

