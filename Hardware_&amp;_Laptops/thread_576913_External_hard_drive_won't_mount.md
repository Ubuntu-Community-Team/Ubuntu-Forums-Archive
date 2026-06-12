---
title: "External hard drive won't mount"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by watson!!!! on 2007-10-15
i recently switched from vista to feisty, and very recently upgraded to gusty. since i upgraded, i've been getting an error message anytime i try to use my external hard drive, claiming it can't be mounted. i was able to use it fine with feisty, so i see no reason why it shouldn't work now. 

here is the error message:
$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs -3g /dev/ sdb1 /media/external drive -o force Or add the option to the relevant row in the /ect/fstab file: /dev/ sdb1 /media/external drive ntfs-3g defaults, force 0 0.

the external drive in question is a maxtor onetouch.

why am i getting this message? it worked fine previously, and i don't have windows installed. i try typing in the command it gives me, but the problem isn't fixed. i'm a serious beginner to linux, so could somebody give me a step-by-step walkthrough of how to fix this?

thanks.

---

### Post by DrPennybags on 2007-10-15
I'm having the exact same problem. I have tried to amnually mount the drive as well as mount from terminal using the force option. Neith did any good. I did find one thread that suggested it may be a bug in Gutsy. Anyone find a solution for this issue yet?

---

### Post by zeronothing on 2007-10-19
hey guys,

I just recently upgraded to Gutsy and I am having the same problem. The problem I was having is all of my internal HDD (that are formatted in NTFS) would mount, but my external HDD would not. The external HDD would try to mount and unmount and retry again. It would never mount. Anyway, to over come this problem I just went to the ntfs-3g website and downloaded the newest source, compiled it, and installed and now I'm back in business. Now, not only do my internal drives show up but my external HDD shows up now with no problem. I believe there is something wrong with the ntfs-3g deb package. when I was installing the newest sources from the ntfs-3g's website during the compiling it gave me a warning.

*****************************************************************************************************************
* WARNING  WARNING  WARNING  WARNING  WARNING  WARNING  WARNING  WARNING   *
* The FUSE user space binaries were NOT installed with root directory      *
* executable prefix. This means that automounting NTFS volumes during boot *
* could fail. This can be fixed the below way by reinstalling FUSE using   *
* the right 'configure' option during FUSE compilation:                    *
*       ./configure --exec-prefix=/                                        *
*       make && sudo make install                                          *
* WARNING  WARNING  WARNING  WARNING  WARNING  WARNING  WARNING  WARNING   *
*****************************************************************************************************************

I would suggest trying to download the newest source and installing it that way. it was pretty simple, just make sure you have the build-essentials, and fuse installed. 

I would also like to mention that I'm using the 64-bit edition of Gutsy

---

### Post by godfather_rocks on 2007-10-20
Guys, same problem here...

I am too new to Ubuntu (or ne type of Linux if it matters..)...

Initially, it mounted external hard-disk (which has 4 NTFS partitions) automatically.. But, by mistake I unplugged it without unmounting - and after that it doesnot work....

I tried to use some 'mount -t' commands as well.. but, it gives message only root can perform that operation... Now, I don't know how to login in root....

Plz suggest wat to do exactly..?

---

### Post by rumburak on 2007-10-20
Same here. External HD (ext3), MP3-Player and CF cards won't mount automatically. Either to mount manually fails. For the HD```
mount -t ext3 /dev/sdf /mount/disk
``` raises an error msg that no ext3 could be found on that HD..
All devices appear in dmesg but that's all. I tried a lot since then (plugging devices while booting, reinstalling the hal-packages, removing the option "usefree" via gconf-editor from /system/storage/default_options/vfat/mount_options or to delete /usr/share/hal/fdi/policy/gparted-disable-automount.fdi. Latter one didn't exist anyway).

I'm pretty curious about answers...

---

### Post by tonofclay on 2007-10-20
I actually had this problem a few days after I connected my maxtor one touch in feisty. I forced the drive to mount doing this: "ntfs -3g /dev/ sdb1 /media/external drive -o force", notice the mount -t is missing from that command. That did the trick for me, whereas the mount -t was causing the problem for me. However when I upgraded to gutsy the problem went away for me, so I don't really have any advice on how to get your drive working error free as it just sort of happened for me.

---

### Post by monfreex on 2007-10-22
I installed Feisty back then and had no trouble of auto mounting my USB and external hard drive but when I upgraded to Gusty thats when the error popped up like the error message from "watson!!!". Hope an update for this would be available soon if this is a bug. Btw Ubuntu rocks! :guitar:

---

### Post by jalirious on 2007-10-24
Nothing as serious, but after unplugging my HD without unmounting there remains a fake HD icon on my desktop that I haven't shook off yet. On plugging in the hard-drive again there appears to be two of the same icons and one works fine. Oh- in gutsy.

---

### Post by rumburak on 2007-10-24
For those who still can't automount:

Try to install following packages:
ivman, pmount, usbmount

It worked out for me, though I have now some crude folders ( usb[1-8] ) in /media that I've not seen back then and I can't guess for what they may are useful. Further, the folder names of the mounted devices are named like the devices (e.g. /media/sdb1 or /media/sdc1). I'm used to hae names like /media/disk oder similar...

---

### Post by ItsAMeMario82 on 2008-04-22
I just had this problem with Ubuntu 7.10.

I'm using a dual windows/ubuntu environment. I discovered that the problem occurred because I didn't go to Safe Removal within Windows XP/Vista. When I did this, I would get the exact same error. So I plugged the drive back in, did the safe removal, then plugged it back into ubuntu. Drive mounted fine after that.

---

### Post by jjtstan on 2008-04-26
I was getting the exact same error message as Watson, and now have at least a temporary fix.  No automount, though.

I've got a Dell i386 with factory installed Gutsy 7.10.  External HD is a SeaGate FreeAgent Go 120GB ntfs.

I installed the ntfs configuration tool.  No luck. Computer didn't even recognize the drive.

Added pmount and ivman, restarted hal:

> sudo /etc/init.d/hal restart

 Disk would then show up in fdisk -l.

> sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

Then got the drive recognized.  

Maybe this would help?  I'd be interested in an automount solution.  Like Watson, I'm an absolute rookie, so need very detailed explanations.

---

