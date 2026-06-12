---
title: "Help! Are my CDROM &amp; DVD drives &quot;mounted?&quot;"
date: 2011-07-26
forum: Hardware
---

### Post by Baffledbylinux on 2011-07-26
This is my first day ever using Linux (Ubuntu 11.04, 32-bit), boy its confusing. I'm having trouble using my CDROM and DVD drives.

I installed Wine 1.2.2  with a view to installing some old games : Tie FIghter, XWing and Star Wars: Rebellion - all gold rating on Winehq.

I managed to install all 3 games from the CDs onto a fake C drive, but none of them will run because they can't find the CD. I tried both drives.

I've set paths in Winecfg, to dev/sr0 and dev/sr1, which is where I think the drives are located. Autodetect didn't find them. However in Winefile when I click on D: and E: (which is what I named them) it says "Path not found." 

I'm now confused as to whether my CDROM and DVD drives are even mounted or not. To be honest I don't even know what mounted means. I can't play audio cds or film dvds either but I'm not sure if thats a separate issue to do with copy protection.

Both disc drives are shown in the system settings/disk utility, and I can explore the contents of the game CDs, but I'm not convinced the drives are installed correctly, or that Wine can see them.

Please help a completely confused Linux noob play his old skool games!
Many thanks
Andy


PS. I've posted a few images of settings, but can provide more information if required.

[http://s1200.photobucket.com/albums/bb329/DasBooter/](http://s1200.photobucket.com/albums/bb329/DasBooter/)


EDIT
Meant to say I am stunned by this OS, its very cool. I didn't realise there were such professional alternatives to Windows.

---

### Post by jramshu on 2011-07-26
Yes, the drives are working and it is mounting the disks , since you can browse the contents. I don't use wine so I can't help you there, sorry.

EDIT: Thought I would try and explain a little better. "mounted" basically means the filesystem on the disk gets attached to the filesystem on the computer so that it is accessible for you to see. If you are able to browse the contents of the disks it is "mounted."

Welcome to Linux, hope you enjoy. Get ready to learn.

---

### Post by pjd99 on 2011-07-26
When you load the cd's/dvd's, they should automatically mount in the /media directory somewhere (usually /media/VOLUMELABEL). Use this path in the mapping for wine.

e.g. I just placed a CD in the drive, and in the drives section of winecfg it showed up as:
F:   /media/071214_1635

I don't think that using the device ID will work, wine doesn't mount any drives, it relies on the underlying operating system to do that.

---

### Post by Baffledbylinux on 2011-07-27
Thanks for your replies!

I set the path to /media/TIE95 and managed to get the game running :-)

I guess that means changing the path for every game I put in?

---

