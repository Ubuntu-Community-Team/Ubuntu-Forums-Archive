---
title: "Can not remove USB HD partition from external drive"
date: 2010-04-17
forum: Hardware
---

### Post by Silvernail on 2010-04-17
When I was installing 9.10 on my computer, I left my external USB hard drive plugged in.  Some how I wound up with a  2.5 gig file on it that is a boot file.

It is listed on the bio screen at boot times as mounted on /dev/sdb6.
And shows here:
> dave@dave:~$ di
Filesystem         Mount               Megs     Used    Avail %Used fs Type
/dev/sda1          /               147365.3   8965.1 130914.4  11%  ext4   
udev               /dev               497.1      0.3    496.8   0%  tmpfs  
/dev/sdb6          /media/6cdedbb0   2347.1   2040.0    187.9  92%  ext3   
/dev/sdb1          /media/Teragb   940903.9  59823.4 833661.8  11%  ext3   
dave@dave:~$ 

I shows on my desktop screen along with my USB terabite drive.


I tried the ```
sudo apt-get remove --purge ????
``` and it tells me it can not find it.
I just deleted several kernel versions 2.6-30-???, this is 28-11.

I tried 'disk utility' and it shows but when I try to delete it I get a 
Busy message.

 [Disk Utility Screen Shot]("http://www.mediafire.com/imageview.php?quickkey=noedzignjzn&thumb=4")

I would like to get rid of it.

Can anyone help.

---

