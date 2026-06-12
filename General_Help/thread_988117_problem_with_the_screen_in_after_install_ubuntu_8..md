---
title: "problem with the screen in after install ubuntu 8.10 with wubi"
date: 2008-11-20
forum: General Help
---

### Post by ElMatador on 2008-11-20
[COLOR="Navy"][SIZE="4"][FONT="Arial"]Hey guys

I have installed yesterday the last version of ubuntu " ubuntu 8.10 " using the little magician wubi, after I finished all the settings and entered the user name and the password in the log screen, an orange screen appears with the cursor and nothing else, so I can t do nothing, I don't know what to do?

anybody can help ?! [/FONT][/SIZE][/COLOR]

---

### Post by hawkhock on 2008-11-27
Installed 8.10 via Wubi today. Same problem as above.  Forum suggestions include 
running chkdsk /r in XP.  Did that - volume is clean.  
Ran defrag in XP; uninstalled Wubi and ran defrag in XP again. 

Will reinstall Wubi to see if problem persists.

---

### Post by hawkhock on 2008-11-28
Second install of Wubi 8.10 -- same problem.  Further research found that "in 8.10 compiz uses a video graphics code path no used by any other code" and affects many Intel graphics. I found the answer and solution at.

ubuntuforums.org/showthread.php?t=973984

G in UT

---

### Post by Swagman on 2008-11-30
> **hawkhock said:**
> Second install of Wubi 8.10 -- same problem.  Further research found that "in 8.10 compiz uses a video graphics code path no used by any other code" and affects many Intel graphics. I found the answer and solution at.

ubuntuforums.org/showthread.php?t=973984

G in UT

Now with added [** Clickability**](http://ubuntuforums.org/showthread.php?t=973984) <-----

---

### Post by ago on 2008-12-01
That is probably a video card issue, press esc at boot, go for rescue mode, you should have an option to repair your video configuration. You might have to install the appropriate video drivers.

---

