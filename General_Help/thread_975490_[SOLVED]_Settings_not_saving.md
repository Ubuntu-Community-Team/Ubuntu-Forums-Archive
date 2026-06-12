---
title: "[SOLVED] Settings not saving"
date: 2008-11-08
forum: General Help
---

### Post by shortylonglegs on 2008-11-08
After installing 8.10, none of my settings are being saved between sessions in any of my programs.  For example, I set up my panels the way I want, with the launchers I want and where I want them.  Then I restart my computer the way I'm supposed to, not hard, and when I get back, my panel is reset to the default.  This is the same with all my programs, I use liferea for rss, so I set it up how I want, check feeds every hour instead of every day, check on startup, etc.  Shut down liferea and start it again, my feeds are there, but all the settings are back to the default.  This is the same with all my programs, and its quite irritating to have to reset all my preferences each time I run a program.  I was having trouble before with owning the permissions of my home folder, but I thought that was sorted out, could this have anything to do with it?  Thanks for any help you can give.


If anyone cares, it was evidently a problem with ownership.  I ran
```
 sudo chown myusername:mygroup ~/* 
``` 
and now it works

---

