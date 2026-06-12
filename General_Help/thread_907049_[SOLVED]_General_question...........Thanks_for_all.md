---
title: "[SOLVED] General question...........Thanks for all the help!"
date: 2008-09-01
forum: General Help
---

### Post by ^^rac on 2008-09-01
I love Ubuntu!!

I dont think ill use MS again :)
Thanks for all your help here guys!!

1) I have 2 questions......When one press ctrl + alt + F1, you go to some kind of console (Or terminal)

How do you get back to the Ubuntu gui?


2) Also, if Ubuntu hangs (I had problems with Utorrent in Wine, but its sorted) What do you do to end that process for instance?


Thanks guyssssss!

---

### Post by eggdeng on 2008-09-01
1) Ctrl + Alt + F7
2) Right click on the panel, choose Add to Panel and choose the Force Quit item. Click Add. Now, you can kill a misbehaving app by clicking first on the Force Quit icon, then on the app window.

---

### Post by jerome1232 on 2008-09-01
Well you have 7 virtual consoles, tty1-7, to activate them ctrl+alt+F1-7. Ubuntu starts X up on tty7 so if you wanted to get back to the gui you would hit ctrl+alt+F7.


Depending on what's hanging your system you can hit ctrl+alt+backspace to restart the x server (and all gui programs along with it)

Or lets say utorrent froze up again
```
ctrl+alt+F1
killall wine
```

or to find the exact process and kill it
```
ps aux | less    # now look for you app that froze up and note it's pid number
kill <pid of app you want to kill>
```

If that didn't kill it
```
kill -9 <pid of app you want to kill>
```

if all else fails you can raise a skinny elephant
push and hold alt+sys req
**R**aising
**S**kinny
**E**lephants
**I**s
**U**tterly
**B**oring

A few seconds after the b and your system will reboot, this is a graceful reboot and flushes writes to disk etc.

---

### Post by ^^rac on 2008-09-01
Thanks guys!

Appreciated!

---

### Post by _sAm_ on 2008-09-01
If a program with GUI hangs press Alt + F2 and type in xkill. Your mouse can now kill:-) click on the program that you want to kill and it will be shut down.

---

