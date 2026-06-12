---
title: "NVIDIA Geoforce 7300"
date: 2008-06-02
forum: Hardware
---

### Post by DougAlder on 2008-06-02
I had this working in 8.04 for dual monitors then today when I logged in my menu bar was missing- I was able to get Ubuntu to reboot and when the start up menu came up I chose to go into repair mode (wish now I had just let it reboot and see if it was just a temporary glitch) I hit repair xwindows - that was my second mistake and when I completed the boot I'm no longer able to use the second monitor. I was able to get into the NVIDIA configuration window however when I try and enable the second monitor I get an error message when I go to sabe stating that NVIDIA can not remove backup.conf from /etc/X11/ - I seem to be stuck here - how can I restore this?

---

### Post by Phonan on 2008-06-02
Just to make sure, are you running as root?

---

### Post by DougAlder on 2008-06-03
> **Phonan said:**
> Just to make sure, are you running as root?
I'm running Heron inside XP so I can't log in as root when I first boot but if I open a terminal window I can su to root. Doing that I was able to delete the backup that NVIDIA couldn't (I'm guessing now that wasn't a good idea) but now when I run NVIDIA's congig editor (sytem/ --> administration --> NVIDIA X server configuration) and try to save it tells me it can't create a new backup file. So I'm lost as to what to do - how can I run that program as root from a terminal window? As you can tell I'm a newbie to Linux

---

### Post by overdrank on 2008-06-03
> **DougAlder said:**
> I'm running Heron inside XP so I can't log in as root when I first boot but if I open a terminal window I can su to root. Doing that I was able to delete the backup that NVIDIA couldn't (I'm guessing now that wasn't a good idea) but now when I run NVIDIA's congig editor (sytem/ --> administration --> NVIDIA X server configuration) and try to save it tells me it can't create a new backup file. So I'm lost as to what to do - how can I run that program as root from a terminal window? As you can tell I'm a newbie to Linux

HI and by inside windows you mean you are running ubuntu as a virtual machine in XP? With what virtual software?

---

### Post by DougAlder on 2008-06-03
> **overdrank said:**
> HI and by inside windows you mean you are running ubuntu as a virtual machine in XP? With what virtual software?

I used Wubi to install it so I'm not certain exactly what that does. I can see some of the Ubuntu files while in XP (C:/ubuntu) and when in Ubuntu I can view all the files in /host

---

### Post by overdrank on 2008-06-03
> **DougAlder said:**
> I used Wubi to install it so I'm not certain exactly what that does. I can see some of the Ubuntu files while in XP (C:/ubuntu) and when in Ubuntu I can view all the files in /host

Ok have you verified that the restricted driver is still enable under system, administration, drivers manager. If you use xfix I may configure your system to use the vesa driver instead of th nvidia driver.

---

### Post by DougAlder on 2008-06-03
> **overdrank said:**
> Ok have you verified that the restricted driver is still enable under system, administration, drivers manager. If you use xfix I may configure your system to use the vesa driver instead of th nvidia driver.

I already did that, then I uninstalled the NVIDIA drivers and reinstalled them. I think what I need to do is run the NVIDIA configuration editor as root but I don't know how to do that as I can only get to root via terminal after logging in to the desktop as a non-root user.

---

### Post by overdrank on 2008-06-03
> **DougAlder said:**
> I already did that, then I uninstalled the NVIDIA drivers and reinstalled them. I think what I need to do is run the NVIDIA configuration editor as root but I don't know how to do that as I can only get to root via terminal after logging in to the desktop as a non-root user.

HI and have you tried ```
gksu nvidia-settings
```

---

### Post by Phonan on 2008-06-03
Yes that's what you need to run- for some reason the menu only runs nvidia-settings, not as root.

---

### Post by DougAlder on 2008-06-03
> **overdrank said:**
> HI and have you tried ```
gksu nvidia-settings
```

Thank You! Thank You! Thank You! That worked like a charm - now to go off and find out what gksu is ;) I've been using DOS and Windows since '92 and this is my first foray into Linux. I'm having fun and I am really impressed with the help newbies like me get in forums like this. Good on all of you.

---

### Post by overdrank on 2008-06-03
> **DougAlder said:**
> Thank You! Thank You! Thank You! That worked like a charm - now to go off and find out what gksu is ;) I've been using DOS and Windows since '92 and this is my first foray into Linux. I'm having fun and I am really impressed with the help newbies like me get in forums like this. Good on all of you.

Great and it is just to run sudo graphically 
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Phonan on 2008-06-03
> **DougAlder said:**
> Thank You! Thank You! Thank You! That worked like a charm - now to go off and find out what gksu is ;) I've been using DOS and Windows since '92 and this is my first foray into Linux. I'm having fun and I am really impressed with the help newbies like me get in forums like this. Good on all of you.

Great that it works! And one more thing, if you want to be able to get nvidia-settings to work straight from a simple menu click, go to Preferences-> Main Menu. Then find the "Nvidia X Settings" menu item, right-click, and select "Properties." Then, you'll see several things, but most important is the one labeled "Command." Here, change whatever you have by adding "gksu" in front of it (no quotes.) Now when you launch your Nvidia X Settings it'll ask for your password and should work easily.

---

