---
title: "Laptop TV-OUT/Mythtv"
date: 2008-09-08
forum: Hardware
---

### Post by myth01 on 2008-09-08
I've searched the internet but cannot find a solution...

I'm trying to set up an HP NC6000 Laptop running Xubuntu as a frontend for Mythtv (its my only hardware with tv-out and Im aiming for a $0 setup).  Setting everything up has been a breeze (mostly) until I connected it to my TV.  After installing the ATI drivers, the TV-out works fine...

 ...until I close the laptop lid and the lcd AND tv-out switch off.

Obviously I want to be able to close the laptop and slip it under the tv.  

So how can I set it up to keep running the TV-out after the laptop lid has been closed?

I'm new to Linux (converted 2 weeks ago) so I apologise if the solution is very simple.

---

### Post by .nedberg on 2008-09-08
You should be able to install gnome-power-manager and use that. In the preferences you can set the laptop to "Do nothing" when you close the lid.

---

### Post by myth01 on 2008-09-08
Cheers .nedberg, I'll give that a go.  I assume I can get it via Synaptic?  It wont be a problem being 'gnome' will it, with Xubuntu running XFCE?

---

### Post by myth01 on 2008-09-08
OK, so went to Synaptic and it appears gnome power manager is already installed.  So next question....  how do you open it?

---

### Post by .nedberg on 2008-09-08
Alt+F2, gnome-power-manager

or in a console
```

gnome-power-manager

```

Gnome-apps are no problem in XFCE (or KDE-apps for that matter, though they need a bit more libraries).

---

### Post by myth01 on 2008-09-08
Argh!  Thank you for your quick reply .nedberg but nothing happens?!

---

### Post by .nedberg on 2008-09-08
One moment... I need to get my Xubuntu laptop up and running...

---

### Post by myth01 on 2008-09-08
Cheers!  Standing by...

---

### Post by .nedberg on 2008-09-08
AAArrrgghhh

Forgot I had wiped Xubuntu and installed Ubuntulite on it...

Anyway, on Ubuntulite I could install gnome-power-manager and run it with Alt+F2 or from a terminal. It shows as a battery meter in the upper right corner. Right-clicking on this pops up a menu with an option called Preferences.

I am installing Xubuntu-desktop right now. Try the suggestion above and tell me if it works.

---

### Post by myth01 on 2008-09-08
tried it via terminal and alt+f2, i did notice that the network icon (the 2 little computers) did jump to the left and straight back again, as if something had tried to start...strange...but still no manager:(

---

### Post by .nedberg on 2008-09-08
As we wait for my (slow and old) computer to install Xubuntu-desktop you could try
```

gnome-power-manager --no-daemon

```
in a terminal and see if you get an error message

---

### Post by myth01 on 2008-09-08
This was the result:

** (gnome-power-manager:6498): WARNING **: DBUS error: Could not get owner of name 'org.gnome.ScreenSaver': no such name
** (gnome-power-manager:6498): DEBUG: proxy is NULL, maybe the daemon responsible for org.gnome.ScreenSaver is not running?
*** ERROR ***
[main] gpm-main.c:255 (19:46:31):	 Power Manager is already running in this session.
Saving to syslog: Power Manager is already running in this session.matt@HPLaptop:~$

---

### Post by myth01 on 2008-09-08
obviously without the :) I don't know how to quote code yet...

---

### Post by .nedberg on 2008-09-08
> **myth01 said:**
> obviously without the :) I don't know how to quote code yet...

What? No smileys in the error? We need more smileys in the errors!:popcorn: You can tick the option "Disable smileys in text" below the "Submit" button, but no problem. I _hope_ I found a solution:

It actually says that gnome-power-manager is running. It is probably configured to hide when on AC.

You have two options:
Unplug and see is the icon shows up, then do as I told you earlier
or
run```
gnome-power-preferences
```

---

### Post by myth01 on 2008-09-08
Cheers .nedberg, the -preferences worked (I also found the notification area icon settings ;) )  Next step, I'll test it with the TV and see what happens....

---

### Post by myth01 on 2008-09-08
You the man .nedberg.  You the man.  Works like a charm.  I knew it would be something simple, and that it would through up another problem in the course of fixing it, I've come to realise thats part of the charm of Linux.

You have yourself a good evening :)

---

