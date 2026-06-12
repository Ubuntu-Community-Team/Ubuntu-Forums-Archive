---
title: "Compiz Major Problem!!!"
date: 2008-09-23
forum: General Help
---

### Post by Pan-Head on 2008-09-23
I was trying to activate compiz on my computer by doing something a read which said something along the lines of opening the konsole and typing "replace --compiz" so i did, then it freaked out and now i have no bar at the top of my windows that enables me to exit, minimize, or maximize the window. so i tried restarting and it's still like this, how do i undo what i just did?

---

### Post by Pan-Head on 2008-09-23
Oh and one more thing, the reason i was enabling it is because in the advanced windows settings, the desktop cube wasn't in there...so if after this problem somebody could help me with the cube that would be great! :-)

---

### Post by 16777216 on 2008-09-23
To get window borders back restart metacity. ```
metacity --replace
```
I would then recommend installing **fusion icon**. ```
sudo apt-get install fusion-icon
```
It will then be in the **System Tools** menu.
Fusion icon will let you pick a window manager from those you have installed compiz, metacity, kwm, openbox, etc..
And if you choose compiz it will let you choose a window border to use with it. Emerald or the metacity theme. ( I think this is what did not start giving you no window borders in compiz. )
I hope this helps you.

---

### Post by Pan-Head on 2008-09-24
thank you so much for this advice! I'm sure it would have worked if wubi didn't hate my computer. i was trying to boot into kubuntu to try what you said, but when i tried, i got the screen that i've gotten like 10 times before...

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of comands.

(initramfs)_

---

### Post by 16777216 on 2008-09-24
Wubi was a good idea but in my opinion is the biggest P-O-S to fall from Canonical's backside. 
( I apologize to any and all people who took part in Wubi, I know it was/is a daunting task and I applaud your efforts but the current implementation has been a huge failure for me and most of those that I know that have tried it. 
So, sorry if my words are harsh. )

---

### Post by Kevbert on 2008-09-24
With regards to compiz, what display card do you have ?  It will only work with nVidia, ATI and Intel display cards (and not all of them).

---

### Post by Pan-Head on 2008-09-24
I've got an nvidia ge-force 6600. I'm probably going to upgrade soon though. But yeah, think i've had enough of Wubi, but till i get another computer, i've gotta stick with windows (have bout $100 worth of games on here that i don't wanna give up.) thanks for your help!

---

### Post by Wolfhere on 2008-09-24
The line was supposed to be 'compiz --replace'. I have better luck with compiz-decorator --replace.

the fusion-icon is awesome (not the compiz-switch). Check to make sure you have the windows-decorator in the ccsm (compiz configurator) enabled.

---

### Post by Kevbert on 2008-09-25
> **Pan-Head said:**
> I've got an nvidia ge-force 6600. I'm probably going to upgrade soon though. But yeah, think i've had enough of Wubi, but till i get another computer, i've gotta stick with windows (have bout $100 worth of games on here that i don't wanna give up.) thanks for your help!

That card will work fine with compiz (I'm using a 7600).  Have a look at the end of your /etc/X11/xorg.conf file and check that the following is added or is there:
```
Section "Module"
	Load		"glx"
EndSection
```
Rather than using wubi why not set up your PC to dual boot Windows and Ubuntu (I heard that wubi can be a bit troublesome - but have not tried it myself).  As you can see from my signature I'm multibooting.

---

