---
title: "lost window bar on 8.10"
date: 2008-11-02
forum: General Help
---

### Post by Paul VW on 2008-11-02
Well I have not, but the odd thing is my wifes account has! (by window bar I mean the bit at the top with an "x" in the far right) This has only happened since I "upgraded" to 8.10

I have tried a few things like changing the appearance settings but that does not work

terminal is just a white square, but if I type in "metacity --replace" in it (though this is not easy when you cant see what your typing) I get the window bar back, but if I close terminal then it reverts back.

---

### Post by JECHO on 2008-11-02
> **Paul VW said:**
> Well I have not, but the odd thing is my wifes account has! (by window bar I mean the bit at the top with an "x" in the far right) This has only happened since I "upgraded" to 8.10

I have tried a few things like changing the appearance settings but that does not work

terminal is just a white square, but if I type in "metacity --replace" in it (though this is not easy when you cant see what your typing) I get the window bar back, but if I close terminal then it reverts back.


is compiz installed? as well as compiz settings manager? if so then open up compiz settings manager and open up the "Window decoration". click the button to the right of the input box for the "command" option. close and reboot.

if compiz settings manager isnt installed then install it using:

```
sudo apt-get install compizconfig-settings-manager
```

once its installed then follow the above instructions.

---

### Post by Paul VW on 2008-11-02
I dont have the manager installed, but why does everything work ok on my account?

edit: I have installed it, and followed your instructions, but still no luck.

---

### Post by Paul VW on 2008-11-02
anyone?

---

### Post by nickstephens on 2008-11-02
I have the same problem. Mostly restarting will correct the problem but I can't see any consistency with the problem occurring :-s 

Any ideas suggestions, short of the present suggestion made here of drawing on the screen with a pencil, are welcome :-) The previous suggestion made in this thread isn't a solution, more a temp fix from what I can see.

---

### Post by outerspacerace on 2008-11-02
Is it similar to what's happening to us over here?

[http://ubuntuforums.org/showthread.php?p=6090869#post6090869](http://ubuntuforums.org/showthread.php?p=6090869#post6090869)

May ease your mind to know it's not just on your machine if so...

---

### Post by Paul VW on 2008-11-03
no my problem is the whole window bar is missing, and terminal is a white square! I dont think its a driver issue or my account would be affected as well?

---

### Post by outerspacerace on 2008-11-03
Ah, I understand your problem now.

I'm not at home so I can't explain exactly how, though if you install the Compiz Fusion Icon I think it'll help you fix this problem.

It allows you to easily change window managers and decorators from the system tray and sometimes the refreshing that occurs when you flick between the various options will sort issues out.

You can get it from the repositories via the add/remove option or *maybe* by running this in a terminal:

sudo apt-get install fusion-icon 

I'm not 100% sure if that's the right command though, it may be something like:

sudo apt-get install compiz-fusion-icon

... you get the picture :)

---

### Post by nickstephens on 2009-03-24
This problem just reoccurred with my hardy machine. Seems to be linked to hibernation mode which I dont use very often to be honest. Easily dealt with though. As suggested, download the compiz fusion icon. 

A subsequent solution is to select metacity as your windows manager. Pity you loose fancy graphics but I find the missing windows bar more annoying.

---

