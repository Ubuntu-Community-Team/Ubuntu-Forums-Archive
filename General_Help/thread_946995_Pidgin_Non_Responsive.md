---
title: "Pidgin Non Responsive"
date: 2008-10-13
forum: General Help
---

### Post by RandomIP on 2008-10-13
Today when i tried to start pidgin it was non responsive, it started a process to run pidin, then disappeared. When I ran pidgin in the terminal i got.
```
jordanr@RyanLaptopUbuntu:~$ pidgin
/home/jordanr/.themes/Clearlooks_blackblue/gtk-2.0/gtkrc:53: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.

```
I recently put emerald --replace, on startup could this be the problem? and how can i fix it without losing my windows frames.

Thanks

---

### Post by pytheas22 on 2008-10-13
Does it return you back to the command prompt after you type that?  If not, pidgin is probably still running in some form; you can check by typing:
```

ps -e | grep pidgin
```

If it returns anything besides a blank line, then pidgin is running.

I don't think that the message represents a fatal error--it's just a generic gtk message complaining about not being able to draw the window border or something the way that it thinks it should; it should not be causing pidgin to fail.

Also, did you try disabling your emerald --replace command, logging in again and seeing if that makes a difference?

---

### Post by RandomIP on 2008-10-13
I got ```

jordanr@RyanLaptopUbuntu:~$ ps -e | grep pidgin
 5724 ?        00:00:19 pidgin
jordanr@RyanLaptopUbuntu:~$ 

```

---

### Post by pytheas22 on 2008-10-13
Then pidgin is running somewhere, which means that it seems to be starting.  Do you not see any kind of window pop up at all?  What happens if you first kill all pidgin processes by typing:
```

sudo killall -9 pidgin
sudo kill -9 $(ps -e | grep pidgin)
```

and then try starting pidgin again?

Also, it may help to simply reinstall pidgin, by typing:
```

sudo apt-get remove --purge pidgin
sudo apt-get install pidgin
```

---

### Post by RandomIP on 2008-10-13
I uninstalled then reinstalled Pidgin,restarted Ubuntu, and restarted pidgin, it says its starting then again nothing happens.

---

### Post by pytheas22 on 2008-10-13
Do you have problems starting any other applications, or is it just pidgin?

---

### Post by RandomIP on 2008-10-14
Its only happening for pidgin, everything else seems to work fine, i tried firefox gimp and open office, their all working fine.

---

### Post by bigbrovar on 2008-10-14
try changing your theme .. mabe to the default theme

---

### Post by RandomIP on 2008-10-14
Changing theme dosent do a thing. Remove emerald --replace from startup session, also didn't do anything. So anyway I'm lost

---

### Post by bigbrovar on 2008-10-14
go to synaptic and search for this **gtk-qt-engine**  if you have it installed then remove it, and reboot your system tell me if it works

---

### Post by RandomIP on 2008-10-14
gtk-qt-engine is not installed, neither was gtk2-engine-gtk-qt nor gtk-qt-engine-kde4

---

### Post by bigbrovar on 2008-10-14
wow am running out of options now :) ok ```
sudo apt-get remove --purge pidgin
``` then ```
sudo apt-get autoremove
``` now ```
rm -r .purple/
``` then reinstall pidgin

---

### Post by RandomIP on 2008-10-14
Followed all that, still wont start...It worked two day's ago...

---

### Post by bigbrovar on 2008-10-14
the last time i experienced something like this i it was caused by a plugin i installed called music tracker .. do you have something like that installed

---

### Post by orawax on 2008-11-15
> **bigbrovar said:**
> the last time i experienced something like this i it was caused by a plugin i installed called music tracker 

I'm not sure but it seems music tracker is the problem. Pidgin hangs few seconds after enabling the plugin, but seems to work when it's disabled.

---

### Post by pytheas22 on 2008-11-15
> In a society that has abolished
every kind of adventure
the only adventure that remains
is to abolish the society. 

Vive mai 68!

(Sorry to be off-topic.)  RandomIP: did you ever solve this problem?

---

