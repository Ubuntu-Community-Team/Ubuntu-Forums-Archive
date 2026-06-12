---
title: "[SOLVED] [Intrepid] Nvidia driver overrides cursor theme"
date: 2008-10-31
forum: General Help
---

### Post by Xzoky on 2008-10-31
Hello all,
I just installed Intrepid and enabled the Nvidia drivers for my GeForce 7600 GS, and it appears that it somehow overrides my custom cursor, leaving me with the default cursor theme. However, my cursor looks the way I want when hovering Firefox. Strange, isn't it ?

I tried to change it in Gnome's Appearance settings, in CCSM's General Options, but it does nothing. I tried both driver versions that are available to me ( version 173 and version 177 ), it does not solve the problem either. My custom cursor seems to work only above Firefox and OpenOffice.

The only way to get it the way I want is to disable the Nvidia driver, which is not quite a solution ... I think this is due to the new "NVidia X Server Settings" and its "cursor shadow" option, since I didn't have this issue in Gutsy or Hardy.
Any ideas ?

---

### Post by Xzoky on 2008-10-31
Nevermind, I found the solution :
In CCSM's General Options plugin, in the "Cursor Theme" field, I had typed the name of my cursor theme "Shere Khan X" with spaces between the words, as it was displayed in Gnome Setting's standard cursor selection window.
I used underscores instead of spaces : "Shere_Khan_X", and that solved the problem.

---

### Post by conundrumx on 2008-10-31
CCSM checks the /usr/share/icons folder for the cursor themes.  You need to match the folder name (case sensitive, of course) in order to get things to apply properly.

---

### Post by lkc0987 on 2008-11-06
hi...

i am having the opposite problem..the cursor theme works well in all windows except FireFox..can someone help me!!

ive got intrepid, ccsm, emerald installed

---

