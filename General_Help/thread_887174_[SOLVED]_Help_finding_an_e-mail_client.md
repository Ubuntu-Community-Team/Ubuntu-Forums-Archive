---
title: "[SOLVED] Help finding an e-mail client"
date: 2008-08-11
forum: General Help
---

### Post by gjr5017 on 2008-08-11
Is there an e-mail client that I can minimize to the notification area and have it running 24/7? I did this in windows with Thunderbird with the minimize-to-tray extension but it only works for windows. I ask this because I just like to see that I have a new e-mail in the notification area instead of running my e-mail client every time because I often forget about it until I see the notification. Thanks in advanced.

Side Note: I'd like it to be a Gnome program so I don't need to have the KDE libraries running 24/7 along with the gnome ones.

---

### Post by estyles on 2008-08-11
I usually have Evolution on my second workspace so it's out of mind - it pops up a notification in the tray when I get a new email.  You could probably even set it to start up on an out-of-the-way workspace on startup, although I don't personally know how to do that.  I'm guessing that isn't what you want - since you say you have Gnome running, I'm assuming that Evolution was installed by default, and you don't like it.

---

### Post by gjr5017 on 2008-08-11
It's not a bad program but I just want something that I can have minimize to the notification area like rhthymbox, pidgin, deluge, etc.

---

### Post by damis648 on 2008-08-11
I do believe Evolution will do this if you select File>Close Window once you start it, as opposed to File>Quit. This is an educated guess, but it seems likely that is what it would do.

---

### Post by x1a4 on 2008-08-11
Hi,
Claws Mail using the 'Notification' plugin.

---

### Post by gjr5017 on 2008-08-11
> **x1a4 said:**
> Hi,
Claws Mail using the 'Notification' plugin.

I've got this up and running but the plugin is the trayicon plugin. Thanks :)

---

### Post by x1a4 on 2008-08-12
> **gjr5017 said:**
> I've got this up and running but the plugin is the trayicon plugin. Thanks :)

The Trayicon plugin is nice but the Notification plugin is nicer.  Trayicon only puts Claws Mail in the tray, but the Notification plugin also shows if you have unread mail, notifies you of new mail, shows if you're on/off line, and can do it in a variety of ways.  I highly recommend it.  

To install it, open CLaws Mail, Click Configuration -> Plugins.  Click the 'Load' button, open the directory /usr/lib/claws-mail/plugins and load notification_plugin.so

To configure it go to Configuration -> Preferences -> Plugins -> Notification.  If it's not on your system, download it [here]("http://www.claws-mail.org/plugins.php") and place in /usr/lib/claws-mail/plugins then load it.

---

### Post by gjr5017 on 2008-08-20
I wasn't feeling claws mail at all...it seemed old and outdated but I found a way around it. I had all tray installed but I just changed the launcher for evolution from 'evolution' to 'alltray "evolution"' and it starts evolution in the notification area. Thanks alot though.

---

