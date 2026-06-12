---
title: "Puting a conky on the desktop and customising it"
date: 2008-08-01
forum: General Help
---

### Post by Silpheed2K on 2008-08-01
A user was helping me customise my desktop.
I downloaded the latest version of conky for debian (ubuntu package is outdated)

So I'm wondering... I can only access conky from command line apparently but he gave me some instructions to enter into some text files that apparently conky reads.
So I'm wondering how do I go about this?

edit: crap i realise i should've put this in the desktop customization forum... if somebody sees this please move it.. and if you can help with my problem please reply.

---

### Post by LowSky on 2008-08-01
you could make a application launcher to save some typing.

What do you mean text files? use a program called gedit to edit text files

---

### Post by tamoneya on 2008-08-01
I have a file called ~/.startconky which looks like this:```
#!/bin/bash
sleep 30 &&
conky -c ~/.conkyrc;
```

Then in sessions I run the file so that conky autostarts.

---

