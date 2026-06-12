---
title: "Limewire Errors"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by vlastanovak on 2008-12-28
I'm trying to install Limewire, but am having some difficulties. Here's a recap of what has been done and what has happened;

1. Downloaded Limewire for Linux from linux.com.

2. I try to run it and it says only one software management tool is allowed to be opened at once, but there's nothing else open!

---

### Post by midnightfox2 on 2008-12-28
I didn't know there was a limewire for linux. Thanx !
I used GTK gnutella instead. Works too but it takes a long time before you get any result on searches.

---

### Post by labinnsw on 2008-12-28
Forget limewire. Try frostwire same thing but free.

---

### Post by Partyboi2 on 2008-12-28
> **vlastanovak said:**
> I'm trying to install Limewire, but am having some difficulties. Here's a recap of what has been done and what has happened;

1. Downloaded Limewire for Linux from linux.com.

2. I try to run it and it says only one software management tool is allowed to be opened at once, but there's nothing else open!

Have you tried rebooting? Another thing you can do is open a terminal and check if there is any Software management tool running by
```
ps x
``` If there is no software management tool running then you may need to remove the lock file
```
sudo rm /var/lib/dpkg/lock
``` But make sure first there is no Software management  tool running before removing the lock file.

If you decide to install frostwire you can get the deb from [[COLOR=Blue]here[/COLOR]]("http://www.frostwire.com/?id=thanks&os=ubuntu").

---

### Post by halw on 2008-12-28
> **labinnsw said:**
> Forget limewire. Try frostwire same thing but free.

Ditto for Frostwire.

---

### Post by vlastanovak on 2008-12-28
OK guys thanks, I will try frostwire instead.

Cheers.

---

### Post by vlastanovak on 2008-12-28
OK I have tried frostwire and am getting the same error;

> Only one software management tool is allowed to run at the same time -
Please close the other application e.g. 'Update Manager', 'aptitude' or 'synaptic' first.

However, I have just restarted my computer.. so nothing is running?

I have now run the command 'ps x' and it returns the following;

>   PID TTY      STAT   TIME COMMAND
 5390 ?        S      0:00 /usr/bin/gnome-keyring-daemon -d --login
 5401 ?        Ssl    0:00 x-session-manager
 5479 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pul
 5480 ?        Ss     0:00 //bin/dbus-daemon --fork --print-pid 6 --print-addres
 5483 ?        Ssl    0:00 /usr/bin/pulseaudio -D --log-target=syslog
 5486 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
 5488 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2
 5495 ?        Ss     0:00 /usr/bin/seahorse-agent --execute x-session-manager
 5505 ?        S      0:00 /usr/lib/gvfs/gvfsd
 5506 ?        S      0:00 /usr/lib/gnome-session/helpers/gnome-keyring-daemon-w
 5510 ?        Ssl    0:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 5511 ?        S      0:00 /bin/sh /usr/bin/compiz
 5516 ?        Ssl    0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/vlastanovak/.gv
 5585 ?        S      0:03 /usr/bin/compiz.real --ignore-desktop-hints --replace
 5596 ?        Ss     0:00 gnome-screensaver
 5597 ?        Ss     0:00 /bin/sh -c /usr/bin/compiz-decorator
 5598 ?        S      0:00 /bin/sh /usr/bin/compiz-decorator
 5600 ?        S      0:01 /usr/bin/gtk-window-decorator
 5605 ?        S      0:03 gnome-panel
 5606 ?        S      0:03 nautilus --no-desktop --browser
 5609 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server -
 5623 ?        S      0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
 5625 ?        S      0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 5628 ?        S      0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.6 /org/gtk/gvfs
 5634 ?        S      0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid
 5637 ?        S      0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.6 /org/gtk/gvf
 5646 ?        S      0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-app
 5648 ?        Sl     0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i
 5665 ?        S      0:00 python /usr/share/system-config-printer/applet.py
 5666 ?        Sl     0:00 /usr/lib/evolution/2.24/evolution-alarm-notify
 5674 ?        S      0:00 tracker-applet
 5675 ?        SNl    0:00 trackerd
 5676 ?        S      0:00 bluetooth-applet
 5677 ?        S      0:00 nm-applet --sm-disable
 5681 ?        S      0:00 update-notifier
 5685 ?        Ss     0:00 gnome-power-manager
 5689 ?        Sl     0:00 /usr/lib/evolution/2.24/evolution-exchange-storage --
 5714 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-2.24 --oaf-a
 5789 ?        S      0:00 /usr/lib/notification-daemon/notification-daemon
 5895 ?        Sl     0:13 /usr/lib/firefox-3.0.5/firefox
 6317 ?        S      0:02 gksu --desktop /usr/share/applications/gdebi.desktop
 6476 ?        Sl     0:00 gnome-terminal
 6478 ?        S      0:00 gnome-pty-helper
 6479 pts/0    Ss     0:00 bash
 6497 pts/0    R+     0:00 ps x


This is all gibberish to me, so what do I do now?

---

### Post by labinnsw on 2008-12-28
Try the other code by Partyboi2

sudo rm /var/lib/dpkg/lock

Close the terminal

Then try installing it again

---

### Post by vlastanovak on 2008-12-28
I tried it, and am still getting the following message;


> Only one software management tool is allowed to run at the same time -
Please close the other application e.g. 'Update Manager', 'aptitude' or 'synaptic' first. 

WTF?

---

### Post by vlastanovak on 2008-12-28
Also whenever I try to run a few other things I get the following message;

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I try to run it and it says I need superuser privileges!? I'm the only user though lol.

---

### Post by Partyboi2 on 2008-12-28
Open a terminal and do what is mentioned.
```
sudo dpkg --configure -a
```

---

### Post by JeremyS2 on 2008-12-31
i had the same error when i tried to install open office, limewire, and skype but the most recent code fixed my problem! :D 

:D:D:D Thanks and HAPPY NEW YEAR!!!!! :D:D:D

> Open a terminal and do what is mentioned.
Code:

sudo dpkg --configure -a



---

