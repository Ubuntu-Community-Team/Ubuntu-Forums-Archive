---
title: "Screen resolution"
date: 2008-07-23
forum: General Help
---

### Post by James.H on 2008-07-23
Hey.

I've just installed Ubuntu on my desktop. However, the screen resolution isn't set. I cannot set it to 1280x1024 since it only goes up to 800's. I belive I've got to install drivers for my graphics card? It's a SIS 760, very poor. Now I have no idea how to do this, so I was wondering if someone could please help me with what command I need to do through terminal?

Thank you very much,

James.

---

### Post by tuxxy on 2008-07-23
System > Administration > hardware drivers

See if the driver is available here or from the terminal
```

jockey-gtk
```

---

### Post by James.H on 2008-07-23
Hi,

There's nothing in system > adminstration > hardware drivers. I'm not sure how to get it. What's the code for?

---

### Post by overdrank on 2008-07-23
> **James.H said:**
> Hi,

There's nothing in system > adminstration > hardware drivers. I'm not sure how to get it. What's the code for?

Hi and welcome. I believe you will not see any hardware drivers for that chipset. You may try the command ```
gksu displayconfig-gtk
``` and adjust your settings. Use the key alt, F2 and enter the command.

---

### Post by James.H on 2008-07-23
Hi,

Thank you for the welcome :) Unfortunately, that command didn't fix the issue. I did however find [http://www.winischhofer.eu/linuxsispart4.shtml](http://www.winischhofer.eu/linuxsispart4.shtml) if its any use, but I'm not sure on how to use it. Sorry.

Thanks,

James.

---

### Post by mailtwogopal on 2008-07-23
hi james,

  i had same problem after installation but i got if fixe thru this:

System-> preferences -> Screen resolution, where it looks like in attached screenshot in which u can find resolution drop down. Select from list and change refresh rate below it. and after it asks "whether to change settings or to keep current settings". just give change settings and close. This is wat i did and is ok till today.

Good luck.

---

### Post by James.H on 2008-07-23
Hey, thanks for posting. The issue is, I cannot get the 1024x768 that you've got (But need 1280x1024 anyway). Mine just has 800x700 and low resolutions like that. My refresh rate doesn't change on any of them.

James.

---

### Post by mailtwogopal on 2008-07-25
hi,

  Make sure that your hardware driver gets installed and try again.

---

### Post by northern lights on 2008-07-25
Okay, try this:

First, let's backup your current xorg.conf```
cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```

Now, let's reconfigure the xserver:

Run ```
sudo /etc/init.d/gdm stop
``` from a terminal. You will be leaving the graphical environment, so remember the next two steps!

Press Alt+F1 to log in and execute ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart the interface with ```
sudo /etc/init.d/gdm start
```

Try to change resolution again.

In case something gets (even more) screwed, revert back with```
cp /etc/X11/xorg.backup /etc/X11/xorg.conf
```

---

