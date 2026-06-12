---
title: "Dell Inspiron 2600 Install Issue"
date: 2005-09-03
forum: Hardware &amp; Laptops
---

### Post by Cody1 on 2005-09-03
Im trying to install Ubuntu on a spare laptop that ive come across.  Its a Dell Inspiron 2600.  I get through the install and it says there is a problem with the X - -----scale??
I forget the rest of the error message but it had something to do with the graphics driver.. i can reinstall it and try again and paste error code here. Im  newbie so just getting going with the whole process, thought id start out on an extra laptop just to play around but i run into this problem.  Any help would be much appreciated. I got the cd in the mail, so it is 5.04 without any new fixes

thanks!

---

### Post by moopere on 2005-09-03
[QUOTE=Cody1]Im trying to install Ubuntu on a spare laptop that ive come across.  Its a Dell Inspiron 2600.  I get through the install and it says there is a problem with the X - -----scale??
I forget the rest of the error message but it had something to do with the graphics driver.. i can reinstall it and try again and paste error code here. Im  newbie so just getting going with the whole process, thought id start out on an extra laptop just to play around but i run into this problem.  Any help would be much appreciated. I got the cd in the mail, so it is 5.04 without any new fixes

thanks![/QUOTE]

You'd have to boot up the system and give the actual full error message to get a reasonable answer.  

However, as you say, its doubtless something going astray with the video detection/configuration.  What sort of VGA card/chip does this laptop use?

Something that usually works, though it can be a bit scary, is to run dpkg-reconfigure xserver-xorg from a spare VT (say ctl-alt F1 for instance).  When it asks you what VGA card to use choose VESA - this will normally work with most machines.  Its somewhat horrible, but should give you a desktop and a stable base from which to play around a bit more.

Lets see your actual error message - perhaps I'm on the wrong track.

Cheers,
Craig

---

