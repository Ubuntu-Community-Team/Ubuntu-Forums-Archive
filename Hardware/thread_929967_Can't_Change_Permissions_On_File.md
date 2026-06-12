---
title: "Can't Change Permissions On File"
date: 2008-09-25
forum: Hardware
---

### Post by Spaceman Spiff on 2008-09-25
Hey guys,
  So I am messing around with wine and I decided I wanted to make my drive_c folder be on my fat32 drive that I use as a medium between my windows installation and linux installation.  I got the partition to automatically mount through my fstab file and it works great, I managed to convince wine that drive_c was located on the fat32 partition and now I am ready to install this file.  However, the file won't let me install, something about write permission, so I check the file and it doesn't have execute flags (but it's an exe so I guess it should.)  So I decided oh well I guess I need to make it executable.

```

  sudo chmod 777 *
  ls -la
             -rw-rw-rw- ....... file name
  sudo chmod 444 *
  ls -la
             -r--r--r-- ....... file name
  sudo chmod 777 *
  ls -la
             -rw-rw-rw- ....... file name

```

So my question is what the hell is going on?



Also on the side, I don't want to research this too much:
  - whats with the green background and blue font for 777 files sometimes, but not always?
  - how do I change my /media/disk partition to be owned by users group rather than root on start up?

---

### Post by prshah on 2008-09-25
> **Spaceman Spiff said:**
> 
I got the partition to automatically mount through my fstab file 

 drive_c was located on the fat32 partition 

```

  sudo chmod 444 *
  ls -la
             -r--r--r-- ....... file name
  sudo chmod 777 *
  ls -la
             -rw-rw-rw- ....... file name

```

So my question is what the hell is going on?

  - how do I change my /media/disk partition to be owned by users group rather than root on start up?

What is the exact entry you have put in the fstab file for your fat32 partition? Doesn't seem correct to me if it is root owned AND grouped. The entry should be similar to```

# /dev/sda1
UUID=54849BAA849B8CDC /media/sda1     vfat    defaults,umask=007,gid=46 0       1

```

This will mount it with group as plugdev (gid=46; check on your system), allowing access to all members of this group. Also, "defaults" will mount it so that all users have access to all files, irrespective of the fact that the files are root owned.

FAT32 does not support "x" (execute bit) permissions, so running chmod u+x (or o+x) is no good. But if you mount it with "defaults" you will be allowed to run programs off it.

---

### Post by Spaceman Spiff on 2008-09-25
Prshah thank you very much.  It makes sense now.  Here is my fstab options for the fat32 partion

```

     user,auto,fmask=0111,dmask=0000

```

I will change my options to the options you listed.  Thank you.

---

### Post by prshah on 2008-09-26
> **Spaceman Spiff said:**
> 
 will change my options to the options you listed. 

OK, please post back if it works, and mark the thread [solved] by clicking "Thread Tools" to the top right of the page, then clicking "Mark Thread as Solved".

If it doesn't work, please post back with errors / error messages (if any).

---

