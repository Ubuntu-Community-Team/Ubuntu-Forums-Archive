---
title: "Changed login theme now can't login"
date: 2008-09-17
forum: General Help
---

### Post by wightghost on 2008-09-17
Hello all
Last night I installed a new login theme in Ubuntu.  This morning I can't login.  It will go through the Ubuntu splash screen and then a blue background displays with the small spinning circle mouse icon but the login screen does not appear.  I'm guessing the login theme is corrupt.  
After reading through the forums I found a suggestion to boot from the live CD then mount the Ubuntu partition and change the gdm.conf file.  My main question is:  How do I mount the Ubuntu partition???
If someone could explain this in really simple terms (I'm reasonably new to all this) or can offer other suggestions I would very much appreciate it.
Thanks for your time.
Brad

---

### Post by leef on 2008-09-17
when you get stuck on the login screen do CTRL + ALT + F2 and login to the console their then do;

```

sudo cp /etc/gdm/gdm.conf /etc/gdm/gdm.conf.old
sudo nano /etc/gdm/gdm.conf

```

find the line that contains "GraphicalTheme" (use SHIFT + W to search) and change that line to;

```

GraphicalTheme=Human

```

Which should set gdm to the default theme. them reboot the machine or restart x by going back the the login screen (CTRL + ALT + F7 or F1 I forget which) and pressing CTRL + ALT + BACKSPACE.

If you really need to do this in the live cd try this in the live cd;

```

sudo mkdir /hd
sudo mount /dev/sda1 /hd
sudo cp /hd/etc/gdm/gdm.conf /hd/etc/gdm/gdm.conf.old
sudo nano /hd/etc/gdm/gdm.conf

```

---

### Post by wightghost on 2008-09-18
> **leef said:**
> when you get stuck on the login screen do CTRL + ALT + F2 and login to the console their then do;

```

sudo cp /etc/gdm/gdm.conf /etc/gdm/gdm.conf.old
sudo nano /etc/gdm/gdm.conf

```

find the line that contains "GraphicalTheme" (use SHIFT + W to search) and change that line to;

```

GraphicalTheme=Human

```

Which should set gdm to the default theme. them reboot the machine or restart x by going back the the login screen (CTRL + ALT + F7 or F1 I forget which) and pressing CTRL + ALT + BACKSPACE.

If you really need to do this in the live cd try this in the live cd;

```

sudo mkdir /hd
sudo mount /dev/sda1 /hd
sudo cp /hd/etc/gdm/gdm.conf /hd/etc/gdm/gdm.conf.old
sudo nano /hd/etc/gdm/gdm.conf

```

Thanks for your detailed reply.  Unfortunately neither of your suggestions worked:( When I tried your first idea the Graphical Theme section already had "Human" listed.  And for some reason your 2nd idea didn't work either.  Thanks for your efforts though.  Any other ideas out there???

---

### Post by leef on 2008-09-18
> **wightghost said:**
> Thanks for your detailed reply.  Unfortunately neither of your suggestions worked:( When I tried your first idea the Graphical Theme section already had "Human" listed.  And for some reason your 2nd idea didn't work either.  Thanks for your efforts though.  Any other ideas out there???

Did you install a new GDM (login) theme or did you install a GTK theme (window decoration, etc)? what changes did they suggest to the gdm.conf file? also when you booted the live cd did the partition mount correctly or did that fail. The /dev/sda1 part of that command was an example sda1 should be replaced with the device and partition that ubuntu is on in older IDE hardware this is usually /dev/hda1. If it's already set to human, I have to wonder if it's  the theme causing the issue, what does "dmesg" report when you change tty (using CTRL + ALT + F2 at the login window)

---

### Post by wightghost on 2008-09-18
Problem solved.  
Leef I tried your first suggestion again:

when you get stuck on the login screen do CTRL + ALT + F2 and login to the console their then do;

Code:

sudo cp /etc/gdm/gdm.conf /etc/gdm/gdm.conf.old
sudo nano /etc/gdm/gdm.conf

Then I found the entry GraphicalThemeRand and changed its setting to True.  My hope was that by doing this Ubuntu would randomly select a different theme to use for the login screen.  That's what happened!  I was then able to login and delete the dodgy theme and select a different one.  It's all working fine now.
Thanks very much for your help.  It's much appreciated.
Brad

---

### Post by kspringer on 2009-01-06
Yeah, I know this is an old thread but it solved a very large problem with my system.
Thanks to all!

k

---

