---
title: "How to reset panels to system default w/ terminal command?"
date: 2008-11-16
forum: General Help
---

### Post by shapiror06 on 2008-11-16
So, I uninstalled the netbook remix from my EEE PC using this command:

> sudo apt-get --purge remove ume-launcher

So, now the desktop is completely blank and i can't get to anything.  I created a launcher on the desktop to open the terminal.  So, is there a command I can type into terminal to reset the panels to system default?  Or a command to open a particular tool where I can do this?

---

### Post by wjp.reg on 2008-11-16
So could you simply reinstall that which you removed?

---

### Post by prshah on 2008-11-16
> **shapiror06 said:**
>  So, is there a command I can type into terminal to reset the panels to system default?  Or a command to open a particular tool where I can do this?

Press Ctrl+Alt+F1 to gain access to a virtual terminal. Login, and give the command ```
sudo /etc/init.d/gdm restart
``` Wait for "[OK]", then switch back with Ctrl+Alt+F7 (in some cases it can be F9 or F10)

If you get errors, or it doesn't work, post back for further steps.

---

### Post by shapiror06 on 2008-11-16
> **prshah said:**
> Press Ctrl+Alt+F1 to gain access to a virtual terminal. Login, and give the command ```
sudo /etc/init.d/gdm restart
``` Wait for "[OK]", then switch back with Ctrl+Alt+F7 (in some cases it can be F9 or F10)

If you get errors, or it doesn't work, post back for further steps.

That didn't seem to work.  Maybe there's a different way to go about what I'm trying to achieve.  I installed Ubuntu EEE, and I didn't like the Netbook Remix "home screen" so-to-speak.  So I uninstalled ume-launcher, now I just have a blank desktop, and there's no "Applications" or "Places" or "System" drop down menus at the top of the screen.  It doesn't show a shortcut to the hdd, or /home on the desktop either.

Basically, I installed Ubuntu EEE because it has all the drivers for my EEE preinstalled and everything's functional.  I just wat the desktop to look like a normal install of Ubuntu, with the standard desktop.

Thanks for all your help!

---

