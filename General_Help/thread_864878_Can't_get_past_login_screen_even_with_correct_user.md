---
title: "Can't get past login screen even with correct user/pass"
date: 2008-07-20
forum: General Help
---

### Post by Rogue Jedi X on 2008-07-20
The login screen will absolutely not let me get to my desktop. What happens is I type in my username and password, then the screen goes black, I get a glimpse of the command-line interface and then I'm back at the login screen being prompted to input my username and password again. Doing so again has the sam results. The only way I was able to get to my desktop was selecting "Failsafe Gnome" from the sessions menu on the bottom left. So, any ideas?

---

### Post by ibutho on 2008-07-20
At the login manager screen, do CTRL-ALt-F1 and login to the terminal. After that enter the command
```
sudo /etc/init.d/gdm stop
```
Wehn thats done, run the command "startx" (minus quotes) and see if you can login to GNOME. Post back any error messages.

---

### Post by Rogue Jedi X on 2008-07-20
Okay, here's my report.
I did as you suggested and stopped gdm via command line, typing startx afterwards. I got thrown into my previous GNOME session, with the only error being the message;

"User Switcher" has quit unexpectedly.
If you reload a panel object, it will automatically be added back to the panel.

It kept popping up if I clicked Reload, but went away after clicking Don't Reload. Browsing around a bit, I found nothing else to be wrong, so I tried logging out. 
I was thrown back to CLI where I started gdm again and came to the login screen. I set the session back to regular GNOME and this time, the login worked.
So, problem solved? If so, thanks! What did I fix, though?

---

### Post by ibutho on 2008-07-20
I don't know what exactly you fixed. I was trying to see if logging in via the CLI would shed more info into your problem. Anyway if everything works as it should now, then thats cool.

---

