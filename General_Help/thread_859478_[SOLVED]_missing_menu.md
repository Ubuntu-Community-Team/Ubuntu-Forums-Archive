---
title: "[SOLVED] missing menu"
date: 2008-07-14
forum: General Help
---

### Post by ghonz on 2008-07-14
Help I've got a missing menu.
I'm running Hardy Heron on a HP Tx1000 series, and my menu bar has vanished.
I used the laptop on sunday it was there and working, since restarting the menu has vanished.

Anyone got any advice?

---

### Post by tamoneya on 2008-07-14
try to restart gnome-panel by hitting alt-f2 and then typing:```
gnome-panel
```

---

### Post by ghonz on 2008-07-14
I've tried hitting alt-f2 and nothing happens
:confused:


> **tamoneya said:**
> try to restart gnome-panel by hitting alt-f2 and then typing:```
gnome-panel
```

---

### Post by tamoneya on 2008-07-14
can you get any terminals running.  If not reboot the computer and hit escape at the grub boot prompt.  This will show you a list of boot options.  Select the "recovery mode" (cant remember exact wording).  This will bring you to a Command line interface.  There you should type:```
sudo dpkg-reconfigure ubuntu-desktop
```
This is assuming you use ubuntu not kubuntu or xubuntu.

---

### Post by ghonz on 2008-07-14
I don't actually know any other way of getting to a terminal apart from through the menu or alt-f2 :) (i'm still a newb)

I tried recovery mode, didnt get a command line but did come to a page to dpkg anything broken, but that didn't fix anything,

Still no menu.

---

### Post by coffeecat on 2008-07-14
Try this. Boot into your broken desktop. Press Ctrl-Alt-F1. This will give you what's called a virtual console. You have to log in again. Now type in the command that tamoneya gave you. Copy it **exactly**. Don't try anything else. Now type in:

```
sudo reboot
```(In case anyone is going to complain that he should go back to the desktop and restart the X-server, I think rebooting is more straightforward.)

Let the system reboot, log in and tell us what the desktop is like now.

---

### Post by jocko on 2008-07-14
> **ghonz said:**
> I don't actually know any other way of getting to a terminal apart from through the menu or alt-f2 :) (i'm still a newb)

I tried recovery mode, didnt get a command line but did come to a page to dpkg anything broken, but that didn't fix anything,

Still no menu.

Not sure what you mean here, but in recovery mode in hardy you get to choose between a few different options, of which one is to get a command line as root (don't remember exactly what it says, but I think it's the last option). In gutsy and earlier there were no choices, it just went straight to the root terminal.
But another way to get a command line when you are logged in to gnome is to press Ctrl+Alt+F1 (or F2, 3,4,5 or 6). That should get you to a terminal, and Ctrl+Alt+F7 gets you back to gnome.

---

### Post by ghonz on 2008-07-14
Ok I did that, restarted and no change :(

any other advice?

> **coffeecat said:**
> 

Let the system reboot, log in and tell us what the desktop is like now.

---

### Post by fooman on 2008-07-14
> **ghonz said:**
> I don't actually know any other way of getting to a terminal apart from through the menu or alt-f2 :) (i'm still a newb)


heres another way...boot up ubuntu to your desktop.  
hit ctrl-alt-f1 to get to a different console.  
log in with your user name and password.
type the following:

```
sudo apt-get install nautilus-open-terminal
```

after it installs, hit ctrl-alt-f7 to get back to your original console.
now you can right click on the desktop and choose "open in terminal".

once the terminal is open, you should be able to get your panel back with:

```
gnome-panel &
```

---

### Post by ghonz on 2008-07-14
Ok after i return to the desktop and right click i don't get an option to open in terminal

> **fooman said:**
> 
now you can right click on the desktop and choose "open in terminal".

once the terminal is open...

---

### Post by fooman on 2008-07-14
sorry,  you may have to reboot after the install.

---

### Post by mc4man on 2008-07-14
If your just missing the menu bar (applications, places, system) and still have the top panel then all you need to do is delete 2 files, applications.menu and settings.menu.
First just try r. clicking on the panel -> add to panel -> menu bar. In all likelihood you won't be able to use it, but try.
The path to the files you may need to delete is /home/<your user name>/.config/menus
If you can't browse there (no working places in new menu bar then from terminal ```
gksudo nautilus
```
that will open a root file browser and go file system -> home -> <your user name> -> on the view tab enable 'show hidden files' -> .config -> menus and delete the 2 mentioned files.
do a Ctrl+Alt+backspace and see

---

### Post by ghonz on 2008-07-15
> **fooman said:**
> sorry,  you may have to reboot after the install.

Wuhoo!!
Its back, thank you :)

---

