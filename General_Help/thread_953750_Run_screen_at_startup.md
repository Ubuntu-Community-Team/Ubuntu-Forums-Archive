---
title: "Run screen at startup"
date: 2008-10-20
forum: General Help
---

### Post by Woody1987 on 2008-10-20
I have a server where i download torrents. To do this i use rtorrent. I would like to be able to start 'Screen' at startup and then within that run rtorrent. Is this possible?

---

### Post by Afkpuz on 2008-10-20
Well, I don't know the specific commands to do that, but I can show you how to run a command at startup.


System>Preferences>Sessions

Click Add

Give a name to this command, then type the specific command into "command".  Then, that will be run at every log in.

---

### Post by bodhi.zazen on 2008-10-20
Yes it is quite easy.

Assuming you do not want to run screen as root, run this in rc.local:

```
sudo -u user screen -d -m rtorrent &
```

where "user"is the user to run screen/rtorrent

Not sure if the & is needed here, you *may* be able to skip it.

---

