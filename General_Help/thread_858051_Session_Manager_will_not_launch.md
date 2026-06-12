---
title: "Session Manager will not launch"
date: 2008-07-13
forum: General Help
---

### Post by upptown on 2008-07-13
Every time I try to launch "sessions" from System/Preferences/Sessions I get: "cannot connect to session manager".  Can anyone help me?

---

### Post by VMC on 2008-07-13
> **upptown said:**
> Every time I try to launch "sessions" from System/Preferences/Sessions I get: "cannot connect to session manager".  Can anyone help me?

I've never had that happen. I think it has something to do with your "~home/.metacity/sessions". I have several files there pointing to apparently what I have changed.

I don't know how to even launch it through Terminal. Like most gui's it has a python file somewhere. Not much help.

---

### Post by spiderbatdad on 2008-07-13
That is strange. Could you verify or post the output of```
sudo /usr/bin/ck-list-sessions
```

Also open /etc/PolicyKit/PolicyKit.conf with text editor and paste contents here.

Maybe simply restart or reinstall gdm.

---

### Post by upptown on 2008-09-07
> **spiderbatdad said:**
> That is strange. Could you verify or post the output of```
sudo /usr/bin/ck-list-sessions
```

Also open /etc/PolicyKit/PolicyKit.conf with text editor and paste contents here.

Maybe simply restart or reinstall gdm.

Sorry for the delay in replying.  In the end I did a fresh install of Hardy vice the upgrade and have not had the problem since.  I think it may have been caused by me mucking up the upgrade process.

---

