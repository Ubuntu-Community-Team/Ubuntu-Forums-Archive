---
title: "missing window manager after boot up"
date: 2008-07-14
forum: General Help
---

### Post by mnglfiddle on 2008-07-14
To any one interested:

I need some suggestions on something I have never before experienced. My brother-in-law installed Ubuntu on a Toshiba laptop - 7.10 Gutsy - and has been using it for several months.

Yesterday, he booted up and instead of being greeted with his friendly login page, he got a black terminal instead, asking for his username and password. After typing them in, it went to a terminal, with his username@username:~$ flashing at him, and no sign of Gnome. I have been using Ubuntu off and on since Hoary, and continuously since 6.06 (now am happily using Hardy), and have never experienced this. 

I suggested (I was driving at the time and many miles away) he type 'sudo gdm', which got an answer saying 'gdm was already running'. I suggested several other things, but to no avail. He tried safe boot, he tried an older kernel in Grub, and so on. Nothing got his graphics back.

Any idea what might be the problem, and what I can do to check this out.

He stated he had not recently changed any settings or installed any new programs.

Thanks,
Matthew

---

### Post by hal8000 on 2008-07-14
First problem is that gdm has not started, so you may be looking at a gnome problem or X window problem.

Get him to try

startx

at the console after logging in with his normal username and password. If X starts, you'll be working in twm, logout then type

gnome-session

or 
startx gnome-session

to see if gnome starts. Clues may be found in /var/log/messages and /var/log/Xorg.0.log

---

### Post by mnglfiddle on 2008-07-14
'startx' was one of the things I told him, and he said his screen started blinking off and on. Would that give you a clue as to the problem?

---

