---
title: "[SOLVED] xrandr screen rotation problem"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by Wamoc on 2008-02-05
Ok, So here is my problem, when I rotate the screen, sections of the display wont refresh properly.  If I do things so that portions of the screen refresh, then it looks right.  I know it isn't the programs I am using because the desktop does this too.

To rotate I am using the command xrandr -o left.  I know that my card has this capability because I was able to do it in windows no problem when I first got it (it is a tablet).

Any help with this would be greatly appreciated.

---

### Post by oldsoundguy on 2008-02-05
you have to have the restricted drivers installed in Linux.  At present only nVida and ATI have such available at their sites, and the ATI is NOT reliable at all.  Otherwise you are faced with writing a lot of command lines for your video. (which I have never done, as I switched all of my machines to nVidia and used ENVY to install the drivers and support software .. all of my screens rotate flawlessly, but all are DESKTOP units.)

---

### Post by Wamoc on 2008-02-05
Actually, my card is not an NVidia or ATI.  It is an integrated Intel GPU. Any ideas for what to do?

---

### Post by oldsoundguy on 2008-02-05
actually Google is your friend:
[http://ubuntuforums.org/showthread.php?t=604896](http://ubuntuforums.org/showthread.php?t=604896)

This MAY do it, then again, it MAY NOT!

---

### Post by Wamoc on 2008-02-05
This fixed it. Thank you very much for your help.

---

