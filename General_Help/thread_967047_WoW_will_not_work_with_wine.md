---
title: "WoW will not work with wine"
date: 2008-11-01
forum: General Help
---

### Post by enaelis on 2008-11-01
To Ubuntu gurus and the like:

    I enjoy playing wow (World of Warcraft) , and would like to do so on my Ubuntu partition, I have gone through numerous guides on how to get wow running in wine, and so far nothing is working. I have had similar problems to others, but the things that solved their problems didn't solve mine. When I start wow.exe with wine, the only thing that comes up is a black screen. I can hear the sounds of the new login background, but there is absolutely no graphics whatsoever. opengl is being used, and yet I still have the same problem. also, before the completely blank screen comes up, the monitor goes black, and a box appears in the middle that says: 

H:30 - 80kHz
V: 50-75Hz

However I'm pretty sure thats just my monitor being stupid.
I would greatly appreciate anyones help so that I may have no life once more!:)

---

### Post by geirha on 2008-11-01
It's switching to fullscreen mode, but the fullscreen mode's refresh rates are going beyond your monitor's specs. Try running it in windowed mode by either adding the -windowed (or maybe -window, don't remember) option to Wow.exe, or by editing WTF/Config.wtf in the World of Warcraft directory and adding the line ```
SET gxWindow "1"
```

You might have to add your monitor's specs to xorg.conf to be able to run in fullscreen mode.

---

### Post by enaelis on 2008-11-01
thank you, I'll try that!

---

### Post by enaelis on 2008-11-01
It works! but it is very laggy, I'll mess around and see if I can fix that, thank you again!

---

### Post by enaelis on 2008-11-04
Alright, it works fine, just as well as it used to on my windows partition. However, I am having issues with the mouse. It is very laggy, and due to this problem I did a search on this problem in the forums. It turns out that  opengl doesn't have mouse hardware support for windows, which means that when I run WoW in wine, the mouse is taken care of by the software, and, due to my relatively weak computer the mouse problem renders the game virtually unplayable. Is there any way I could get opengl to have mouse hardware support? (it has it on mac computers). Now, thinking logically, both mac and linux are unix based, does this mean that I could just use the mac version of WoW and/or opengl? I realize that that is probobly a noob question, but I am really sick of switching back to windows xp every time that I want to play World of Warcraft. please notify me if there is any way to get the mouse to work, (such as a hack, or mod) anything other than switching out of opengl, as doing so would make wow unplayable for me. Thank you! ^_^

---

### Post by enaelis on 2008-11-05
*bump*

---

### Post by TORRO89 on 2008-11-05
the lag is associated with with blizzards anti cheat software. need to be carefull it monitors all backround applications and open files.

---

### Post by enaelis on 2008-11-06
I do not, and have never used cheats, why would this be affecting my computer? also, I posted above that I believe I already know what the problem is, I just need a fix. I need to be able to use opengl hardware mouse support with linux, opengl hardware mouse support exists on macintosh computers, and using anything but opengl with wine would render WoW unplayable on my machine. (I still need a fix!)

---

### Post by enaelis on 2008-11-19
could someone at least tell me if there is no soltion?

---

