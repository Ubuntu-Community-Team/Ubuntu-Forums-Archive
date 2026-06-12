---
title: "How to mount hard drive on startup"
date: 2008-10-15
forum: General Help
---

### Post by Afkpuz on 2008-10-15
I've got a second hard drive in my computer and am looking to get it to mount on startup.  I have very little experience with drive mounting and such, but understand ubuntu pretty well, so can anyone help me?  Thanks

---

### Post by LowSky on 2008-10-15
has it been formatted yet? If its NTFS open add/remove and look for NTFS-3g

---

### Post by Sam on 2008-10-15
[Mounting Windows Partitions in Ubuntu](http://www.psychocats.net/ubuntu/mountwindowsfstab)
[Mounting Linux Partitions in Ubuntu](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Spaceman9 on 2008-10-15
Try this. Run 'sudo fdisk -l' in a terminal and write down the partition numbers.

Then create a mount point as a folder in the media folder. Give the monut point a name for the drive you want to mount. 

sudo mkdir /media/(name of drive or mount point)

Then mount it

sudo mount -t <filesystem>  <partition>  /media/(name of drive or mount point)

---

### Post by Afkpuz on 2008-10-16
Yes, it has been formatted with ext3.  I can see it on my computer, I just want it to mount on bootup.  Is there anyway to do that?  I know in kubuntu, you can just check a box in system settings and it will mount at startup.  Nothing like that in Ubuntu?

---

### Post by vanadium on 2008-10-16
Did you notice the post of Sam? Second link.

---

### Post by Afkpuz on 2008-10-21
Thanks guys, that link did work.  I guess when I looked at it, I thought it was just to mount the drive once, but it was just what I needed.  Thanks!

---

### Post by aharp on 2009-06-20
Hi:  As a nubie, I did what you suggested and it worked fine to mount the 2nd hdd I have in the system (it has winoz only on it).  Now that drive mounts when I startup and I would like to prevent that as it slows down the startup process a lot.  Could you tell me how to do that?  If I just unmount it while ubuntu is running it reloads next time I startup.  I was trying to find the configuration file that mounts the drive but was unable to locate it.  Thanks if you have the time to  help.

---

### Post by mhgsys on 2009-06-20
> **aharp said:**
> Hi:  As a nubie, I did what you suggested and it worked fine to mount the 2nd hdd I have in the system (it has winoz only on it).  Now that drive mounts when I startup and I would like to prevent that as it slows down the startup process a lot.  Could you tell me how to do that?  If I just unmount it while ubuntu is running it reloads next time I startup.  I was trying to find the configuration file that mounts the drive but was unable to locate it.  Thanks if you have the time to  help.

just edit your /etc/fstab

```

sudo nano /etc/fstab

```
and put a # before the disk that you don't want to mount automatically.

f.e
If you putted in;
/dev/hda5 /storage ext3 defaults 0 0
 
put a # in front of it to disable the line.
#/dev/hda5 /storage ext3 defaults 0 0

---

