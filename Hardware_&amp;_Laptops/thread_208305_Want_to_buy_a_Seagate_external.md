---
title: "Want to buy a Seagate external"
date: 2006-07-03
forum: Hardware &amp; Laptops
---

### Post by satbunny on 2006-07-03
[http://www.seagate.com/products/retail/external/usb/index.html](http://www.seagate.com/products/retail/external/usb/index.html)

I want to buy a Seagate external drive for my Sony Vaio currently running Mandriva 2006.0 but will be shortly running 6.06.
I have a Maxtor One Touch that Windows recognises but not Mandriva 2006.0 nor a Ubuntu 6.06 laptop.

All machines have USB 2.0

Are mass storage drives on USB 2 a problem?
Is there a How-To or should it just automount?

---

### Post by autocrosser on 2006-07-03
I run several external devices with no problems--I don't know about the Maxtor, but a simple external device (without the "one-touch" or similar) will work ok. I'm using a Firewire DVD/CD writer & two external harddrives--both the drives I formated as ext3. If you have problems, you can edit the /etc/fstab to do what you want---I created "named" drives in my /media--code is:

sudo mkdir /media/"name of your drive"
look in the drive list-I use gparted
sudo mount /dev/sd(a-b-c-etc) /media/"name of your drive"

You will have access to your drive at that time & check on reboots to verify that it stays there.

---

### Post by satbunny on 2006-07-04
Thanks, I think I will risk it.

;)

---

### Post by autocrosser on 2006-07-04
My /etc/fstab looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>       <options>                         <dump>  <pass>
proc            /proc           proc         defaults                           0       0
/dev/hdb1       /               ext3         defaults,errors=remount-ro,noatime 0       1
/dev/hdb5       none            swap         sw                                 0       0
/dev/hdc        /media/cdrom0   udf,iso9660  user,noauto                        0       0
/dev/sdb2       /media/Tunes    ext3         rw,auto,noatime                    0       0
/dev/sdb3       /media/Games    ext3         rw,auto,noatime                    0       0
/dev/hda1       /mnt/Windows    ntfs-fuse    auto,gid=1002,umask=0002           0       0

---

