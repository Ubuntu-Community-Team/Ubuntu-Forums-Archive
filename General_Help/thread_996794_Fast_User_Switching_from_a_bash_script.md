---
title: "Fast User Switching from a bash script"
date: 2008-11-29
forum: General Help
---

### Post by urioli on 2008-11-29
Hi,

I'd like to call the fast user switching functionality from a bash script (entering another user session from a script). Anybody has any idea how I could do that?

What I'm trying to achieve is the following: I have already created a user that logins without a password and automatically starts xbmc (X-box Media Centre) fullscreen on my tv. I'd like to be able to activate this user session using my infrared remote control. I already know how to call a script from my remote so the only thing left is knowing how to activate a user session from a bash script.

Thanks in advance,

Oriol

---

### Post by cmnorton on 2008-11-29
Any bash script can become another user by entering su - username and entering that user's password. It's not the best idea to embed passwords in a script, but there are other ways to have scripts run on behalf of users. Cron is one way. You can get to a user's cron table being logged in as that user and using crontab -e, or you can specify the user to run a script in the global /etc/crontab.

---

### Post by urioli on 2008-11-30
Thanks for your prompt answer, but I don't think I've explained myself enough. I don't want to run a command as the user xmbc, I wan't to start the xmbc user X-session from a terminal window in any other user session (exactly as if I clicked on the Fast-User switching applet on the top right corner of the screen and I selected the xmbc user from that menu). I already know how su or cron work but they don't solve my problem. Thanks anyway.

---

### Post by KeyserSoze93 on 2008-11-30
```
sudo su xbmc -c "startx -- :2"
```
where xbmc is your xbox user.

---

