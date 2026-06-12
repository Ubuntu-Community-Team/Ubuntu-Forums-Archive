---
title: "Change Run Level in Hardy"
date: 2008-07-29
forum: General Help
---

### Post by Coldmiser487 on 2008-07-29
I am trying to track down an issue I am having where my computer locks up when trying to reboot (or shutdown).  

To do this, I would like to see exactly what is the last thing it attempts to run before it locks up.  

I'm assuming the easiest way to do this is to change to run level 3 and then shutdown when I'm not in xWindows.  

However, I do not know how to change the run level in Hardy, I thought it was in /etc/inittab but there isn't one in Hardy.

Anyone have any ideas for me?
I appreciate any and all comments

---

### Post by rEbyTer on 2008-07-29
The simplest method is to install rcconf.

---

### Post by Titan8990 on 2008-07-29
Run levels are different in Debian based distros then they are in basically every other. In debian run levels 2-6 are all graphical. They are also moving away from inittab as you have already seen.

---

### Post by koenn on 2008-07-29
```
sudo telinit 3
``` should get you to run leve 3, but you won't see much because, indeed, all runlevels are identical (except 1 and 6)

you could
Ctrl+Alt + F1  => gets you to a console
log in, 
tell the computer to reboot
eg 
```

sudo telinit 6
# or
sudo shutdown -r now

```

---

### Post by Vivaldi Gloria on 2008-07-29
> **Coldmiser487 said:**
> Anyone have any ideas for me?
I appreciate any and all comments

Here's a nice intro to debian runlevels:

[http://www.debian-administration.org/articles/212](http://www.debian-administration.org/articles/212)

---

### Post by Vivaldi Gloria on 2008-07-29
> **Titan8990 said:**
> In debian run levels 2-6 are all graphical. 

This is wrong. Read 

[http://www.debian-administration.org/articles/212](http://www.debian-administration.org/articles/212)

---

### Post by Vivaldi Gloria on 2008-07-29
> **Coldmiser487 said:**
>  I thought it was in /etc/inittab but there isn't one in Hardy.

Now the main folder to start/stop things is /etc/event.d. The init deamon looks only in this folder. All runlevels are called from rc? files in /etc/event.d.

---

### Post by Coldmiser487 on 2008-07-29
> **koenn said:**
> 
you could
Ctrl+Alt + F1  => gets you to a console
log in, 
tell the computer to reboot
eg 


I thought about doing this too, unfortunately everytime I do this my screen (HP laptop) gives me a vertical line pattern that resembles a circus tent, making TTY1 - 6 completely unusable

---

### Post by koenn on 2008-07-29
OK, here's another way. 

look in /etc/rc2.d for S30gdm, and rename it to K30gdm
thus is the GUI login program for gnome; it also starts your X session. the renaming stops that from happening. 

Reboot; you'll be in a console
now, either shutdown to see what happens, or

run /etc/init.d/gdm start
this will start your gnome session. Now shutdown again. you'll return to the console and hopefully see the shutdown sequence as it would be when you terminate a normal gui session.

The one thing that might get in the way is usplash, the "userfriendly" boot/shutdown screens that hide useful information from the user. 
I'm not sure how to disable those, but probably renaming the usplash script in /etc/rc2.d or /etc/init.d might do the trick.

you'll need to be a little bit CLI savvy to undo all your changes again (finding files, editing them).

---

### Post by Coldmiser487 on 2008-07-29
**UPDATE**

> **koenn said:**
> OK, here's another way. 

look in /etc/rc2.d for S30gdm, and rename it to K30gdm
thus is the GUI login program for gnome; it also starts your X session. the renaming stops that from happening. 

Reboot; you'll be in a console
now, either shutdown to see what happens


OK, I was able to follow these instructions by renaming S30gdm and this worked like a charm (no graphics mode was used on shutdown) however, my system rebooted without issue so I'm assuming now that the hanging has something to do with X

I rebooted went back in and got to my prompt and typed 'startx' to start the GUI and everything went fine, then when I tried to exit from X it locked up.

OK, now I'm SURE it has something to do with X.

Do any of you guru's out there know of which logs are kept by X to see what is causing the lockups when I'm exiting the GUI?





> **Vivaldi Gloria said:**
> Here's a nice intro to debian runlevels:

[http://www.debian-administration.org/articles/212](http://www.debian-administration.org/articles/212)
That is a GREAT article, thanks for the resource.

---

### Post by bodhi.zazen on 2008-07-29
Ubuntu is transitioning to upstart.

[http://www.linux.com/feature/125977](http://www.linux.com/feature/125977)

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

