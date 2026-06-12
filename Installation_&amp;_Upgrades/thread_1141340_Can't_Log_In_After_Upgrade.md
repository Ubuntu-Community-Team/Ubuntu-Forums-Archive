---
title: "Can't Log In After Upgrade"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by jretzer on 2009-04-28
I just upgraded online to the new version and now I can't log in. It asks for a username and password, but I don't ever recall being asked for a username before ... what to do?

This is on a dual boot with my XP machine

---

### Post by cariboo on 2009-04-28
You have to use the user name and password that you set when you origionally installed Ubuntu. THe name of your home directory is your user name. To cahnge the password, start in recovery mode, and at the menu select drop to root prompt, then at the prompt type:

```
passwd <username>
```

Where <username> is your username without the brackets.

---

