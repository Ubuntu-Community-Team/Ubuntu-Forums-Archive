---
title: "Startup script"
date: 2008-11-24
forum: General Help
---

### Post by zkab on 2008-11-24
I have an application - Navit - that I try to start in fullscreen.
My script looks like:

navit &
sleep 2
wmctrl -a Navit -b add,fullscreen

When I execute the script from a terminal window it works OK but when I specify that the same script should execute as a startup script (xfe Settings Manager/Autostarted Apps) it will not give me a full screen.
Why is there a difference in executing a script from terminal window or as a startup script ?
I have Xubuntu 8.10

---

### Post by geirha on 2008-11-24
My first guess would be that your script gets run before the window manager starts. Is your script the last thing that gets run?

---

### Post by zkab on 2008-11-24
Sounds like a probable cause ... how can I force the startup script to execute after window manager :confused:

---

### Post by Shooree on 2009-03-22
I've got a similar problem, since I also manually added a few entriesto the Autostart Apps, with commands that should invoke scripts in my home folder.

Not one of them really works - not even the conky one, which has a sleep period in it:

#!/bin/bash
sleep 10 && conky;

where am I going wrong?

Also, in my home folder, I can see a file with the same name as that script, but ending with a ".sh~" 

Any help would be greatly appretiated.

---

### Post by tukuyomi on 2009-03-22
You can create a file named .xsession in your $HOME and invoke commands to be run:
Here is mine, for example:
```
rm .xsession-errors
(
        sleep 19;
        conky
)&
gnome-session
```
As you can see, I invoke gnome-session. You'll probably want to invoke xfce-session.
The part in (..) invokes conky, but is delayed by 19 seconds; --this allows compiz (within gnome-session) to start before conky, else (on my computer at least) conky will be displayed on only one desktop.
It's important to add a & after (..) to actually start gnome-session without waiting the delayed conky.
! But do not add & after the last command (gnome-session) !

Hope this helps a bit :)

---

