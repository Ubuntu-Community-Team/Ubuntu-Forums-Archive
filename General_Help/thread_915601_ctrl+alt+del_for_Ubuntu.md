---
title: "ctrl+alt+del for Ubuntu?"
date: 2008-09-10
forum: General Help
---

### Post by PsychedelicWonders on 2008-09-10
Alright everyone knows that when you press ctrl+alt+del in windows you get the task manager to see what programs and applications are running.

Is there anything like this in Ubuntu?

Sometimes I lose a program and need to find it or I need to force one to shut down.

Also, is there a differnce between "programs" & "applications" or are they the same thing?

---

### Post by mick222 on 2008-09-10
there is the system monitor
 system--> Administration --> system monitor
 but i dont know a keyboard shortcut

---

### Post by panther_sn on 2008-09-10
Ok I have in one of my panels two useful programs which will do as u ask, one is "force quit" the other is "system monitor"  To add these to a panel righct click on the panel and select add to panel.  Now force quit you use by clicking it and then click the crossbars on the program that isn't responding.   The system monitor is useful to find out what system programs/resources are being used.

And no no real difference between programs/applications.

Hope this helps

---

### Post by PsychedelicWonders on 2008-09-10
so isnt there a "force quit" in system monitor?

System monitor def is what I was looking for.

I'm able to force programs to shut down from there right?

there isnt a keyboard short cut though huh?

---

### Post by joshuachad on 2008-09-10
the only thing I know of is from the commmand line. Say you want to kill firefox. Open a terminal and type "ps -eaf | grep firefox". The output looks like > n3m0      4102     1  0 01:29 ?        00:00:00 /bin/sh /usr/lib/firefox-3.0.1/run-mozilla.sh /usr/lib/firefox-3.0.1/firefox

That first number 4102 is called a PID. If you then type "sudo kill -9 4102" the program will close.

Hope that helps in case. I know  you were looking for a GUI solution.

---

### Post by u-slayer on 2008-09-10
Install Compiz and you can create one easily enough. Create a key binding to gnome-system-monitor. I tried to do this with CTRL+ALT+DELETE but it was taken by the stupid shutdown windown. How do I unbind the shutdown window?

---

### Post by sonofusion82 on 2008-09-10
in Kubuntu/KDE, it is Ctrl-Esc to get the System Monitor.
however, i still prefer "top" or "ps aux" commands.

---

### Post by pansz on 2008-09-10
Windows way is not a good way since when there is some bad program hanging the gui, then task manager may not draw at all. Or if you are playing a Full-screen game, it may refuse to switch back.

In Linux there is always a brute force way: Ctrl-Alt-F1 will bring you to the command prompt. login here, then use the "killall" command.

e.g. "killall firefox " will send SIGTERM to all firefox processes. (this is like close program in tab 1 of windows task manager)
if that does not end the firefox,
"killall -9 firefox" will send SIGKILL to all firefox processes. (this is like close program in tab 2 of windows task manager)

usually, you can use "top" command here to see which process eats up 99% of CPU. (this is like viewing tab 3 of windows task manager)

press Ctrl-Alt-F7 will send you back to the X Window GUI.

---

### Post by lakersforce on 2008-09-10
> **PsychedelicWonders said:**
> so isnt there a "force quit" in system monitor?


Right-click on the process and choose *terminate process*

---

### Post by u-slayer on 2008-09-10
> **joshuachad said:**
> the only thing I know of is from the commmand line. Say you want to kill firefox. Open a terminal and type "ps -eaf | grep firefox". The output looks like > n3m0      4102     1  0 01:29 ?        00:00:00 /bin/sh /usr/lib/firefox-3.0.1/run-mozilla.sh /usr/lib/firefox-3.0.1/firefox

That first number 4102 is called a PID. If you then type "sudo kill -9 4102" the program will close.

Hope that helps in case. I know  you were looking for a GUI solution.

WTF!!? so complicated?

Try this: killall firefox

I just blew your ******* mind, didn't I?

---

### Post by ronnielsen1 on 2008-09-10
I know that Ubuntu Tweak will enable the ctrl-alt-delete - not that you really need it 
[http://ubuntu-tweak.com/2008/07/29/improved-version-ubuntu-tweak-035-released.html](http://ubuntu-tweak.com/2008/07/29/improved-version-ubuntu-tweak-035-released.html)

---

### Post by Lary Grant on 2008-09-10
> **u-slayer said:**
> WTF!!? so complicated?
Try this: killall firefox
I just blew your ******* mind, didn't I?

Why does Firefox require me to do this constantly?  Can't it start up in a more intelligent way and kill old instances of itself if necessary?  I don't mind it too much myself, but this is very unfriendly to newbies.

---

