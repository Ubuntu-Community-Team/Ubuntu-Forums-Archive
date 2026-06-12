---
title: "BIG Problem"
date: 2008-07-23
forum: General Help
---

### Post by Shiv4m on 2008-07-23
Hey guys I installed a new login session theme and it doesn't show on my start up. I can't sign in or anything! Is there any other way to logon and change my login session so this doesn't happen again? I really have important information on that computer I hope I don't have to reformat it! :(

Please help as soon as possible! Thank You!

---

### Post by Jinxx on 2008-07-23
> **Shiv4m said:**
> Hey guys I installed a new login session theme and it doesn't show on my start up. I can't sign in or anything! Is there any other way to logon and change my login session so this doesn't happen again? I really have important information on that computer I hope I don't have to reformat it! :(

Please help as soon as possible! Thank You!

Did you try Ctrl + Alt + F2?  That should let you log in to the terminal, and then use startx (I think) to boot up X11.  

That should get you logged in, at least.

---

### Post by the_real_fourthdimension on 2008-07-23
> **Shiv4m said:**
> Hey guys I installed a new login session theme and it doesn't show on my start up. I can't sign in or anything! Is there any other way to logon and change my login session so this doesn't happen again? I really have important information on that computer I hope I don't have to reformat it! :(

Please help as soon as possible! Thank You!

Assuming you get a login screen w/out any fields, you can try Alt+Ctrl+F1, logging in with your info, then typing "startx".

EDIT:  Looks like you beat me by a few seconds, Jinxx :)

---

### Post by Shiv4m on 2008-07-23
Let me try those 2...

---

### Post by ali999 on 2008-07-23
when grub loads up isn't there an option to boot it without loading up gnome or something? i'm pretty sure this brings up a terminal type of screen where you should be able to login and hopefully uninstall whatever it is that you installed.

---

### Post by Jinxx on 2008-07-23
> **the_real_fourthdimension said:**
> Assuming you get a login screen w/out any fields, you can try Alt+Ctrl+F1, logging in with your info, then typing "startx".

EDIT:  Looks like you beat me by a few seconds, Jinxx :)

Haha yeah.  Is it Ctrl + Alt + F2 or Ctrl + Alt + F1?

I see everyone say it's F1, but I've always used F2.  :confused:

---

### Post by Shiv4m on 2008-07-23
I typed in startx and then it says:

Fatal server error:
Server is already active for display0

---

### Post by the_real_fourthdimension on 2008-07-23
> **Jinxx said:**
> Haha yeah.  Is it Ctrl + Alt + F2 or Ctrl + Alt + F1?

I see everyone say it's F1, but I've always used F2.  :confused:

Well, I've never tried F2. :)  I've always just used F1.

---

### Post by the_real_fourthdimension on 2008-07-23
> **Shiv4m said:**
> I typed in startx and then it says:

Fatal server error:
Server is already active for display0

Yeah...  forgot about that.  Before you type "startx", type:
```
 sudo rm /tmp/.X0-lock 
```

---

### Post by Shiv4m on 2008-07-23
This is what it says after I type in startx:

Fata server error:
Server is already active fir display 0
 If this server is no longer running, remove /tmp/ .X0-lock and start again.

---

### Post by Shiv4m on 2008-07-23
> **the_real_fourthdimension said:**
> Yeah...  forgot about that.  Before you type "startx", type:
```
 sudo rm /tmp/.X0-lock 
```

It says '.xo-lock' No such file or directory

---

### Post by the_real_fourthdimension on 2008-07-23
> **Shiv4m said:**
> It says '.xo-lock' No such file or directory

Yeah, this is case sensitive. "X" has to be in caps, and "0" is a zero, not a letter. :)

---

### Post by Shiv4m on 2008-07-23
Ye I got in finally thank you so much! I'm thanking all of you!

---

### Post by the_real_fourthdimension on 2008-07-23
Welcome :)

---

### Post by Shiv4m on 2008-07-24
> **Shiv4m said:**
> Hey guys I installed a new login session theme and it doesn't show on my start up. I can't sign in or anything! Is there any other way to logon and change my login session so this doesn't happen again? I really have important information on that computer I hope I don't have to reformat it! :(

Please help as soon as possible! Thank You!

After this problem was solved, I lost all my themes! Desktop cube, window wiggle, themes, and my DIABLO II! I get a critical error now everytime I try to launch D2 about Direct 3D. I'm sure the code I entered had to do something with it. Is there anyway I can make everything run smoothly how it used to be? Nothing works anymore!

Thank you again :confused:

---

### Post by Jinxx on 2008-07-25
> **Shiv4m said:**
> After this problem was solved, I lost all my themes! Desktop cube, window wiggle, themes, and my DIABLO II! I get a critical error now everytime I try to launch D2 about Direct 3D. I'm sure the code I entered had to do something with it. Is there anyway I can make everything run smoothly how it used to be? Nothing works anymore!

Thank you again :confused:

I don't think that code you used to get back in to your system would've broken all that.  Perhaps what caused it is whatever you did to lock you out in the first place?  The code "startx" is just a command to start X11, the graphical interface.  It is run automatically every time you boot.  

Wish I could be of more help.  Good luck!

---

### Post by Shiv4m on 2008-07-27
After I used that different method to login all my themes and graphics went away, no clue how!

---

