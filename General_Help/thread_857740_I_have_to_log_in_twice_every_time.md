---
title: "I have to log in twice every time"
date: 2008-07-12
forum: General Help
---

### Post by adohall on 2008-07-12
This has been happening for over a week - perhaps since last kernel update (?) to my 8.04 installation (which had been running fine for months): The first time I get the login screen I log in, then I see a black screen with 4-line terminal-style message then a blank screen for a couple of seconds then I'm shunted back to the login screen. I log in again and now everything proceeds normally. When I exit Ubuntu, I get a long terminal-style message on a black screen for a couple of seconds before proceeding to the splash screen and close-down. All of this happens every session. Any ideas on how to fix the problem? It's not life-threatening but annoying none the less.

---

### Post by hcwinsemius on 2008-07-15
Yep, same problem here, I haven't found many useful comment until now. Can anybody help out?

---

### Post by Hoyret on 2008-07-16
Happening here as well.  I looked at my syslog and found the following line at about the time when it happened:

Jul 16 03:09:59 egg gdm[5324]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

---

