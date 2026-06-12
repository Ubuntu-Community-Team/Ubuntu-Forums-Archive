---
title: "Screenlets not starting after installation"
date: 2008-10-28
forum: General Help
---

### Post by belier on 2008-10-28
Hi.

I've just installed screenlets using synaptics. I've launched it, it appears on task bar for a while with the sand glass and then disappears. I've tried to install it again using sudo apt-get install screenlets* and it happens the same. I've read about screenlets on the forum but no succes,

Any idea?

Thanks in advance

---

### Post by xb3rtx on 2008-10-28
Are you having trouble running the screenlets program in general or just screenlets.  I have screenlets installed and retrieved it the same way but didnt have any trouble opening the main app.  The problem I have is getting screenlets to launch on boot, and getting them to stay stuck to a certain cube face.  It also seems like it takes forever to load some of these screenlets too.

---

### Post by NewJack on 2008-10-28
I posted this over on your other thread in the Absolute Beginner Forum [http://ubuntuforums.org/showthread.php?p=6050704#post6050704](http://ubuntuforums.org/showthread.php?p=6050704#post6050704) (Please mark one of these for deletion):


After installing Screenlets, did you restart X (Ctrl-Alt-Backspace then log back in)? If so, then look in your Sessions>Startup tab and make sure that Screenlets is set to run at startup. If it isn't just add it manually. That should do the trick.

If that doesn't, then I would say to run Screenlets from the Terminal by typing ```
screenlets
```
 to see if you get any error messages.  Maybe you are missing a dependency somewhere along the way.

Good luck, hope that helped!

---

