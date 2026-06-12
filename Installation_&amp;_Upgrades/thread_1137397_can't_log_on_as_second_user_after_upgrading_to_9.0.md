---
title: "can't log on as second user after upgrading to 9.04"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by yesongs on 2009-04-25
After upgrading to 9.04 my computer works fine with no problem at all.
but...
When I try to log out and log on as a different user (there are two users on my PC), I have a black screen, the mouse pointer is visible and moving and nothing more. My only option is then to reset the PC and reboot again as the first user. (Automatically logon).
The home/2nd user files are accessible when I logon as the 1st user and this is not suppose to happen.
How can I get the 2nd user back?

---

### Post by bsmith1051 on 2009-04-25
From your main login, use your sudo password to hide all the "." config files in the other user's /home, e.g.
```
> cd /home/user2
> sudo mkdir OLD-CONFIGS
> sudo mv ".*" OLD-CONFIGS
```
I'm not really sure if those commands will work as I've written them, but you get the idea.

My suspicion is that the upgrade did something to your Gnome and/or X configuration files -- but only on your current account, i.e., it skipped any other accounts.  So the workaround is to let them be recreated from scratch (and then manually restore anything important).

---

### Post by yesongs on 2009-04-27
thanks for your answer. I've just tried the solution you proposed and worked fine!
I copied back the .* folders that contained settings that i need (like firefox or pidgin) and now everything works fine.
the only thing is that the last command
> sudo mv ".*" OLD-CONFIGS
didn't worked so I moved the folders logging in as root.
Anyway I have it back:guitar:
Thanks again!!!

---

### Post by bsmith1051 on 2009-04-29
Excellent!  I'll probably face the same issue when I upgrade, good to know the fix :smile:

---

