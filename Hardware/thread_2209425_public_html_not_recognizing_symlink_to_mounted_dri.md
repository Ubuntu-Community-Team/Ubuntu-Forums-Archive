---
title: "public_html not recognizing symlink to mounted drive"
date: 2014-03-05
forum: Hardware
---

### Post by katie2 on 2014-03-05
[I]Hello!

I am trying to create a soft link from a fat32 mounted drive. It is 3TB, so I had to break it up upon initial partitioning.
This is what it looks like in my fstab:

[/I]*/dev/sda1    /home/mounted_drives/eliot_1a   vfat    auto,users,uid=1000,gid=1001,rw,dmask=000,fmask=000,utf8     0        2*

*/dev/sda2    /home/mounted_drives/eliot_1b   vfat    auto,users,uid=1000,gid=1001,rw,dmask=000,fmask=000,utf8     0        2*
[I]
I mounted it to my home folder in order to make it accessible to samba from a windows machine to transfer large data files.  I have created a symlink from the mounted drive to his home folder: /home/peter/"paula" . "Paula" was defined by the symlink. I am now trying to create another symlink to his public_html folder to access some data via the web: /home/peter/public_html/"craig" 

This is the error I am getting from the Apache2 server:
[/I][h=1]*Forbidden*[/h][COLOR=#000000][FONT=Times New Roman]You don't have permission to access /~peter/craig on this server.[/FONT][/COLOR]
[HR][/HR]Apache/2.2.22 (Ubuntu) Server at 128.143.16.65 Port 80 I am still quite new to linux and learning by doing, if you can offer any advice, it would be great!!

Thanks,
Katie

---

