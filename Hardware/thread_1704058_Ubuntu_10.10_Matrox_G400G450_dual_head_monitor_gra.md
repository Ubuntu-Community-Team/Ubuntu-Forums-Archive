---
title: "Ubuntu 10.10 Matrox G400/G450 dual head monitor graphics card monitor unknown fails"
date: 2011-03-10
forum: Hardware
---

### Post by zakchambers01 on 2011-03-10
I have just purchase a new pc but I am using my old matrox G400/G450 dual head/monitor graphics card.  It manages to detect both monitors in the sense that it shows a mirror of the same desktop on both screens.  
If I go into the monitor setup tool there is one monitor detected with the title 'unknown' and the mirror desktops checkbook is greyed out.  I have played with resolutions and refresh rates but nothing changes.  

I was wondering about the mga package but I have the latest version.  The detect screens buttons doesn't do anything, I click and nothing.  I'd like to get it so I have the 2 monitors showing one desktop.

Maybe I need to find the drivers for my specific monitors, although really not sure about this one hence the post.  I know my way around ubuntu but always struggled with hardware issues like this, hence my first post on ubuntu forums.

Hope you can help.  Thanks

---

### Post by dplmartin on 2011-04-17
Has anyone got any answers on this because I have exactly the same need. I've done some research around Xinerama and I've found that Matrox did do some modified drivers [http://www.matrox.com/graphics/en/support/drivers/download/?id=143](http://www.matrox.com/graphics/en/support/drivers/download/?id=143)

I've just not found anything that would make a good step by step guide on how to do it. Here are the resources I've looked at so far:
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)
[http://www.anandtech.com/show/623/1](http://www.anandtech.com/show/623/1)
[http://ubuntuforums.org/showthread.php?p=1773624](http://ubuntuforums.org/showthread.php?p=1773624)

Is someone able to clarify this matter for me?

Thanks in advance.

---

### Post by DCKelley on 2011-06-12
Same basic issue here on a sightly different card, see a dual display (mirror screen) only

Have a dual monitor set-up with a Matrox G550 dual head (which works fine on the Windows side with a grub boot to cope with getting to it), but I _can not see the 2nd monitor _in the Sys->Prefs->Monitors dialog and...

displayconfig-gtk
Produces _no response_  (nothing, just a blank line)  I think this is the key issue at this point, why no config data shown? 

And my xorg.conf file is entirely _empty_ at this time.  

I really have no clue as to how to proceed. The driver itself is loaded, lspci returns:

01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G550 AGP (rev 01)

Any wisdom from those that have dealt with this issue before??

---

