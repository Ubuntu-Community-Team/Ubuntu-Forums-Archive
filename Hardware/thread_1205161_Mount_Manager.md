---
title: "Mount Manager"
date: 2009-07-05
forum: Hardware
---

### Post by pmla on 2009-07-05
I'm running Ubuntu 9.04 desktop and have a bunch or network drives (windows file sharing and samba) that I would like to mount / unmount and automount.

After checking the forum, the majority of users recommend Mount Manager for this task... I think it as a nice GUI.

After installing mountmanager from repositories, I saw that it created an icon in System»Administration.


When i try to run it from GUI, nothing happens.

If I try to run it from terminal I'm getting this error:
@Gamer-Ub:~$ mountmanager
4 records in /etc/fstab were detected. 
[G] DBus interface was created
[G] All devices were recieved
[I] Storage device was detected: "/dev/sda2" 
[I] Storage device was detected: "/dev/sda1" 
[I] Storage device was detected: "/dev/sda6" 
[I] Storage device was detected: "/dev/sda5" 
[I] Storage device was detected: "/dev/sr0" 
[I] Storage device was detected: "/dev/sda" 
[G] Parsing of  "/usr/share/mountmanager/options/common.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/iso9660.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/udf.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/ext3.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/ntfs-3g.xml"  was successful 
Segmentation fault



Here is mt fstab file

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda5 during installation
UUID=f049e45d-51a9-44c3-ab3e-45b5205bdc51 / ext3 relatime,erro$
# swap was on /dev/sda6 during installation
UUID=caf81dd0-14ee-477b-b854-e4cd3e5fffdf none swap sw $
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

Is there any way of fixing this? or maybe a better software with GUI to mout/unmout and automount startup?

---

### Post by pmla on 2009-07-06
***** bump 1 / 3 *****

---

### Post by pmla on 2009-07-06
Was checking their website, ubuntu forum and google. It seems to have a bug when installed in ubuntu 9.04. Don't even know why it's available in repositories if it does not work.



Can anyone recommend a mount soft with GUI /mout/unmout/automount at startup that might also be used in **network** drives/shares/partions?

---

### Post by tomick on 2009-09-12
I now it's old topic, but this problem is still exist. 
If you have package in repository "mountmanager_0.2.6-0ubuntu2"
you shuld download "ubuntu3" version DEB package from [this]("https://launchpad.net/~fabricesp/+archive/ppa/+files/mountmanager_0.2.6-0ubuntu3~intrepid_amd64.deb")(64bit) or [this]("https://launchpad.net/~fabricesp/+archive/ppa/+files/mountmanager_0.2.6-0ubuntu3~intrepid_i386.deb")(32bit) location. This packages was build for Intrepid.

---

### Post by giyad on 2009-11-10
> **tomick said:**
> I now it's old topic, but this problem is still exist. 
If you have package in repository "mountmanager_0.2.6-0ubuntu2"
you shuld download "ubuntu3" version DEB package from [this]("https://launchpad.net/~fabricesp/+archive/ppa/+files/mountmanager_0.2.6-0ubuntu3~intrepid_amd64.deb")(64bit) or [this]("https://launchpad.net/~fabricesp/+archive/ppa/+files/mountmanager_0.2.6-0ubuntu3~intrepid_i386.deb")(32bit) location. This packages was build for Intrepid.
Thanks tomick, that worked great!

I used Add/Remove to get rid of the old mountmanager that I installed from the repositories, and used the link you gave me to install the new one.

---

### Post by cSquall on 2011-01-19
> **tomick said:**
> I now it's old topic, but this problem is still exist. 
If you have package in repository "mountmanager_0.2.6-0ubuntu2"
you shuld download "ubuntu3" version DEB package from [this]("https://launchpad.net/%7Efabricesp/+archive/ppa/+files/mountmanager_0.2.6-0ubuntu3%7Eintrepid_amd64.deb")(64bit) or [this]("https://launchpad.net/%7Efabricesp/+archive/ppa/+files/mountmanager_0.2.6-0ubuntu3%7Eintrepid_i386.deb")(32bit) location. This packages was build for Intrepid.

Verified -- this works.  This version of Mountmanager even corrected the errors that pysdm had created!

---

