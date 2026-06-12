---
title: "Dell Inspiron screen resolution, Help!"
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by quincyjones on 2006-04-21
Hi, Please please help!
I have installed breezy badger on my Inspiron notebook (Intel 910GML chipset) but I can not get the correct screen resolution. In my preferences>screen resolution I only have the option for 1024x768. In my xorg.conf file there is absolutely no mention of 1024x768! 
It mentions all the correct resolutions in the correct places (as far as I can tell) ie: Section "Monitor" >Modeline and SubSection "Display" >Modes.

I have also run dpkg-reconfigure xserver-org (from the command line with xorg stopped), it seems to run perfectly and recognise everything but it makes no difference.

Where is the 1024x768 resolution coming from?
:confused:

---

### Post by aysiu on 2006-04-22
You didn't say what Inspiron model you're using, so maybe [this search](http://www.google.com/search?hl=en&q=inspiron+910gml+linux&btnG=Google+Search) might help?

---

### Post by Peacepunk on 2006-04-22
tune in to this:

[http://users.skynet.be/thomasvst/linux-on-laptop/](http://users.skynet.be/thomasvst/linux-on-laptop/)

you'll find an easy hack that would allow you to use wathever screen reolution you'll like.

Find some more in:

[http://www.ubuntuforums.org/showpost.php?p=797354&postcount=12](http://www.ubuntuforums.org/showpost.php?p=797354&postcount=12)

some details & recommendations that applies to Badger.



Cheers from da Peacepunk. If I did it in 1 hour, you should be ok in 1... minute !


_

---

### Post by paritybit on 2006-04-22
From memory this is one of the displays that needs 915resolution to get it working. I just installed the Debian package for this (found here [http://ftp.us.debian.org/debian/pool/main/9/915resolution/915resolution_0.5.2-2_i386.deb](http://ftp.us.debian.org/debian/pool/main/9/915resolution/915resolution_0.5.2-2_i386.deb) (and yes, direct links are evil but this is for simplicity)) or just look here [http://packages.debian.org/testing/x11/915resolution](http://packages.debian.org/testing/x11/915resolution)
sudo dpkg -i <filename> (whatever you save it as/to).
Now edit /etc/default/915resolution
you will want it to look something like this:
```
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE
#
MODE=5c
#
# and set resolutions for the mode.
#
XRESO=1280
YRESO=800
```
Now one more step needed that tripped me up. you will need to do this command:
```
sudo ln -s /etc/init.d/915resolution /etc/rcS.d/S90915resolution
```
this is because as the default for the Debian package is to start up after X (which isn't a lot of help) so this will make it start up before and should all work a dream, well it did on my inspiron 710m.

---

### Post by quincyjones on 2006-04-23
Hey, Thanks for all the replies!
This (from Peacepunk) sorted me out: 
**[http://users.skynet.be/thomasvst/linux-on-laptop/](http://users.skynet.be/thomasvst/linux-on-laptop/)**
but clearly other ways will work too!
:D

---

