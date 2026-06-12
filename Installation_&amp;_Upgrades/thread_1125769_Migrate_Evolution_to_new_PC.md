---
title: "Migrate Evolution to new PC"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by BananaFish on 2009-04-14
Hi All,

I am currently moving my old Home folder to a new PC, trying to move my Evolution data at the moment. Found this on the Evolution website FAQs:

> How can I transfer all my Evolution data from an old home directory to a new home directory? 
...
5. If for some reason you cannot dump your Evolution settings in GConf (e.g. no access to the old system), copying the data (cp -R oldComputer:$OLDHOME/.gconf/apps/evolution newComputer:$NEWHOME/.gconf/apps/evolution) will do as well, **but make sure that this is done while Gnome and the GConf daemon are not running**, see below.
...

Not sure how I leave Gnome (or get back) though.........?

Can anyone help.........?

I found this:

> sudo /etc/init.d/gdm start
sudo /etc/init.d/gdm stop

Stopping GDM causes GNOME and all graphical applications to quit, starting it will take you to the login screen. 

I'm guessing (but not brave enough to try) that if I do this in a terminal window, that all 'desktop/graphicUI/all that I use & understand' will quit and perhaps I'll be left with only a command prompt....?
is that right?

Thanks for any help,

JW

---

### Post by Cheesehead on 2009-04-14
Easier way is to log out, but do not shutdown.
At the login screen, press CTRL+ALT+F1
Login normally to the text terminal, run the copy command, and use the 'logout' to log out.
Press CTRL+ALT+F7 to return to the graphical login screen. Login and try the new evolution.

---

### Post by BananaFish on 2009-04-15
Thanks very much Cheesehead, I shall give that a go!

---

### Post by fballem on 2009-04-15
A couple of questions, if I may:

1. If you are moving to a new PC, have you thought about exactly what you wish to preserve? The reason that I'm asking is that if I'm moving to a new PC, then I want to preserve data, but not necessarily full configuration information.

2. If the object is to preserve your data, then have you considered the backup option in Evolution? 
- If you select File > Backup Settings, then you can create a backup file that contains all of your mail, contacts, calendar, and e-mail account settings.
- Word of warning - once you've provided the name of the backup file and selected OK, a screen pops up to confirm that you want to close Evolution. Once you click 'Yes', it can take a while for the backup to start - be patient. When done, copy the backup file to the new machine after you've done a basic install of ubuntu.
- When you install on the new machine and start Evolution for the first time, one of the options will allow you to restore from a backup. Select the option, then select the file that you made previously. Everything will be imported with the exception of the passwords for your mail servers. The passwords will be asked for when you do your first send/receive and will be preserved if the appropriate box is checked.
- I have done this many times (I tend to blow my machine up a lot, necessitating re-installation) and it has worked very reliably.

Just an alternative approach.

---

### Post by BananaFish on 2009-04-17
> **fballem said:**
> 
If the object is to preserve your data, then have you considered the backup option in Evolution? 



fballem, thanks very much I might give that a go instead, I hadn't noticed the Evolution backup option.

I've already copied the .evolution folder over, and got my old emails only, I guess I could put it back in the old PC and run the backup.

Odd that Evolution website doesn't mention that in the FAQs...?

Thanks again.

---

