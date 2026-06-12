---
title: "[SOLVED] toshiba m65 17&amp;quot; no desktop"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by wormser on 2007-04-23
I am trying to get my buddy to install Feisty on his Toshiba m65 17" with an Intel graphics card.  It fails to boot into the desktop and gives the error "fatal IO error 104".  We tried booting with vesa and had no success.  I am not sure where to go from here and what files I should post.  Any help would be appreciated.   Thanks.

---

### Post by rayde on 2007-05-14
I experience the same problem with Feisty Fawn on a Toshiba M65-S9091 with onboard Intel graphics.  The problem did not exist on 6.10.  

This is stumping me...  this same laptop has worked with Sabayon+Beryl.  The problem occurs in Festy Fawn Desktop and Ubuntu Studio.

The Live CD seems to work... 

Help?:confused:

EDIT:

i have added the intel driver:


sudo aptitude install xserver-xorg-video-intel

and then:

sudo gedit /etc/X11/xorg.conf

I changed the "vesa" under my video card driver to "intel" and reboot...  video seems to work.

is this a known bug???

---

### Post by nomad00 on 2007-06-09
Ok, this is really confusing me. Your post works perfectly from the Alternate CD, but when i try to do it from the regular CD sudo aptitude install xserver-xorg-video-intel fails to find the package....? 

Help?

---

### Post by nomad00 on 2007-06-09
Ok, it was a silly problem, i didn't have the universe repository set up....ha!

---

