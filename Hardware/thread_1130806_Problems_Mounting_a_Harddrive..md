---
title: "Problems Mounting a Harddrive."
date: 2009-04-20
forum: Hardware
---

### Post by mYstline on 2009-04-20
Hi all :)

I'm completely new at using Ubuntu, I've played around on it before, but never installed it myself. 

I've managed to install everything and update everything perfectly fine, however, I've yet to be able to mount my secondary harddrive, that I basically keep all my information on (I have one harddrive for OS and another for information) 

I'm not sure what information you people will need to help me, but I saw in a few threads that I tried looking through that /etc/fstab was needed.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=04660d3d-b055-4e61-9a90-d7a595674233 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=49b4f78f-34b2-4947-bd48-d5cb40d8f838 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I've uploaded an image of the error I get when I try to mount by right clicking > mount device as well.

Thanks in advance :)

---

