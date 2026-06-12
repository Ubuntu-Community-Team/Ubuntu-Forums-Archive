---
title: "Can't find hard drive"
date: 2010-09-28
forum: Hardware
---

### Post by sreevbg108 on 2010-09-28
Hello,
    I have ubuntu 10.04 installed on a Kingston 8gb flash drive. I needed more space for my stuff, so I got a 1 TB hard drive that had 208 gb of storage filled. I wanted to partition this so I could use the space in another way. I downloaded gparted and was about to partition when it says, "you can potentially have a LOSS of DATA." So I quit the aplication and after that, the hard drive doesn't show up in the "places" section anymore. Is there a reason for this and is there a fix? I have valuable data on it. I tried unplugging from the motherboard and plug it back in. (the motherboard can fing the drive). I've also restarted the computer and it doesn't help.

---

### Post by Dawei87 on 2010-09-28
is the hard drive you were going to partition the one you boot your other operating system from? or is it just storage? if the motherboard doesnt see the hard drive then i would suggest clearing the cmos settings on the board. you can usually do this by setting a jumper or removing the battery itself for a few seconds while the machine is powered off. then when you reboot, if the bios ask you if you want to use the default settings or open the configuration tool, dont load the defaults, just open the configuration tool and see if you can see your drive. if so, save the settings and exit. your computer will reboot and it should be ok, if not there could be extensive damage to your hard drive.

EDIT: could also be helpful to use a livecd version of gparted, for some reason i always get best results this way. you could use the gparted installed in the ubuntu livecd, but i like using just gparted itself. you can find it here: [http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.6.3-3/gparted-live-0.6.3-3.iso/download](http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.6.3-3/gparted-live-0.6.3-3.iso/download)
you can also use a different livecd that has a good set of hard drive tools here: [http://www.hirensbootcd.net/download/Hirens.BootCD.11.0.zip](http://www.hirensbootcd.net/download/Hirens.BootCD.11.0.zip)

---

### Post by sreevbg108 on 2010-09-28
The motherboard sees it fine. The hard drive is a hitachi model. The drive is just extra storage.

---

### Post by Dawei87 on 2010-09-28
if you reboot your computer does it see the hard drive in linux again? if not i would try using the livecd of gparted to partition it, and along the way it should fix any errors it finds

---

### Post by sreevbg108 on 2010-09-28
Linux still doesn't see it but thanks, i'll see if I can find the hard drive if I can boot off of gparted.

---

### Post by Dawei87 on 2010-09-28
i guess it could also be useful if you post the contents of you /etc/fstab, dont know why i didnt think about that before, i guess ive been doing too much maintenance in windows lately...

EDIT: btw, i mean the /etc/fstab in on your linux partition on the flashdrive.

---

### Post by sreevbg108 on 2010-09-28
I think it is the ubuntu that is screwed up. I tried using the live cd of ubuntu 10.04.1 and it showed my 1 TB drive. Here are the contents of /etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=b63b5a07-78eb-4643-968f-7f0bbd71ecd5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=16a4982f-5387-42ea-9c8b-4ad886af8c9a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

EDIT: I forgot to mention that brasero isn't letting me burn the gparted disc so I can't try that now.

---

### Post by Dawei87 on 2010-09-28
you might try editing the fstab so that it has the 1tb hdd specified on it, that should hopefully get it going again. assuming the partition on the 1tb hdd is called /dev/sda1 (it may not, its just an example. you can boot the livecd again and edit the fstab and use gparted to find exactly what it is called.) you can make the fstab look something like this:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# 1tb hdd. CHANGE THE DETAILS AS NECESSARY FOR YOU HARD DRIVE INCLUDING MOUNT POINT, DEVICE PATH, AND FILESYSTEM TYPE
**/dev/sda1** **/media/sda1**   **ext4**   user,noauto  0 0
# / was on /dev/sdb1 during installation
UUID=b63b5a07-78eb-4643-968f-7f0bbd71ecd5 / ext4 errors=remount-ro 0 1
# swap was on /dev/sdb5 during installation
UUID=16a4982f-5387-42ea-9c8b-4ad886af8c9a none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

EDIT: i think that should get you going if set up properly, if not, the cleanest solution might just be to reinstall linux. kinda sucks but it is sometimes faster than dealing with forums for help. and it would also be a good idea to make a backup of your fstab file in the same location and just call it fstab.backup before you make any changes just in case i gave you wrong advice.

---

### Post by sreevbg108 on 2010-09-29
After I rebooted the computer and booted into my main os, (without editing the etc/fstab) the hard drive appeared again. This nice because I got my hard drive back, but this is very frustrating because I don't know when this will happen again. If there is a reason for this, can you tell me? I would like to know the best partitioning program and backing up is required.

---

