---
title: "howto install Ubuntu 9.04 alternative PS3"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by junke1990 on 2009-08-23
Hey ya all, I had a lot of probs with booting ubuntu fromout kboot.

Since I had no disks (and it is 22:30 on sunday) left I tried USB sticks.

I downloaded the ubuntu 9.04 alternative PS3 image, [http://cdimage.ubuntu.com/ports/releases/jaunty/release/ubuntu-9.04-alternate-powerpc+ps3.iso](http://cdimage.ubuntu.com/ports/releases/jaunty/release/ubuntu-9.04-alternate-powerpc+ps3.iso) and got it on the drive with unetbootin(356).

after doing the usual with the otheros.bld I booted up the PS3 and came to kboot but no disk....

so I did the following
to open a shell
```
$kboat: sh
```

checking out what dev is my usb in my case sda1 and mounting it
```
ls /dev/sd?1   #in my case sda1
mkdir /mnt/temp 
mount /dev/sda1 /mnt/temp
cd /mnt/temp
```

after a lot of **** from kexec i tried to load it with -f (force!) and it worked like a charm!
```
kexec ubnkern --initrd=ubninit --append="root=/dev/sda1" -f
```

the installer will boot!

now the only (known) prob (for me that is) with the installer is, it will search for a cdrom for the files to install but we have don't have one... so i tried the how to on [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) but no succes :( 

I did the following
```
mkdir /cdrom /dev/cdroms
cd /dev/cdroms
ln -s ../sda1 cdrom0
mount -t vfat /dev/cdroms/cdrom0 /cdrom 
```

with the last command I get
```
mount: mounting /dev/cdroms/cdrom0 on /cdrom failed: no such device
```

I read a lot about the error but cant get it to work... is replacing the initrd and kern the only option to avoid this problem? and is it still needed (posts are about older versions)

---

### Post by junke1990 on 2009-08-23
I replaced them with the files from [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/hd-media/) and still the same problem... no such device!

---

### Post by KSDZ on 2009-09-02
Instead of using unetbootin to copy the contents of the ISO to a Fat filesystem, copy the complete ISO filesystem like this:
```
sudo dd if=/path/to/image.iso of=/dev/sd??
```
(make sure you replace the questionmarks)

Download Gujin:
```

wget http://downloads.sourceforge.net/project/gujin/deb_debian32/debian32.tar.gz?use_mirror=ovh

```

Unpack:
```

mkdir gujin
tar xzvf debian32.tar.gz -C gujin

```

Install:
```

cd gujin
sudo dpkg -i gujin_2.7_i386.deb

```

Then, install gujin to your usb key:
```

sudo /sbin/gujin /dev/sd?0

```
(replace the questionmark, but make sure the zero stays)

Then restart, select the partition you dd'ed the image to,
and try the trick you did before again (symlink).
It should work now.

---

