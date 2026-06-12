---
title: "[SOLVED] compiz and emerald"
date: 2008-10-12
forum: General Help
---

### Post by metalmaniac248 on 2008-10-12
i just managed to somehow change my resolution to something like 1124x1000 and my screen was messed up, i tried editing xorg but that didnt work, 

and i couldnt change it through the screen resolution method


upon login, i was presented with a window sayin that ubuntu was running low graphics mode, and from there i configured the settings back what they should be (1024x768 ) 



however now, i can't run my compiz effects, AWN, or emerald,


any ideas 


PS. 

i have been having issues with my logon screen being the wrong resolution, however i have somehow managwed to fix this by this series of events

---

### Post by overdrank on 2008-10-12
> **metalmaniac248 said:**
> 




however now, i can run my compiz effects, AWN, or emerald,




Hi and I assume you mean can't. What is the model of the graphics card?
What did you change in the xorg.

Moved :)

---

### Post by metalmaniac248 on 2008-10-12
erm, yes i did mean can't 


well i have a nvidia card, 

and in xorg i just changed the screen resolution under "monitor" from 800x600@60 to 1024x768@60 

however as i said this didnt actually change my screen resolution



PS.

i just tried to open google earth and it's now giving me an message saying that it could not detect my graphics card driver (if that is of any use to you)

---

### Post by overdrank on 2008-10-12
> **metalmaniac248 said:**
> erm, yes i did mean can't 


well i have a nvidia card, 

and in xorg i just changed the screen resolution under "monitor" from 800x600@60 to 1024x768@60 

however as i said this didnt actually change my screen resolution



PS.

i just tried to open google earth and it's now giving me an message saying that it could not detect my graphics card driver (if that is of any use to you)

Ok under system, administration is your driver enabled?

---

### Post by metalmaniac248 on 2008-10-12
it wasnt enabled so i enabled it and i got this error

```


E: /var/cache/apt/archives/nvidia-glx-new_169.12+2.6.24.13-19.45_i386.deb: subprocess pre-installation script returned error exit status 2
```

---

### Post by metalmaniac248 on 2008-10-13
i have also been having problems updating my system whenever i do i get this
error


```
W: Failed to fetch http://giss.tv/~vale/ubuntu32/./libquicktimehv_2.1.0-2svn20080707ubuntu_i386.deb
  404 Not Found

```


i think this may be linked to the problem i am having with getting my nvidia drivers

---

### Post by metalmaniac248 on 2008-10-13
issue now resolved thanks to envy ng

---

