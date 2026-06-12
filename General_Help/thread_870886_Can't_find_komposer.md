---
title: "Can't find komposer"
date: 2008-07-26
forum: General Help
---

### Post by no-1-uno on 2008-07-26
After reading some of the past post's on WYSIWIG editors I decided to install Bluefish and Komposer.

I used the terminal install instructions from one of the posts
```
 sudo apt-get install bluefish komposer
```

and Bluefish installed but Komposer did not, I then tried 
```
 sudo apt-get install komposer
```
and still no program just a message 
*[I]Couldn't find package komposer*[/I].

Then I tried the S.P.M., with the 2 extra repositories enabled I did a search for komposer and it came up blank.

Where do I find Komposer? I used to use Frontpage 2002 and was moving over to Dreamweaver MX when I started my march with the Penguins.

If Komposer is not available is there a program somewhere between Frontpage and Dreamweaver

---

### Post by stevoo on 2008-07-26
Kompozer should be displayed in the Internet Section of applications

I dont have it installed any more so i cant remember 
but running
Kompozer 
from the command prompt will it display anything ?

---

### Post by drs305 on 2008-07-26
> **no-1-uno said:**
> After reading some of the past post's on WYSIWIG editors I decided to install Bluefish and Komposer.

I used the terminal install instructions from one of the posts
```
 sudo apt-get install bluefish komposer
```


It's spelled with a Z = kompozer - that should fix things.

Added: Please mark this SOLVED if that takes care of it.

---

### Post by no-1-uno on 2008-07-26
DUH??????

Let me try that and see what happens.

[Blushing and looking more stupid than normal]

---

### Post by no-1-uno on 2008-07-26
tojo@ubuntu:~$ sudo apt-get install kompozer
[sudo] password for tojo: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
tojo@ubuntu:~$ 


OK what do I do with this?

---

### Post by drs305 on 2008-07-26
> **no-1-uno said:**
> tojo@ubuntu:~$ sudo apt-get install kompozer
[sudo] password for tojo: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
tojo@ubuntu:~$ 

OK what do I do with this?

Do you have another synaptic still open? If so, close it. If you don't think you do, run the following and see if synaptic or some other installation app like apt-get or aptitude is listed:
```
ps -u *username*
```

If you find another installation app open, kill it with:
```
sudo killall *appname*
```

---

### Post by no-1-uno on 2008-07-26
tojo@ubuntu:~$ ps -u tojo
  PID TTY          TIME CMD
 6137 ?        00:00:05 gconfd-2
 6139 ?        00:00:00 gnome-keyring-d
 6140 ?        00:00:00 x-session-manag
 6264 ?        00:00:00 seahorse-agent
 6268 ?        00:00:00 dbus-daemon
 6269 ?        00:00:04 gnome-settings-
 6280 ?        00:00:07 pulseaudio
 6297 ?        00:00:00 gconf-helper
 6306 ?        00:00:00 compiz
 6307 ?        00:00:12 gnome-screensav
 6309 ?        00:00:15 gnome-panel
 6314 ?        00:00:06 nautilus
 6321 ?        00:00:00 bonobo-activati
 6345 ?        00:00:00 gvfsd
 6362 ?        00:00:00 gvfs-fuse-daemo
 6389 ?        00:01:35 compiz.real
 6390 ?        00:00:00 bluetooth-apple
 6393 ?        00:00:01 update-notifier
 6398 ?        00:00:00 tracker-applet
 6403 ?        00:00:00 trackerd
 6406 ?        00:00:00 python
 6407 ?        00:00:00 gnome-volume-ma
 6408 ?        00:00:09 nm-applet
 6410 ?        00:00:00 gnome-power-man
 6456 ?        00:00:00 trashapplet
 6459 ?        00:00:00 gvfsd-trash
 6461 ?        00:00:00 gvfsd-burn
 6471 ?        00:00:00 evolution-data-
 6506 ?        00:00:00 mixer_applet2
 6508 ?        00:00:00 fast-user-switc
 6510 ?        00:00:00 sh
 6511 ?        00:00:00 compiz-decorato
 6513 ?        00:00:07 gtk-window-deco
10717 ?        00:32:44 firefox
10768 ?        00:00:17 evolution
10793 ?        00:00:00 evolution-excha
11209 ?        00:00:02 gnome-terminal
11211 ?        00:00:00 gnome-pty-helpe
11667 ?        00:00:01 notification-da
12137 ?        00:00:00 gksu
13747 pts/1    00:00:00 bash
17521 ?        00:00:00 gedit
18992 pts/1    00:00:00 ps
tojo@ubuntu:~$ 

Too far ahead of me, been running Ubuntu for almost one month now. Still very wet behind the ears.

---

### Post by no-1-uno on 2008-07-26
Got it to work, did not relize that just having the S.P.M. open would not allow the terminal to work.

Thanks for all the help

Even learning my way around and bruising my head glad to have converted to the march of the Penquins

---

### Post by drs305 on 2008-07-26
> **no-1-uno said:**
> 
Too far ahead of me, been running Ubuntu for almost one month now. Still very wet behind the ears.

No problem ;-)  None of the running apps appear to be installers.

We can try these two commands although it probably won't clear it. If not you might try rebooting.

```
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a
```

---

