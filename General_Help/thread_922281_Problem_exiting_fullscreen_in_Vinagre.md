---
title: "Problem exiting fullscreen in Vinagre"
date: 2008-09-17
forum: General Help
---

### Post by Randis on 2008-09-17
Hi,

I just started using Vinagre. The first couple of times the fullscreen mode worked fine, but now all of the sudden I can only enter it, but not exit. F11 toggles it on but not of. The same with Ctrl+Alt.

The only way to exit the mode that I could quickly think of, was to kill the client from VNC server side.

Am I just being stupid?

Thanks.

---

### Post by sunapi386 on 2008-10-15
I encountered this problem too, I somehow disconnect vinagre in fullscreen, I donno, but the screen was blank when I loaded vinagre. 
Reboots didn't fix it, the program loaded with a grey screen, and it responds to <Alt><F4>

I just fixed the problem by removing, installing, and then syncing.

```
# apt-get remove vinagre
# apt-get install vinagre
```

Hit <Alt><F2> for run box
type in 
```
vinagre --sync
```

Worked for me.

---

### Post by GepettoBR on 2008-11-19
I cna also no longer exit fullscreen mode, and vinagre always starts in fullscreen. Reinstalling and syncing did not work.

---

### Post by Schmoove on 2008-11-26
Same problem here. I fixed it this way:

Go to configuration editor (gconf-editor) and go to **apps > vinagre**

_There I just set:_
window_state = 0
window_height = 100
window_width = 100

Then restart vinagre and you should get a 100x100 window which you can resize to your likings again.

---

### Post by softcrack on 2008-12-18
thank you very much. It works for me.

> **Schmoove said:**
> Same problem here. I fixed it this way:

Go to configuration editor (gconf-editor) and go to **apps > vinagre**

_There I just set:_
window_state = 0
window_height = 100
window_width = 100

Then restart vinagre and you should get a 100x100 window which you can resize to your likings again.

---

### Post by karbolet on 2009-01-18
The white screen is vinagre starting in fullscreen with nothing to display. A hack to get this working is by typing "vinagre reset" and wait about 10 seconds - or you can substitute anything instead of reset, basically this forces it to get an error and go out of fullscreen.

---

### Post by Dongsheng Wang on 2009-03-12
If you know the toggle full screen shortcuts, you can use it to get out of the full screen mode. 

The toggle full screen shortcuts is set to "Super L" key by default.

---

