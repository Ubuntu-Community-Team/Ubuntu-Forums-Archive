---
title: "How to disable ambient light sensor on Compaq nc4200"
date: 2008-09-24
forum: Hardware
---

### Post by lotus49 on 2008-09-24
I have a Compaq nc4200 on which I have installed 8.04.

The only problem I have is that the screen is REALLY dim.  So much so that despite having good eyesight, I can barely read the screen sometimes.  The brightness buttons do work but it is already on the brightest setting.

If I shine a torch at the ambient light sensor then the screen gets really bright so I believe that this is the problem and so I would like to disable it.

Does anyone know how to do this?  I have searched high and low and all I can find is other people with the same problem and no solutions.

---

### Post by AA21 on 2010-10-03
Hello, I know this is a really old thread and no one could help the first time but I am having the exact same issue with the light sensor on my NC4200 meaning that unless I'm shining a torch at it the display is almost unreadibly dark.  If anyone could help you'd have my unending gratitude!  I have Googled it of course and did find a fix for an ASUS laptop which said to perform the below changes but I don't have the files they reference on my system (I've tried a locate on them all but no luck) :(

cd /sys/devices/platform/asus-laptop
chmod 755 ls_level
chmod 755 ls_switch
echo 4 > ls_level

Thank you in advance for any help!

---

