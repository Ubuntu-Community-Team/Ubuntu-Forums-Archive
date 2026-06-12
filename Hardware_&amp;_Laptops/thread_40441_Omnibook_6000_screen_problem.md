---
title: "Omnibook 6000 screen problem"
date: 2005-06-09
forum: Hardware &amp; Laptops
---

### Post by Artanis on 2005-06-09
I have an omnibook 6000 (p3 800, 10gb hdd, 128mb ram). Ubuntu 5.04 installed a treat (I came from CentOS 4.0) and it was up and running in no time. The only problem I have is that when in X (gnome) the top few millimetres of my screen are missing. I can only see the bottom half of Applications etc, it cuts off just above the - in the A, and at the bottom of the screen there is also a few millimetres of taskbar that should'nt be there (Doesnt show up in screenshots, it's about the same size as is missing from the top.

I changed the driver from 'ati' to 'vesa' in the /etc/X11/xorg.conf and it all appears normal, but I'd prefer to use the ATI drivers as gnome ran smoother..

Any help you guys/girls can give me would be great.. because I'm gone for idea's.

---

### Post by Dominik Smogór on 2005-06-26
I had the same problem and it appears that some tingering with xvidtune tool can solve it. Nevertheless inserting the following modeline into monitor section of /etc/xorg.conf file solves the problem permanently on my omnibook:
[FONT=Courier New]Modeline        "1024x768"     65.15   1024 1040 1136 1312    768  768  771  804 +hsync +vsync[/FONT]
Hope this helps.

ps.
Is it a regression bug in xorg. I haven't encoutered it in Warty? Who should I report it to?

---

