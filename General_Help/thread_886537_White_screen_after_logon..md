---
title: "White screen after logon."
date: 2008-08-11
forum: General Help
---

### Post by wilko125 on 2008-08-11
Hey all, Ive had this error for the past two days (only installed ubuntu 3 days ago). Basically right after logging into Gnome I get a black screen with a cursor which shortly changes to a white screen with a cursor. I can bring up a terminal most of the time with Ctrl+Alt+F1.

I've tried a few solutions I have found in other threads regarding similar problems, but to no avail. I'm running Ubuntu 8.04

This problem occurred after installing about 100mb of updates and restarting.

Fixes I've tried:

1.
```

sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure ubuntu-desktop

```

2. I've tried xfix from the recovery screen.

3. I've tried creating a different user account and logging in with that.

There is something in the start up scripts that is doing this but I have no idea how to check/fix whatever has happened to my system since the updates.

I'm writing this on the gnome-failsafe login.

Any help would be appreciated - I don't feel like reinstalling ubuntu :p

---

### Post by wilko125 on 2008-08-13
Bump, please help :(

---

### Post by sayakb on 2008-08-13
Press Ctrl+Alt+F1, login to tty1 and type in:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And restart X

---

### Post by wilko125 on 2008-08-13
Unfortunately that didn't yield any results either, by the look of the output once I ran that command, it is essentially the same as the xfix option in the recovery screen.

Thanks for your help anyway :)

---

### Post by Green_Star on 2008-08-13
I am not sure what display card you have. I have ATI X1300, same thing happened. I started ubuntu normally, and selected some session before logging in.(screen was so weired, so not able to see which I was selecting). And installed latest ATI drivers using envy. Everything fine after that.

---

