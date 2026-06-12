---
title: "GNOME fails? - only background loads after login"
date: 2008-10-18
forum: General Help
---

### Post by PC_Nerd on 2008-10-18
Hi,
Fairly new to ubuntu, so I'm not entirely sure what is causing the problem.  When i login to ubuntu ( 8.04, one user) the background loads and sometimes the Desktop icons load.  However most of the time the panels/menus dont load and Im forced to do the following:
ALT + CTRL + F1
Login
$sudo shutdown now

Once I've done that it brings up the recovery menu.  I select normal boot - and login again.... everythings working.

It happens 95% of the time when I login, however the desktop environment often freezes in the middle of doing something else.

I've searched google and had no success because I think I might be in the dark about what to actually search for.  "ubuntu 8.04 freezes after login" seems to bring up a few random things none of which have worked for me.

Thanks for your time,
Jack

---

### Post by PC_Nerd on 2008-10-19
Update:
I ran memtest ( that came with ubuntu when I installed it).... and after running for over 6 hours - it didnt throw out any error.

Any suggestions?
Thanks

---

### Post by steveydoteu on 2008-10-19
Have you recently installed any other window managers?

Even if the answer is no, at the login prompt check that the session it is attempting to load is GNOME. If it is, alter it to failsafe gnome, then see if it will load as desired.

---

### Post by PC_Nerd on 2008-10-19
From memory I did when i was trying to get audacity working,... though I dont remember what it was.....

is there some way through the terminal that I can get it to list the window managers, and then uninstall?

Thanks
** I wasnt aware that I shouldnt have installed the extra window manager - as i thought that it would run on top of gnome ( shows my understanding of linux :P)

Thanks

---

### Post by steveydoteu on 2008-10-19
Take a look at the session list at the login. IT will list anything extra that has been installed.

Installing other window managers is not a problem, you just need to make certain that it is indeed trying to load GNOME.

In my case I had installed openbox and did not realise it was loading as default.

---

### Post by PC_Nerd on 2008-10-20
Ok,

At login it lists the following options:
Last session
Run Xclient script
GNOME
remote login ( or similar)
failsafe GNOME
failsafe terminal ( i think)

I removed Avant, however im still having the problem - where nothing loads.  generally I can start one application ( which i alway schoose terminal so i can start other apps).  I;ve tried Xclient, GNOME and failsafe gnome and all of them have a similar issue ( however when i select GNOME it simply freezes on the beige color between login and desktop).

Any other suggestions? - thanks

---

### Post by PC_Nerd on 2008-10-21
*Bump*
Thanks for the help so far but problem not solved.  I dont particularly want to reinstall ubuntu, and Im sure that doing so would be a little too dramatic?

Any suggestions would be great.
Thanks

---

### Post by tedrampart on 2008-10-24
I seem to be experiencing this issue as well on one of the machines I maintain.  

although I'm running gutsy.. this happened after I updated in apt-get yesterday..

EDIT: I got access to the machine with the problem and could login fine with my admin account, and could create a new temp user for my clients to use til I can get more solved in the meantime.. have you tried other user accounts?

---

### Post by PC_Nerd on 2008-10-24
Hi,

Creating a new user through the terminal works, and ive been logged into this use for about an hour now and nothing has stopped working etc.

Since its working how can i "repair" my other user, because I dont particularly want to migrate all the files and settings across etc.?

Thanks

Edit::  Just to clarify, the user that isnt working works fine when in terminal - no issues.  its simply the GUI side of things that screw up etc.Thanks

---

### Post by PC_Nerd on 2008-10-24
Hi,
When terminal stopped responding ( for some reason if often goes directly to a plain white screen withough the prompt [whatever] $    etc.  When i force quit it gnome panels disapear and the alt+f2 shortcut stops working.  the only method is to ctrl+alt+f1.

Any ideaS?

* this is on the new user.

---

