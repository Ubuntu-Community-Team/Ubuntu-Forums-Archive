---
title: "No automatic mounting at startup"
date: 2008-09-10
forum: Hardware
---

### Post by GH68 on 2008-09-10
I have added a line in my [FONT="Book Antiqua"]/etc/fstab[/FONT] to mount my Windows drive, a separate internal drive on the same computer as I use for my Ubuntu. The drive is not mounted at startup, although it mounts perfectly and becomes accessible for all users when running sudo mount -a.
My Windows drive is the sda1 in my fstab shown below:

[FONT="Book Antiqua"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=56d3fa89-d81c-46aa-90f4-8094f9f35666 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=4c9335ba-c10c-4102-a31d-12e72b2eebac none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1	/media/windows	ntfs-3g	defaults,umask=0	0	0
192.168.1.21:/shares/internal	/media	nfs	rsize=8192,wsize=8192,timeo=14,intr
/dev/sde1	/media/PB_SAVE	ntfs	force,ro,nls=utf8	0	0[/FONT]



Any ideas?

---

### Post by IntuitiveNipple on 2008-09-10
The SMB mount that follows it mounts to /media ? Is that masking the previous mount to /media/windows of the NTFS volume? Shouldn't the SMB mount-point be something like /media/net1 ?

---

### Post by GH68 on 2008-09-10
Thanks IntuitiveNipple. It is a good point. Strangely enough the nfs mount is working and mounts the directory PUBLIC. However, I will try to add to mount it to a subfolder of /media instead of /media directly to see if it influences my Windows mount!

---

### Post by GH68 on 2008-09-10
Ok, I tried to mount the nfs server in net1, so now my /etc/fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=56d3fa89-d81c-46aa-90f4-8094f9f35666 /               ext3    relatime,erro$
# /dev/sdb5
UUID=4c9335ba-c10c-4102-a31d-12e72b2eebac none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1       /media/windows  ntfs-3g defaults,umask=0        0       0
192.168.1.21:/shares/internal   /media/net1     nfs     rsize=8192,wsize=8192,t$
/dev/sde1       /media/PB_SAVE  ntfs    force,ro,nls=utf8       0      0  


However, I think I found the solution to my problem while doing this: The /media/windows directory was not created! I suppose this was rather the reason for my problem than the wrong mounting of the nfs share? But now, a new strange thing has happened. In my /media/net1 I do find my folder PUBLIC, which is the one I mount. However, I also find the following empty folders:
windows
cd0
net1
lost+found
*Edit 2008-09-11: It turned out that these folders could be removed and they did not appear again after restart*


I doen't hurt too much to have them there, though.

Thanks for pointing me in the right direction!

---

### Post by IntuitiveNipple on 2008-09-10
> **GH68 said:**
> However, I think I found the solution to my problem while doing this: The /media/windows directory was not created! 
That would certainly do it :D Glad you spotted it, these minor things can drive you up the wall very quickly!

---

