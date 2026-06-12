---
title: "Error starting the GNOME Settings Daemon - no internet connection now!"
date: 2008-07-15
forum: General Help
---

### Post by Goodson1974 on 2008-07-15
I updated Hardy a couple of days ago, and since then i've been getting the following error: -
 
 
[COLOR=black][FONT=Courier New]There was an **error** starting the **GNOME** Settings Daemon.[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]Some things, such as themes, sounds, or background settings may not work correctly.[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]The last **error** message was:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]Did not receive a reply. Possible causes include: the remote application did not send a reply,[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]the message bus security policy blocked the reply, the reply timeout expired, or the network[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]connection was broken.[/FONT][/COLOR]
 
 
It takes five to ten minutes to display this error, and when the desktop is finally usable, i cannot connect to the internet.
 
I've checked the network setup and it doesn't seem to have changed, and is displaying the correct settings.
 
I've checked through a number of threads for this error, but none seem to have lost internet access.
 
Is there anything i can do or should i reinstall?
 
Any help is appreciated.

---

### Post by nnebular22 on 2008-07-16
i got the same error message.  but thats not all thats wrong with mine.  my ati graphics card is not supported either.  but the ubuntu website says it is.  (ATI 9800 pro)

---

### Post by Viper666 on 2008-07-17
Don't have any info on your network card to help you more but i also had that error after doing an upgrade and could not resolve it by any means. 
I would suggest you save all your important stuff and do a clean install cause something obviously isn't updated properly.

---

### Post by jmjohn on 2008-10-01
Hey guys,

To fix this, I removed all some of my local configuration files.

First, back up the files that you will remove
$ cp -r .gnome ~/gnomebackup
$ cp -r .gnome2 ~/gnomebackup
$ cp -r .gnome2_private ~/gnomebackup
$ cp -r .gconf ~/gnomebackup
$ cp -r .gconfd ~/gnomebackup


Next, remove them.
$ rm -rf .gnome .gnome2 .gnome2_private .gconf .gconfd

Next, ctrl + alt + Backspace, and log back in.

If the problems gone, great.  If you like, copy the folders back until you have a recurrence, then you've found the problem.

---

### Post by UV-Ray on 2008-10-06
Your solution is brilliant, **jmjohn**! It's working! ;)

---

### Post by jmjohn on 2008-10-08
I fixed this problem for good on my computer (it popped back up!) by re-installing dbus and x11-dbus using synaptic as suggested on a bug report.

---

