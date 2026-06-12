---
title: "New Monitor, Max Resolution not Showing."
date: 2005-12-26
forum: Hardware &amp; Laptops
---

### Post by Rev. Nathan on 2005-12-26
I got an old monitor of my grandma, who just got a flatpanel. She was using a 21" CRT @ 800x600 before, so I snagged it. It is capable of doing 1600x1200, but my options are only showing me 1280x1024 (Which was the highest resolution of my last monitor). Do I need drivers or something? This monitor is no longer supported by HP. It's the Ergo 1600, if by some lucky chance someone has had this.

---

### Post by Who on 2005-12-26
You need to edit your /etc/X11/Xorg.conf file to get the best performance out of your monitor really, however, if you want a nice automated way to put all the settings right then you can use:
sudo dpkg --reconfigure xserver-xorg
and then follow the steps (Sudo is a prefix to give you administrator rights. the command following is using debian package manager to reconfigure the package that is responsible for providing the graphics, xserver-xorg)

I like to backup the old file first:
sudo cp /etc/X11/xorg.cong /etc/X11/xorg.conf_BACKUP[date]
(cp = copy, first path is orig. file, second path is the new file)

Good luck! It is useful to have your monitor manual or the internet handy to find the sync ranges etc...

Who

---

### Post by Rev. Nathan on 2005-12-26
Thank you, I figured it out from your post, although you gave me wrong information in places. I just needed to open /etc/X11/xorg.conf, edit the section with resolutions, follow the command given in the file, type it in Terminal (it makes a backup all its own), kill the XServer, and go!

But thanks for pointing me in the right direction! I'm rollin' 1600x1200 now! :)

---

### Post by Who on 2005-12-26
Fair dos, 
I haven't looked in detail at a breezy xorg.conf - so the info may well be in there :),
and I was wrong, sorry! - it is sudo dpkg-reconfigure xserver-xorg. as my other posts will show - I have no bootable system at the moment to check stuff on! My mistake!

Glad you could fathom it out!

Who

---

