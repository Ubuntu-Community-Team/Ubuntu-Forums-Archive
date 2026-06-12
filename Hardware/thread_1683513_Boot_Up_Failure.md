---
title: "Boot Up Failure"
date: 2011-02-07
forum: Hardware
---

### Post by TheOmega720 on 2011-02-07
When I boot my laptop it goes through the normal white text until the very end it says:
target file system doesnt have requested /sbin/init

and also:
no init found try passing init = bootarg

I need this computer for school so I appreciate the help.

---

### Post by TheOmega720 on 2011-02-08
Can't anyone provide advice?
I'm thinking the only option is reinstall at this point.
I won't loose anything other than some incomplete papers and my music and video collections.

---

### Post by drs305 on 2011-02-08
Reinstalling is often faster than troubleshooting this type of problem, but you may wish to wait to see what solutions are offered.

My reason for posting is to remind you that you can probably recover any files in your home or other Ubuntu folder by mounting your Ubuntu partition via the LiveCD. 

Boot to the desktop, mount your Ubuntu partition, and you should be able to see and copy your files to another location. 

Assuming Ubuntu is on sda5 (change values as necessary):
```
sudo mount /dev/sda5 /mnt
gksu nautilus /mnt/home/*yourusername*
```

I've used "gksu" just so you have access to any files anywhere on the system, regardless of who owns them.

You could try this before reinstalling just to see if there are errors on the disk that are preventing the system from booting. Again, I'll assume Ubuntu is on sda5. Change the value if necessary. *The partition must be unmounted before running the e2fsck command.*

```
sudo umount /dev/sda5
sudo e2fsck -pfv /dev/sd**a5**
```

---

