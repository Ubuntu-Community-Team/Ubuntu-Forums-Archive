---
title: "26 gig /dev/sda6 umount not working"
date: 2008-11-26
forum: Hardware
---

### Post by suffice on 2008-11-26
i have intrepid, been ok, little buggy, and i noticed my drive was full the other day... its also mythbuntu running as regular desktop

then upon further investigation i noticed that a partition is mounted @ /var/lib   that is from /dev/sda6 of 26 gb of xfs.

now during my setup i didnt partiotion this in, not do i want it..
gparted or cl wont let me unmount to add add it to the regular drive..

output of sudo umount /dev/sda6 is 

/var/lib: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
i tried then lsof and fuser, but dont understand what is coming out of there.....

is there any way to force a umount?   or has anyoen heard of this before?....there is only 1mb on the partition, and i know its nothin....it just seems wierd that i never put it there, and now its threre, making the rest of my comp slow because the drive is near maxed out.....

---

### Post by jpkotta on 2008-11-26
I'll bet that tons of things are using /var/lib/.  You'll probably have to reboot.  

Here is what I'd do.  Edit /etc/fstab so that the /var/lib/ filesystem won't mount any more (just put a '#' at the beginning of that line).  Then shutdown and reboot with a Live CD.  In the live cd, mount the root filesystem and the /var/lib/ fs, and copy everything in the /var/lib fs to the root fs.  Use -a for this:
```
cp -a /media/varlib/ /media/rfs/var/lib
```
Then you should be able to reboot and the /var/lib fs will be unused (make sure of this by running "mount"), and you can do whatever you want with that partition.

---

### Post by suffice on 2008-11-27
sweet.....that worked.....


the only thing is i was then hoping to add the dead space to sda1......but cant if its up and going...but im sure that if i booted a live cd again, then mounted and install gparted that i could add them because sda1 woulnd be active...

thanks for the help...

also now...since that sda6 is deleted and now reformatted into  a new partiion at /media/downoads, i guess then fstab would be cleaned up of the other stuff? or just leave it if its all working? ha...

thanks again...

---

