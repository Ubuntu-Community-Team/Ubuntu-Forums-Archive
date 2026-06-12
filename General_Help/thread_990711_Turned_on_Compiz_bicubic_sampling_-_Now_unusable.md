---
title: "Turned on Compiz bicubic sampling - Now unusable"
date: 2008-11-23
forum: General Help
---

### Post by tom_s on 2008-11-23
I'm using a Dell Inspiron 6000 with Ubuntu 8.10. I have quite a few of the Compiz things turned on (rotating cube etc). Everything was working great.

I selected the "bicubic sampling" widget and as soon as I checked the checkbox my display went black and grey. I see no text, no menus, no nothing - just a vague outline of the cube and a dim shading.

Without being able to see the menus, how do I reset the graphics? Can I interrupt startup at some point before the Gnome desktop gets shown and fix a config file somewhere?

---

### Post by eternalnewbee on 2008-11-23
**Ctrl-Alt-Backspace** will log you out. See if the problem persists after you've logged in again.

---

### Post by Locutus_of_Borg on 2008-11-23
when at the login screen,
hold control+alt and press F2 (my computer's keyboard only works with the left control+alt for some reason)
log in from this terminal
mv .config/autostart/* .
change * to whichever one starts compiz (not on ubuntu now, and not using the autostart directory so i dont know for sure, compiz.desktop seems about close-ish though) just do not run that command without changing the * to the correct entry
exit the terminal and control+alt  F7 back to the graphical login, you should now log in without compiz starting...enter ccsm and turn off bicubic filter, restart compiz, and move the *.desktop file back to the autostart directory:
mv *.desktop .config/autostart/

---

### Post by eternalnewbee on 2008-11-23
I wonder if this works: Press **ALT-F2** and enter ```
metacity-- replace
```
If this works, there's no need to log out. Too bad I didn't think about this before.

---

### Post by tom_s on 2008-11-23
Thanks to both of you for the help. I'm fixed now.

For the record, because I have an autologin (no login screen) things seemed more complex. I *think* that the key steps were:

1. On a new login, press Ctrl+Alt+F2 to get a terminal window. 
2. mv .config/compiz/compizconfig/config .
3. sudo mv /etc/compizconfig/config etcconfig
4. restart computer

It seemed that with the autologin, compiz was starting up before I got my prompt, and writing out a new config file on exit, so I think that 3 was needed (the name etcconfig is chosen at random and I will now delete those files anyway). But I'm not entirely sure.

Still; happy ending. Thanks again.

---

### Post by eternalnewbee on 2008-11-23
Excellent tom_s.
Please mark this thread as solved, under [COLOR="Red"]Thread Tools[/COLOR], at the top of this page

---

### Post by Harry_Iyer on 2008-12-12
> **tom_s said:**
> 

I selected the "bicubic sampling" widget and as soon as I checked the checkbox my display went black and grey. I see no text, no menus, no nothing - just a vague outline of the cube and a dim shading.

_

Faced the exact same problem today . . . someone should report this particular effect!

> **eternalnewbee said:**
> 

**Ctrl-Alt-Backspace** will log you out. See if the problem persists after you've logged in again.

_

Serves no use if there is just a single user . . . Thanks anyway

> **eternalnewbee said:**
> 

I wonder if this works: Press **ALT-F2** and enter 
```

metacity-- replace

```

If this works, there's no need to log out. Too bad I didn't think about this before.

_

Well it works yes, but it gives rise to a whole new problem.

Check the last post by moonlit knight **[[SIZE="6"][COLOR="Blue"]_HERE_[/COLOR][/SIZE]]("http://ubuntuforums.org/showthread.php?t=942529&highlight=metacity+replace+sound&page=2")**

> **tom_s said:**
> 

I *think* that the key steps were:

1. On a new login, press Ctrl+Alt+F2 to get a terminal window. 
2. mv .config/compiz/compizconfig/config .
3. sudo mv /etc/compizconfig/config etcconfig
4. restart computer

_

Doing this really saved my day . . . Thanks a lot. Just 1 request, you could have CODED the commands . . . I was really confused by them at first!

[SIZE="6"][COLOR="Red"]Thanks everyone who helped in this thread . . .!!![/COLOR][/SIZE]

---

### Post by jlobo on 2008-12-23
hola ubuntu forums!
first post!

I think there is an easier way to fix this...

ctrl+alt+f1

```
killall compiz.real
```

```
exit
```

navigate to your compiz settings as usual and turn off bicubic filtering...

reload compiz(you can just go to preferences>appearance and check "normal" on the visual effects tab)

viola!

just thought I'd share what I did with you!

---

### Post by irfan9727 on 2009-01-24
> **jlobo said:**
> hola ubuntu forums!
first post!

I think there is an easier way to fix this...

ctrl+alt+f1

```
killall compiz.real
```

```
exit
```

navigate to your compiz settings as usual and turn off bicubic filtering...

reload compiz(you can just go to preferences>appearance and check "normal" on the visual effects tab)

viola!

just thought I'd share what I did with you!

Thanks! You just saved my day! I nearly uninstalled ubuntu (yes, I used wubi) Thanks!

---

