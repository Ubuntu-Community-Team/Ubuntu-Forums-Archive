---
title: "Writing EXIF data to files on a network drive"
date: 2011-07-09
forum: Hardware
---

### Post by seandroms on 2011-07-09
I am trying to organize a large collection of photos stored on a network attached storage device, a DNS-323 in particular. I am able to read and write files on the NAS without problem. 

However, when I use various programs to attach tags to my photos in the EXIF information (or perhaps IPTC, I'm unclear on the difference), it fails. 

The programs I've tried to use so far have been [jBrout]("http://jbrout.manatlan.com/") which fails without complaint, and [mapivi]("http://mapivi.sourceforge.net/mapivi.shtml"), which gives the error [PHP]save failed for /home/sean/pictures/blah/blah/blah.jpg[/PHP]

If I copy the picture in question to my local hard drive, the tagging works fine.

Here is my fstab line for the NAS:
[PHP]//nas/Volume_1	/media/nas	cifs	credentials=/home/sean/.smbcredentials,iocharset=utf8,file_mode=0770,dir_mode=0770	0	0[/PHP]

I suspect there is some obscure permission error happening, but I have no idea how to fix it, especially since I can create/modify/delete files just fine otherwise.

jBrout in particular looks like it's the perfect program for me, and I would love to have this issue resolved. Does anyone have any ideas?

Thanks in advance!

---

### Post by seandroms on 2011-07-09
The program qPhotoTag gave me a slightly more helpful error message which led me to believe the source of the problem is a bug in Exiv2, see for example [this post from exiv2.org]("http://dev.exiv2.org/boards/3/topics/930").

It looks like I may have to compile my own version of exiv2 if I want to fix this problem. I'll try tomorrow and report back.

---

