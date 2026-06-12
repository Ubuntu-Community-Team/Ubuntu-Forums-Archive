---
title: "HELP! blank screen due to a change in resolution"
date: 2008-07-25
forum: General Help
---

### Post by skribbulz on 2008-07-25
I was taking on more than i could handle, and started messing with the resolution on my laptop. When I restarted, the loading screen came up and then the screen goes blank.

What can I do to fix this??? I've researched and tried about a million different things...I'm fairly new to all this. I don't know what information you may need, but please do let me know if you can help. 

THANKS!!!

---

### Post by argail1980 on 2008-07-25
what exactly did you do?

try to change to the console by hitting CTRL+ALT+F2. loging with ur username and password. then enter:
```
nano /var/log/Xorg.0.log
```
Lines beginning with '(EE)' are errors, post them please
also check

```
nano /etc/X11/xorg.conf
```

and post the contents of that file here.

---

### Post by skribbulz on 2008-07-25
Okay, so when I hit CTRL+ALT+F2 it brings me to a log in screen but then it starts saying its loading all this stuff and then it flickers and goes back to a blank screen before I can even log in. Also, when I pressed the button to turn off my laptop and then pressed CTRL+ALT+F2 it brought me to the login screen but I wasn't able to log in before it shut off.

When I typed in that 1st code, there wasnt anything in there...


I'm on a different computer so is there a specific part or the xorg file that i could post?

---

### Post by argail1980 on 2008-07-26
The problem you are describing sounds like a problem with the graphics driver or the configuration. It seems to me that the graphical ionterface is restarting over and over, that's why the login prompt disappears again and again. OK here's some explanations and some ideas:

When you make changes in the resolution, the file /etc/X11/xorg.conf is changed. So if you would be able to change it back, you could fix your problem.

The other file contains the log of the X server (the graphical interface). There we could find hints what exactly went wrong.

Do you have an SSH server installed on the broken machine? In that case you could login from another computer.

Possibility No.2: get an Ubuntu alternate CD and put it into your broken machine. from the boot menu you should be able to change a rescue console. From this console you can access the file system of your computer and try to revert the bad changes in your xorg.conf (and get it's contents to post here)

---

### Post by skribbulz on 2008-07-29
when i put my disc in and restart it doesnt come up at all? 


GRR this is so frustrating im really stuck at this point i dont even care if i have to reformat my laptop just for it to work but now my ubuntu live disc isnt even working!

if someone could please walk me through this it would be much appreciated!!

---

### Post by skribbulz on 2008-07-31
BUMP!

please help

---

### Post by argail1980 on 2008-08-02
have you tried with the ubuntu alternate CD? I have no experience with the live cd.
What exactly happens if you use the live cd?

---

