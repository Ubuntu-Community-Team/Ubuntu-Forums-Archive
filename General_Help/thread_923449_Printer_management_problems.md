---
title: "Printer management problems"
date: 2008-09-18
forum: General Help
---

### Post by M4rotku on 2008-09-18
Hello all,

Last night I accidentally hit the "Print" button repetitively thinking that it was the save button.  I was very groggy and printing a paper for class the next day.  Now whenever I load paper into my printer, it tries to resume printing these 5 or so copies that I issued.  I tried to go into
Sytem > Administration > Printing, but when I clicked on it, the mouse changed to "busy" for a few seconds, and then nothing happened.

How can I get into Printing to cancel these tasks? or, if there is an easier way, how would I go about doing that?

Much thanks,
M4rotku

---

### Post by whizbaby on 2008-09-18
Try doing (from console)
```
sudo cancel -a printer_name
```
you can also put 'localhost:631' in your favourite browsers adress bar and go to 'jobs' and cancel all.

---

### Post by M4rotku on 2008-09-18
Thanks,

that worked fine for canceling the jobs.

However, I am still a bit worried about me not being able to access the
System > Administration > Printing

Does anyone have a solution for this?

Much thanks,
M4rotku

---

### Post by whizbaby on 2008-09-18
This should not be an issue normally, but are you in the lpadmin group?
Type
```
groups
```
in a terminal window and look if 'lpadmin' is there.
By the way, are you on gnome?

---

### Post by M4rotku on 2008-09-18
I am in the group and I am using gnome.  It's not so much an issue now that I have that one page, but I am still annoyed at not being able to access part of my system.

---

### Post by plucky on 2008-09-19
Open a terminal and input ```
/usr/bin/system-config-printer
``` and see if there are any error messages.This should open the "printing" GUI.

If nothing shows,then check the permission on that file ```
cd /usr/bin
ls -l system-config-printer
```

Mine looks like this > -rwxr-xr-x 1 root root 78 2008-04-21 16:44 system-config-printer


Good Luck

---

### Post by M4rotku on 2008-09-19
This was the response, it seems to have something to do with the fact that I recently installed Glade:

> $ /usr/bin/system-config-printer
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 29, in <module>
    import gtk.glade
ImportError: No module named gtk.glade
$

---

### Post by M4rotku on 2008-09-22
anyone?

---

### Post by plucky on 2008-09-23
> **M4rotku said:**
> This was the response, it seems to have something to do with the fact that I recently installed Glade:

Have you tried removing Glade?

---

### Post by M4rotku on 2008-09-23
I just removed glade and got the same response:

> joey@joey-laptop:~$ /usr/bin/system-config-printer
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 29, in <module>
    import gtk.glade
ImportError: No module named gtk.glade


---

### Post by Sef on 2008-09-23
How did you remove glade?  You may not have removed the configuration files.

---

### Post by M4rotku on 2008-09-24
I went into synaptic and chose to completely remove, so the config files are gone.

---

