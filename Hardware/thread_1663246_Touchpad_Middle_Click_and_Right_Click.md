---
title: "Touchpad Middle Click and Right Click"
date: 2011-01-09
forum: Hardware
---

### Post by enceladus47 on 2011-01-09
On the touchpad when I tap with two fingers together it right clicks and when with three fingers it middle clicks... which is very handy, but is there a way to switch them ?:) (have a two finger tap do a middle click)

I have a Toshiba a100-811
Thanks :)

---

### Post by pi/roman on 2011-01-09
```
synclient -l
```You should see a list of options and values. Look at tapbutton2 and tapbutton3, those are your current settings for 2 and 3 finger tapping. If tapbutton2 is 3 and tapbutton3 is 2 you can reverse them by
```

synclient tapbutton2=2
synclient tapbutton3=3
```

Actually it's probably the other way but you get the idea.

---

### Post by enceladus47 on 2011-01-09
Browsing just became a little easier, thanks :)

---

### Post by enceladus47 on 2011-01-09
Also is there a way to keep those settings after a restart?

---

### Post by pi/roman on 2011-01-09
I have a guide for it here:
[[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1401645[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1401645")

You are already at step 4 permanent configuration.  Select either part a b or c depending on which distro you are using, although actually some methods are interchangeable but some are not but I have verified the ones I listed.

---

### Post by enceladus47 on 2011-01-09
Thanks, I had already tried putting the commands in startup applications before posting (5a), now I tried 4c and 5b and neither worked :confused:
I mean in 5b the code works alright, but after putting in startup applications it still doesn't work on start-up.

---

### Post by pi/roman on 2011-01-09
Thanks for the feedback. I will find a solution.

---

### Post by pi/roman on 2011-01-10
Here's a duct tape and hot glue fix for you. Maybe someone can come up with something more appropriate. 

Create a file named syntaps, or whatever you like, and place the following in it

```
sleep 10; xinput set-int-prop TouchPad "Synaptics Tap Action" 8 0 0 0 0 0 2 3
```The 10 second sleep timer will allow it to get over period at startup up where the command seems to be blocked. Make it executable and place it in /usr/bin then make a startup command for it. You will have to run it again when it wakes up from suspend mode so you can press alt/f2 then type "syntaps" or whatever name you choose. Maybe there is a way to make it automatically  run upon resume.

I willl update the startup cammands section of my guide to run commands from a delayed script so someone else doesn't have the same problem.

---

### Post by enceladus47 on 2011-01-10
Okay that works perfectly, thanks. :)

Before your post I had tried restarting around 20 times and it worked about 3-4 times but didn't get the chance to report it. I didn't understand it and definitely didn't think of the delay idea, but that explains it.

---

