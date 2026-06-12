---
title: "cant get a terminal"
date: 2008-08-13
forum: General Help
---

### Post by madtom1999 on 2008-08-13
I've just installed Xubuntu on an old machine and it seems to run OK but if I do Alt F2 or click on terminal in the menu the screen flashes and eventually pops up with a new login screen, loosing all the old session as far as I can tell.
Any clues anyone?

---

### Post by plucky on 2008-08-14
> **madtom1999 said:**
> I've just installed Xubuntu on an old machine and it seems to run OK but if I do Alt F2 or click on terminal in the menu the screen flashes and eventually pops up with a new login screen, loosing all the old session as far as I can tell.
Any clues anyone?

What version of Xubuntu are you running?

There was a problem a while back with Xubuntu terminal couldn't handle a default depth of 24 but could handle 16.Something to do with the graphic module.The problem is that Hardy has changed the way the graphic card is installed and the user cannot now edit the xorg.conf file to change the default depth.

You could use xterm instead,by right clicking on the desktop and create a launcher with the command "xterm", or install gnome-terminal which will work in Xubuntu ```
sudo apt-get gnome-terminal
```

Good Luck

---

### Post by Kevbert on 2008-08-14
Terminal is probably already installed.  To get a terminal icon on your taskbar do the following:
1) Right-click on top panel and select New Item.
2) Make sure Launcher is selected then click on Add.
3) Enter name Terminal and description (whatever you like).
4) Select Icon terminal by selecting funny symbol and selecting it from the list.
5) In command line enter /usr/bin/xfce4-terminal
6) Select Close.
You should now have a terminal icon in the top righthand corner of the taskbar which will launch terminal when selected.

---

### Post by sayakb on 2008-08-14
Press Alt+F2 and type in:
```
xterm
```

---

### Post by madtom1999 on 2008-08-14
Thanks for the help everyone.
To reiterate:
Latest Xubuntu fully updated and upgraded.
Running 'terminal' from the menu or ALT-F2 crashed the current session
creating a launcher for /usr/bin/xfce4-terminal and clicking it also crashed the current session.
I've installed gnome-terminal and now I can run 'terminal' from the menu and ALT-F2 now works as expected - unless I run xfce4-terminal which crashes the session.
How can I report a bug for xfce4-terminal which is either the problem or part of the problem as suggested by plucky?

---

### Post by Kevbert on 2008-08-14
You need to register with [[COLOR="Red"]Launchpad[/COLOR]]("https://bugs.launchpad.net/").  They will require PC specs, Xubuntu version and what you tried to get the problem sorted.
Funnily enough it looks like Launchpad is a bit busy at the moment as I'm getting a timout on the website.  This may be due to the new alpha release of Intrepid!!!

---

### Post by sayakb on 2008-08-14
Afaik, xterm should work.. Did you try executing xterm? Report bugs to [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by madtom1999 on 2008-08-14
I didnt try xterm as ALT-F2 didnt work and I'm lazy*.
It seems to work now (after loading gnome-terminal).
Next time I load a machine with the same problem I'll try it and report back


* well not really - I'm trying to put out as many old pasttheirsellbydateifyouputwindowsonthem machines back into the real world and I'd rather have clean installs for this if possible, or at least fixes that work across all users as installing gnome-term. Making an icon on every users desktop is not quite as nice as having the menu work properly.

---

### Post by madtom1999 on 2008-08-14
I think its been reported as a bug:
[https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849]("https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849")

---

