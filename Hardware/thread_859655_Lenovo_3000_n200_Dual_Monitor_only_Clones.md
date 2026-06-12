---
title: "Lenovo 3000 n200 Dual Monitor only Clones"
date: 2008-07-14
forum: Hardware
---

### Post by sypherz on 2008-07-14
Hello,  New to the forums here so please bear with me. :)

As the title shows i have a lenovo and i can not for the life of me get an extended desktop, it only clones

Now i have searched for help the past few days and i have tried most. the one i keep going back to is editing the xorg.conf file to show a subsection like this:
SubSection “Display”
Virtual 2560 1024
EndSubSection

Now my monitor is a sony that only supports 1024x768 so i assumed 2560 1024 was the resolution which some places on the web motioned too.  Now after editing the xorg.conf file i then add the command and string:
xrandr --output LVDS --right-of VGA
which is also explained in a few places on the net.

Can anyone help?
my lspci:
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

sorry, im also running Ubuntu 8.04
Thanks in advance

---

### Post by sypherz on 2008-07-14
Bump?  :)

---

