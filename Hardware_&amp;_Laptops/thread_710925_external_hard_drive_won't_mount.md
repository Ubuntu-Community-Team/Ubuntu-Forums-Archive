---
title: "external hard drive won't mount"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by grumpylad77 on 2008-02-29
I am trying to mount a Seagate external hard drive.

When I turn it on I get:

$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1': 
Choice 1:If you have Windows then disconnect the external devices by clicking 
on the 'Safely Remove Hardware' icon in the Windows taskbar then
shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use 
the 'force' option for your own responsibility. For example type on the command
line: mount -t ntfs-3g/dev/sdb1/media/New Volume -o force
Or add the option to the relevant row in the /etc/fstab file: 
/dev/sdb1/media/New Volume ntfs-3g defaults,force 0 0

So I typed that into the command line and got:
Failed to access '/dev/sdb1/media': Not a directory


I know that I am probably just doing something wrong in the command line, but
don't know what

---

### Post by hhhhhx on 2008-02-29
this also happened to me so heres my advice:
make sure your in as root, and check the mount point, on mine it was wrong. :)

---

