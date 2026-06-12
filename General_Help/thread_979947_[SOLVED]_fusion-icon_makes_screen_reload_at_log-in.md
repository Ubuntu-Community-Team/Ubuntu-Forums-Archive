---
title: "[SOLVED] fusion-icon makes screen reload at log-in"
date: 2008-11-12
forum: General Help
---

### Post by christoforever on 2008-11-12
This is just an annoying thing, does not kill my experience, just annoying. With compiz enabled everything loads up fine when I first power up. However when I have compiz fusion set to run on boot up, the desktop loads then fusion-icon loads and blanks out the screen and then redraws everything. Everything works fine its just the reloading of the screen with fusion-icon that bothers me. Anyone else have this problem or know how to solve it?

---

### Post by binbash on 2008-11-12
I have the same problem and waiting for a solution also.

---

### Post by christoforever on 2008-11-13
I should mention that this has been going on for quite some time, meaning for the past few releases at least. It's definitely gotten better, but still a minor hiccup. Just annoying is all

---

### Post by christoforever on 2008-11-17
Solved the problem... For anyone else having this issue this is what you need to do:

1.) sudo gedit /usr/bin/gnome-wm
2.) add this line to the first available space at beginning of file   
     WINDOW_MANAGER=/usr/bin/fusion-icon
3.)save and exit.

On the next restart of your system fusion icon is run first before metacity, which is why you get the hiccup, and everything works as it should.

---

### Post by inigomontoya on 2008-11-17
Could I use this option for only one user?  I use compiz while my wife does not.

---

### Post by loomsen on 2008-11-17
> **christoforever said:**
> Solved the problem... For anyone else having this issue this is what you need to do:

1.) sudo gedit /usr/bin/gnome-wm
2.) add this line to the first available space at beginning of file   
     WINDOW_MANAGER=/usr/bin/fusion-icon
3.)save and exit.

On the next restart of your system fusion icon is run first before metacity, which is why you get the hiccup, and everything works as it should.

This really kicks somes serious b*tts! Thanks, jeez, I've been lungin so long for a solution for this very annoying problem of compiz replacing itself and therefore taking so much time to actually come alive.

Thanks again.

---

### Post by christoforever on 2008-11-18
Seeing as how this runs fusion-icon without running it through sessions, it may do that for all profiles, but im not sure. I only have me on my laptop and never use other users. I would be interested to know what happens when you put it in your account and then what happens when your wife logs in.

---

### Post by christoforever on 2008-11-18
Also i mis-spoke on why this works. Looking through the gnome-wm file, it seems compiz loads on its own if present or set to load. When you add compiz-fusion to your sessions, gnome loads compiz first, then reloads it through fusion-icon, which is where the hiccup comes in. So if you simply by pass all that and set the default window manager as fusion-icon. it will run that script instead which will load compiz for you... only once... so no hiccup.

---

### Post by loomsen on 2008-11-18
Yes, there are multiple issues/possible issues.

However, this was quite a nice move of you, even if it didn't solve your problem. Cause, as you said, if your wife logs in, fusion-icon will do the window-management. /usr/ is a shared lib between given users, maintainable only by root.

Humm, you may want to issue 
```
pstree -n
```

This will show running processess, sorted by PID and in a tree form, like here:
[[img]http://www.ubuntu-pics.de/thumb/5940/screenshot_01_4fz3Br.png[/img]](http://www.ubuntu-pics.de/bild/5940/screenshot_01_4fz3Br.png)
Now, in my case, I'd probably use the seahorse agent to issue what should happen for which user if I was you. See it's manual. Oh, and take a look at this too, removing gnome-screensaver did the most of the trick actually:
[[img]http://www.ubuntu-pics.de/thumb/5925/screenshot_14_K3FF25.png[/img]](http://www.ubuntu-pics.de/bild/5925/screenshot_14_K3FF25.png)  [[img]http://www.ubuntu-pics.de/thumb/5926/screenshot_15_25ABnd.png[/img]](http://www.ubuntu-pics.de/bild/5926/screenshot_15_25ABnd.png)

Now thats really a massive boost, tho it didn't really take 2 minutes, it is pretty obvious that onee should try and live without gnome-screensaver :)
xscreensaver for instance is pretty lightweight, and ships with even more screensavers. Or just use compiz screensaver plugin, at so am I doing.

But, where is actually the problem, even if your wife doesn't use compiz? She'll have to look at the icon in the tray, ok, but what else?
Just create a profile for her, unchecking every single plugin and chosing metacity as window decorator. Or gtk. Whichever, except the icon she won't notice any difference.

---

