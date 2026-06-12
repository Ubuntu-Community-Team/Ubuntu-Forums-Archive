---
title: "Help Needed With adesklets"
date: 2008-10-28
forum: General Help
---

### Post by Mark76 on 2008-10-28
I was looking for a weather applet for my openbox desktop session and I remembered adesklets. So I installed the package from the repository, ran the installer and installed the weather applet along with calendar, newsfeed and notes applets.  But now I'm having problems running them. To start with, running the command "adesklets" in a terminal gives no indication that anything is wrong, yet it seems to be a bit of a lottery as to whether or not they'll start. And when they do start they have an unattractive grey background (though I do know they can do fake transparency). The second problem is how to start them on log in. I'm using openbox-session for a desktop environment; so I assumed that adding adesklets & to the autostart menu would do the trick. But it hasn't.  The third, and final (so far), problem is that the configuration option in the right click menu doesn't work.

Anyone know what to do? :confused:

---

### Post by Ginsly on 2008-11-02
You need to add which Desktop you are using to the start command....

adesklets --nautilus  (Gnome)
adesklets --xfce4     (XFCE)
adesklets --kde       (KDE)

I found this helpfull the first time I used adesklets
[http://ubuntuforums.org/showthread.php?t=183709&highlight=adesklets](http://ubuntuforums.org/showthread.php?t=183709&highlight=adesklets)

---

### Post by Ginsly on 2008-11-02
Ok, sorry, I answered too soon, I see now your using openbox  :oops:

---

### Post by Mark76 on 2008-11-02
Yeah. Don't worry, I worked it out in the end (no idea how though).

---

