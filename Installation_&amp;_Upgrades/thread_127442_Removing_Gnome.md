---
title: "Removing Gnome"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by dickohead on 2006-02-08
So... I originally installed 5.04, then upgraded to 5.10, at this stage I hadn't mastered apt-get so was using VNC for tasks, but recently Gnome/GDM/X has started to play up and will lock up my server.

I have tried removing ubuntu-desktop, gnome-desktop-environment, gnome, gnome-base etc etc etc 'sudo apt-get remove x-package' just won't work. I'm assuming it's because I have upgraded from a 5.04 desktop install.

What do I need to tell apt-get to remove so that I am left with the server installation... ie:

My server uses SSH/Apache/Ruby-on-rails/php and samba... anything else is killable (except the GB's of data of course!).

Anyone know what I *should* be doing?

---

### Post by matthewv on 2006-02-09
You might want to try a ```
 sudo apt-get remove libx11-6
```
This will remove almost everything graphically related, including gnome (and kde).
I would take a look through the list that it the command gives, just to make sure you are not removing anything important.
The other packages that you tried to remove probably did not have the desired effect because they are meta-packages... packages that just install a stack of other packages on your system.. not specific bits of software

---

### Post by dickohead on 2006-02-09
Thanks Matt! I tried to SSH into my server from work... but I got prompted for the username and then the connection died, tried again and it was refused, perhaps my issues are not with Gnome but with SSH.... Are there any known issues with SSH causing it to lock up the system? Or maybe my server's just getting old!

When I get home I shall try and remove the packages directly from the machine (it makes me feel so dirty though... :() and let you know how I go!

Thanks!

---

