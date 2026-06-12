---
title: "Disk check at boot fails"
date: 2008-06-07
forum: Hardware
---

### Post by Greevous on 2008-06-07
My Toshiba Satellite (fairly old, currently running Gutsy) encounters an error every time that it boots. It won't continue booting until I press Ctrl+D, and boots and runs perfectly thereafter. The log in /var/log/fsck/checkfs says the following:

> Log of fsck -C -R -A -a 
Fri Jun  6 21:25:04 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=fc3ae588-c375-4797-9a9a-78ca3e6516e8'

fsck died with exit status 8

Fri Jun  6 21:25:04 2008

Is there a way I can fix this so that my notebook can boot completely by itself? Thanks in advance.

---

### Post by Rocket2DMn on 2008-06-07
Can you please post the outputs of
```
cat /etc/fstab
sudo blkid
```

---

### Post by Greevous on 2008-06-07
Here is the output:

> userx@userx-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=0902cda6-fa6e-43b7-9060-2f69179738fe /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=fc3ae588-c375-4797-9a9a-78ca3e6516e8 /media/hda2     ext3    defaults        0       2
# /dev/hda4
UUID=3cb63621-4009-4e01-afac-a21623ae5d3a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


> userx@userx-laptop:~$ sudo blkid
[sudo] password for userx:
/dev/hda1: UUID="0902cda6-fa6e-43b7-9060-2f69179738fe" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda2: UUID="e03369a7-6195-4c6e-8594-027d0e8d135f" SEC_TYPE="ext2" TYPE="ext3" LABEL="storage" 
/dev/hda4: TYPE="swap" UUID="3cb63621-4009-4e01-afac-a21623ae5d3a" 


---

### Post by Rocket2DMn on 2008-06-07
OK, it seems like the UUID on your hda2 partition changed for some reason.  Did you fiddle with the partition?  In any case, it should be an easy fix.  Let's edit fstab and change the UUID
```
gksudo gedit /etc/fstab
```
Now change the hda2 line from
```
UUID=fc3ae588-c375-4797-9a9a-78ca3e6516e8 /media/hda2 ext3 defaults 0 2
```
to
```
UUID=e03369a7-6195-4c6e-8594-027d0e8d135f /media/hda2 ext3 defaults 0 2
```
Save and close.  Now reboot and it should work ok (it will probably run through the whole disk check, it may take a few minutes).

---

### Post by Greevous on 2008-06-07
Thank you, that worked brilliantly. I actually had reformatted that partition recently, but didn't think that GParted could have messed anything up.

---

