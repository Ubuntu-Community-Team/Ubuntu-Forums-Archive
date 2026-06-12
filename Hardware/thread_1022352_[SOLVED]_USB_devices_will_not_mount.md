---
title: "[SOLVED] USB devices will not mount"
date: 2008-12-26
forum: Hardware
---

### Post by mucklas on 2008-12-26
Hi all. I had trouble some time ago and you nice people helped me then. Here's hoping you'll do it again.

I run Hardy Heron on my laptop, and I have problems mounting USB devices. I get an error: Invalid mount option when attempting to mount the volume (volume name)
This has occured while trying to mount a flash and an mp3-player.
My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ea0d451f-661e-4bdf-a375-ff95f318b094 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda5
UUID=e7d3f384-85d3-4578-b77d-76d6f92043d3 none            swap    sw              0       0
/dev/sda1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
//Ethernet_BD/audio     /mnt/audio        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mod$
//Ethernet_BD/bucket    /mnt/bucket       cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mod$
//Ethernet_BD/pictures  /mnt/pictures     cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mod$
//Ethernet_BD/video     /mnt/video        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mod$

Ethernet_BD is an external harddrive connected through LAN.

My laptop dvd is toast so I use an external when needed. For this the USB-port works just fine. Ditto for my printer/scanner.

Help, please?

---

### Post by mucklas on 2008-12-27
I found the solution in this thread:
[http://ubuntuforums.org/showthread.php?t=937681&](http://ubuntuforums.org/showthread.php?t=937681&)
I guess that will teach me not to stop searching too soon :)

---

