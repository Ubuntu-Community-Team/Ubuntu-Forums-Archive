---
title: "After updates, many admin tasks won't open"
date: 2008-07-22
forum: General Help
---

### Post by TransplantedCanuck on 2008-07-22
My wife installed updates a week or 2 ago (as she always does when they appear). Since then numerous problems have started happening. I'll start in order from booting.

PROBLEM ONE:
Login to Ubuntu, desktop appears, popup in the bottom right corner saying:
"The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your system administrator"

I did some googling and somebody said I should simply re-install the package. So I went to open up synaptic... I got the 'dpkg --configure -a' problem. Ok, ran the command and then it worked. Fine. Re-installed the package, and went to reboot!

PROBLEM TWO:
CLick on the little green shutdown menu man. Instead of getting the window with all the possible options, it just logs me out, then I can reboot. I'm hoping this is related to the first problem?

Log back into Ubuntu, and it still gives me the error message. I try and ignore it for now and will deal with it later. I wanted to install GNOMAD for my Creative MP3 player, I go to open up the add/remove programs program from the Applications menu, and it starts with the "starting Add/Remove..." in the taskbar, then disappears. In the system logs I don't see any sort of error (or any reaction at all). Well, wondering if perhaps theres a new kernel and its buggered, I go to start up the startup manager to change to a working kernel... I click on it, enter the password and it won't open. Again nothing in the system logs. I also checked the running processes, no sign of any of them there.

A list of System Programs that won't open:
Preferences:
- Main Menu
Administration:
- Hardware Drivers
- Hardware Testing
- Software Sources
- Startup Manager
- Update Manager

Other noticed symptoms:
- Programs that used to minimize to the tray when closed no longer do so, they just close. None of these programs can now be sent ot the tray.
- After the updates, the minimize/maximize/close buttons (dash, box, X) in all the windows were turned off, I fixed this in the "Windows" tool afterwards, but they WERE changed.


I posted this elsewhere a few weeks ago and got only this response that didn't help me:

> You may want to check if the upgrade was succesful. If you can open a terminal and run the following commands. Are these succesful and are using the correct release?

# sudo apt-get update
# sudo apt-get dist-upgrade


My output: > Error with:

sudo apt-get update

Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
  510 Not Extended [IP: 87.98.242.10 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
  510 Not Extended [IP: 87.98.242.10 80]
Fetched 801kB in 25s (31.8kB/s)
W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz) 510 Not Extended [IP: 87.98.242.10 80]
W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz) 510 Not Extended [IP: 87.98.242.10 80]
E: Some index files failed to download, they have been ignored, or old ones used instead.

sudo apt-get dist-upgrade updated Firefox and flash.

---

### Post by Potatoj316 on 2008-07-22
to install GNOMAD you could try (terminal)
```
sudo aptitude install gnomad
```

Ive had a similar problem where admin tasks just close before they actually ever open.  I usually just try to open it again and it works.  Im wondering if the thing that is suposed to ask for your password to allow you to open the program didnt work because that is the effect that I see.  The password prompter never opens and therefore the admin program cant so it closes.

---

### Post by TransplantedCanuck on 2008-07-22
Installing gnomad was just how I discovered it and the least of my worries. :p

As for the password prompting window, when I go to open startup manager I get the password prompt, type in the password and then nothing else happens.

---

### Post by TransplantedCanuck on 2008-07-23
Bump of desperation :)

---

### Post by iaculallad on 2008-07-23
> **TransplantedCanuck said:**
> Bump of desperation :)

Post your hosts file:

```
cat /etc/hosts
```

---

### Post by TransplantedCanuck on 2008-07-23
Here you go:

```
127.0.0.1	localhost
127.0.1.1	maren-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by TransplantedCanuck on 2008-07-25
bump... and...?

---

### Post by TransplantedCanuck on 2008-08-05
bump? Can anyone help me?

---

### Post by TransplantedCanuck on 2008-08-13
Update with some new info I got from elsewhere, but couldn't get any further advice. Maybe this might shed some new light on the problem? Is there a way to "re-install" without wiping out all my existing programs/data/information?

> When lots of programs just die like that, it usually indicates that some core library is corrupted, or didn't update correctly. Have you tried launching these programs from a terminal? What output do you get?


> Heres a few example things, the problem is, I don't seem to be able to find these in synaptic. Is there something like a repair install for Ubuntu(its a poor solution in windows, but it still works when time is short)? Or what would you recommend to fix this? A re-install is not really a suitable option due to time constraints on all sides of the equation.


```
maren@maren-desktop:~$ sudo su-to-root -X -c /usr/sbin/startupmanager
Traceback (most recent call last):
  File "/usr/sbin/startupmanager", line 31, in <module>
    from gtk_frontend import SumGui
  File "/usr/share/startupmanager/gtk_frontend.py", line 27, in <module>
    import pygtk
ImportError: No module named pygtk
maren@maren-desktop:~$ /usr/bin/update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 25, in <module>
    import pygtk
ImportError: No module named pygtk
maren@maren-desktop:~$ /usr/bin/gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 27, in <module>
    from AppInstall.activation import main
  File "/usr/lib/python2.5/site-packages/AppInstall/activation.py", line 20, in <module>
    import gconf
ImportError: No module named gconf
maren@maren-desktop:~$ sudo gksu -D /usr/share/applications/jockey-gtk.desktop /usr/bin/jockey-gtk
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 23, in <module>
    import gtk, gtk.glade, gobject, pynotify
ImportError: No module named gtk
    
```

---

