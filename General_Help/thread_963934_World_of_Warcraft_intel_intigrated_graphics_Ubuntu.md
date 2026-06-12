---
title: "World of Warcraft intel intigrated graphics? Ubuntu 8.04"
date: 2008-10-30
forum: General Help
---

### Post by xxguitardud3 on 2008-10-30
Has anyone gotten world of warcraft to run successfully on intel graphics?  I have an Intel 915gm 128mb shared integrated card, and im using the i810 driver. Also im using Ubuntu 8.04.

---

### Post by xxguitardud3 on 2008-10-30
Bump

More than an hour an no replies HELLO!!!

Why do people always ignore my posts lol :(

---

### Post by Toribor on 2008-10-30
I've done it in Windows, and it's okay, but never tried doing it with Wine, never bothered. I'm running an xps m1210 with 945g graphics. It's nothing impressive but it's okay. Apparently Wine is pretty good with WoW so it might be worth a shot, but don't expect it to run like a 3rd party graphics controller would...

---

### Post by aztalon on 2008-10-30
I ran WoW on a Dell Inspiron 1300, which I believe has the 915 chipset. It ran fine under Wine, albeit slow with all the graphics turned down to low.

---

### Post by Nurionn on 2008-10-30
On my Notebook, WoW runs pretty well under wine. So I think it's an 


I'm even playing now (at least if server weren't down) but I have an NVIDIA graphic card...




Edit would like to post this tutorial: [http://forums.wow-europe.com/thread.html?topicId=206990759&sid=3]("http://forums.wow-europe.com/thread.html?topicId=206990759&sid=3") (it's in German, but it works)

Some important things:

_Configure wine_ (Sorry, I don't know the exact strings in English, so i'll translate)
- activate pixel shader
- vertex shader = hardware
- allow window manager to control windows
- sound: alsa

_Change wtf.conf_
- [http://echtor2oo3.de/Config.wtf]("http://echtor2oo3.de/Config.wtf") (I just copied that one and changed resolution)

_Registry tweak_
- run the following command in terminal:
```
printf "Windows Registry Editor Version 5.00\n[HKEY_CURRENT_USER\Software\Wine\OpenGL]\n\"DisabledExtensions\"=\"GL_ARB_vertex_buffer_object\"" > $HOME/.wine/drive_c/wow.reg ; regedit -s "C:\\wow.reg" 
```


I made better exprerience playing in window mode. In full screen mode the game disappeared after I changed working display ([CTRL]+[ALT]+[LEFT]) e.g. to search something on the web.



I hope it'll work for you as well as for me.

---

### Post by Dyne87 on 2008-11-21
hey man i feel ur pain. my notebook has an i9xxgm chipset and from what i've come to understand, next to the ati chipsets, we have one of the hardest chipsets for wine gaming. on 2.4 i barely got wow to work under wine. the problem is with the intel drivers. i could play but i couldnt have the minimap open indoors and the ground detail didnt have any "detail" and my box was dubbed "crayola wow". now on the 3.0.3 patch all ui detail (both original ui and addon ui) is either black or white and all fonts are missing and replaced with boxes. the good news is that because windows had graphical errors on some chipsets, blizzard released that adding SET fixedFunction "1" to your config.wtf file fixes the ground detail error and i now have ground detail.

---

