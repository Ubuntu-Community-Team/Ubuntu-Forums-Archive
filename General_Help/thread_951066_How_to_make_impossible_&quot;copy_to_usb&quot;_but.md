---
title: "How to make impossible &quot;copy to usb&quot; but possible &quot;copy from usb&quot;?"
date: 2008-10-17
forum: General Help
---

### Post by ruipedroca on 2008-10-17
Hi,


My question is simple, although it may not be easy: :confused:

How to make impossible "copy to usb" devices but at the same time possible "copy from usb" devices, and printing?


Regards,

---

### Post by ruipedroca on 2008-10-20
Problably isn't possible, right?

---

### Post by TenPlus1 on 2008-10-20
?!?! Be a little more specific...  Do you mean copy a file to a USB device and at the same time copy a file from the USB device ???

---

### Post by loell on 2008-10-20
once you attach it, its always writable until its full.

---

### Post by griz on 2008-10-20
I think the OP is trying to figure out how to restrict write access to a usb device while allowing read access.  Please correct me if I'm wrong.  Anyway, wouldn't changing the permissions do that for him?  Maybe trying to restrict write access would be a reasonable first step.

---

### Post by northern lights on 2008-10-20
If I interpret you right you have a USB flashdrive / stick / external hdd and you want to make the data on it available for second parties to read but not allow these to write to the device?

If you're sharing with other *nix machines only, format the USB device as ext3 either using GParted (partitioning app, available from the repositories) or by running```
mkfs.ext3 -b 4096 /dev/XXXY
```where XXXY will be something along the lines of sdc1 (check using *fdisk -l*).

Once formatted, apply permissions```
chmod -R 774 /dev/XXXY/
```
The numeric mode 774 gives the user and its group read, write and execution rights whereas anybody not in your usergroup can only read it.

In *chmod XYZ*

X is the user's rights
Y the usergroup's rights
Z others' rights

4 - read access
2 - write access
1 - execution rights

7 = 4+2+1

---

### Post by /////// on 2008-10-20
I suppose you can just mount the USB device as Read Only, when mounting just you the -r switch ie mount /dev/sdx /media/xxx -r

---

### Post by josephellengar on 2008-10-20
I thought the option to mount read only was -ro or is that only in the fstab?  What you could also do is if it is every USB drive attached you could put the line into your fstab.  Or, if it is only your specific usb drive you could put the line in your fstab with the uuid of the usb drive below it.  The fstab is located in /etc/fstab and it's kind of self-explanatory to fill out.  I think the option for read only is -ro.

---

### Post by ruipedroca on 2008-10-20
Thanks to all!


Let me be more specific:

1-Kubuntu desktop 8.4
2-users don't have root access
3-users _must_ be able to connect their usb pens _and also_ usb photocameras and copy all the files they want to the computer
4-users _must not_ be able to copy files from the computer to their usb pens or photocameras

Like some of you said, probably permissions will be the solution.
I'm used to use chown and chmod commands and adding partitions to fstab, but in this case I'm kind of lost here because usb pens and photocameras are mounted automatically. ](*,)
 

I'd welcome very much some help configuring fstab for this matter.
Here is my fstab actual content:

[COLOR="Green"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=95efbb9f-8b0f-4a44-9508-ca193c63bafc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=dafcc1bc-d8ea-4dac-aa7d-338767c95b4d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3 /mnt/144gb ext3 users,defaults,atime,auto,rw,dev,exec,suid 0 0
/dev/sdb1 /mnt/200gb ext3 users,defaults,atime,auto,rw,dev,exec,suid 0 0
/dev/sdc1 /mnt/500gb ext3 users,defaults,atime,auto,rw,dev,exec,suid 0 0[/COLOR]


Thanks in advance!

---

### Post by jerome1232 on 2008-10-20
I think what you want to do is actually change what gnomes automount defaults are.

if you open gconf-editor, go to system->storage->default_options it lists what the current defaults for each file system are, modifying these should get what you want.

edit: sorry I just noticed you are useing kde, not sure how to do it there. :(

---

### Post by bodhi.zazen on 2008-10-20
I think you may be talking about writing udev rules.

Check out this link : [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

There is a section "Controlling permissions and ownership"

---

### Post by /////// on 2008-10-21
> **idigchess said:**
> I thought the option to mount read only was -ro or is that only in the fstab?  What you could also do is if it is every USB drive attached you could put the line into your fstab.  Or, if it is only your specific usb drive you could put the line in your fstab with the uuid of the usb drive below it.  The fstab is located in /etc/fstab and it's kind of self-explanatory to fill out.  I think the option for read only is -ro.

 -r     Mount the file system read-only. A synonym is -o ro.
from man mount

---

### Post by dcstar on 2008-10-21
> **ruipedroca said:**
> Thanks to all!


Let me be more specific:

1-Kubuntu desktop 8.4
2-users don't have root access
3-users _must_ be able to connect their usb pens _and also_ usb photocameras and copy all the files they want to the computer
4-users _must not_ be able to copy files from the computer to their usb pens or photocameras
........
Thanks in advance!

Set the user account(s) to have no read permissions on your machine.

---

### Post by ruipedroca on 2008-11-04
I'm going to try and them post feedback!

---

