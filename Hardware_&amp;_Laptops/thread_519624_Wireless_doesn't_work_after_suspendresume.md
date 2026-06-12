---
title: "Wireless doesn't work after suspend/resume"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by saxonthebeach908 on 2007-08-07
Just got Feisty going on my m1210...managed to get most everything working fine, except after suspending, my wireless doesn't work on resume. I'm using wicd instead of NM (nm wouldn't connect to networks). In order to get wireless to work after resuming, I have to manually run wicd again; when I do this the old instance of wicd shows up and starts working, leaving me with two instances in the systray. I can close one of them and everything works like before, but I'd rather not have to go through all these steps after each suspend/resume, as I use suspend a lot. Any suggestions?

---

### Post by imdano on 2007-08-07
What version of wicd are you using?  What happens with wicd when you resume?  The tray disappears or just stays disconnected?  When you manually run wicd again, what command are you using?

---

### Post by saxonthebeach908 on 2007-08-08
> **imdano said:**
> What version of wicd are you using?  What happens with wicd when you resume?  The tray disappears or just stays disconnected?  When you manually run wicd again, what command are you using?

When I resume, the tray disappears ( but leaves a blank empty space) and stays disconnected. When I run it manually, i use alt+F2 and /opt/wicd/tray.py

---

### Post by imdano on 2007-08-08
What version are you using, and is the network you want to connect to set to automatically connect?  It'd also be helpful if you run /opt/wicd/tray.py from the command line so debugging output would get logged there, suspend, and post the output you get on resume.

---

### Post by saxonthebeach908 on 2007-08-08
Ver. 1.3.1. Yes, set to automatically connect. On resume in the terminal I just repeated this indefinitely:
```
networkID returned -1, waiting...
networkID returned -1, waiting...
networkID returned -1, waiting...
networkID returned -1, waiting...
networkID returned -1, waiting...
networkID returned -1, waiting...
networkID returned -1, waiting...

```

---

### Post by imdano on 2007-08-08
I think this is a known bug that's fixed in newer versions.  Download this edgy.py and put it in the /opt/wicd directory.  Restart the tray and see if the problem is solved.

[http://wicd.svn.sourceforge.net/viewvc/*checkout*/wicd/stable/edgy.py?revision=71](http://wicd.svn.sourceforge.net/viewvc/*checkout*/wicd/stable/edgy.py?revision=71)

---

### Post by saxonthebeach908 on 2007-08-08
No luck....replaced the edgy.py with that one, but it still does the same thing...

---

### Post by saxonthebeach908 on 2007-08-08
Nevermind, I changed some of the drivers wicd was using around and got it working. thanks for the help

---

### Post by imdano on 2007-08-08
Glad you got it working.  Do you mind sharing exactly what you were using and what you changed?  It might help someone else with a similar problem.

---

### Post by saxonthebeach908 on 2007-08-08
I switched the WPA driver option in wicd from ndiskwrapper to 'madwifi' and that solved all my problems...I'm just going to take it for what it is and not ask questions :)

---

