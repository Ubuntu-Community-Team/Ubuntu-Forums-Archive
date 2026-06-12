---
title: "[SOLVED] Installing fonts."
date: 2008-10-20
forum: General Help
---

### Post by fullmetalgerbil on 2008-10-20
Hi, I'm running 8.04 Hardy and I can't seem to get fonts installed. I did manage to install a few font packages available via Synaptic, however I've tried to copy other ttf font files to usr/share/.fonts with no success. I'm just not given the "paste into folder" option when I right click on the true type fonts folder inside .fonts-and when I went to change permissions I was informed that root was the owner of the folder so I wasn't allowed to write into it, nor change permissions.
Cetainly this could all be fixed by some terminal work, however I can't get root privileges through the command line. Not even su- works.
This is the really irritating thing about Ubuntu, perhaps the one and only thing I can barely stand about it, the whole superuser/root dichotomy. If I can go ahead and potentially destroy my system using sudo, then why is it I have to jump through hoops to get root privileges?
Sorry about the tangent. I really do love Ubuntu, I just need some help installing fonts.

---

### Post by kostkon on 2008-10-20
> **fullmetalgerbil said:**
> Hi, I'm running 8.04 Hardy and I can't seem to get fonts installed. I did manage to install a few font packages available via Synaptic, however I've tried to copy other ttf font files to usr/share/.fonts with no success. I'm just not given the "paste into folder" option when I right click on the true type fonts folder inside .fonts-and when I went to change permissions I was informed that root was the owner of the folder so I wasn't allowed to write into it, nor change permissions.
Cetainly this could all be fixed by some terminal work, however I can't get root privileges through the command line. Not even su- works.
This is the really irritating thing about Ubuntu, perhaps the one and only thing I can barely stand about it, the whole superuser/root dichotomy. If I can go ahead and potentially destroy my system using sudo, then why is it I have to jump through hoops to get root privileges?
Sorry about the tangent. I really do love Ubuntu, I just need some help installing fonts.
Just copy them to the *.fonts* folder that exists in your home folder. If it does not exist, just create it yourself.

---

### Post by Alpha-geek on 2008-10-20
Open a root session of Nautilus by hitting alt + F2. type this in command box,```
gksu nautilus
``` Click "run", then enter your password. You can then drag & drop fonts to your hearts content.

---

### Post by fullmetalgerbil on 2008-10-20
Thanks Alpha Geek, gksu worked like a charm.

---

