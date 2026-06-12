---
title: "Gateway M210 Widescreen MAJOR SCREWUP :(:(:("
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by wreckingcru on 2005-04-19
I have a Gateway M210 with a 14.1 widescreen display. After googling enough, I figured out how to get the max 1280x768 resolution and I was very happy.

I downloaded and ran 855resolution as '855 resolution 5c 1280 768' ...and after a gnome restart (Ctrl_Alt_F1 -> sudo /etc/init.d/gdm restart) ....the resolution worked.

Then I added an executable script called '855resol' (which contained the above line for 855resolution) into the init.d folder and ran the command (i forget, rc something) to add it to the startup menu.

Unfortunately, the resolution did not auto-1280x768 at startup - I would have to manually run the script and restart gdm to get it to work.

I tried messing around with the options , and went into preferences->sessions and went to startup programs (which was empty) and added my 855resol script to that list, figuring that might do it.

Err, BIG F*** UP !!!
Now when I startup, I login, and the screen where all the modules are loading just hangs....and I have NO CLUE how to fix that....I'm certain it's that program I added at startup (since that needed to be run as root), and is hanging up my login procedure.


How can I fix that problem of hanging logon screen? I'll worry about the resolution later.

PK.

---

### Post by speedman on 2005-04-19
Try selecting the failsafe gnome option from the sessions option at the GDM login screen.  That might get you into Gnome and allow you to remove the startup entry you made for your regular Gnome session.

If you can't get in that way try this from a console:

<ctrl> <alt> <f2> at the GDM login screen, log in with your username and issue this command:

rm -rf .ICE* .gconf* .gnome*

<ctrl> <alt> <f7> will return you to GDM where you can try logging in to a normal Gnome session, which you will have to reset your preferences for after deleting the files noted above.

With regards to running your script on boot ... put it in /etc/init.d/ and create the following symlink:

sudo ln -s /etc/init.d/your_script_name /etc/rc2.d/S12your_script_name

HTH


Regards,

SM

---

