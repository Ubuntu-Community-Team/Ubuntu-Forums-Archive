---
title: "I got this! I dont know why! ?? :("
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by &#65313;&#65324;&#65321; on 2009-07-19
Hi everyone.

I am new to the forum as well as linux! This is my first thread.

I have ubuntu 8.10, and i wish to upgrade FF with the latest 3.5 one.


I used the following code in the terminal:


[FONT=Courier New][SIZE=3][COLOR=Purple]sudo apt-get update
sudo apt-get autoremove
sudo apt-get install firefox[/COLOR][/SIZE][/FONT]


and the problem that i got:

[SIZE=2][COLOR=Purple]alih@alih-desktop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR][/SIZE]


After I started FF, it said 3.0.11 again, with no change!

Did I miss something? :confused:

Anyone helps me please.

---

### Post by .nedberg on 2009-07-19
You need to uninstall the FIrefox you have
```

sudo apt-get remove firefox

```
then install firefox-3.5
```

sudo apt-get install firefox-3.5

```

---

### Post by vinutux on 2009-07-19
alternatively install from here**[COLOR="DarkGreen"][ https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa")[/COLOR]**

---

### Post by Sef on 2009-07-19
> alternatively install from here**[COLOR=DarkGreen][ https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")[/COLOR]**That is the recommended way to upgrade to Firefox 3.5.

> You need to uninstall the FIrefox you have
     Code:
     sudo apt-get remove firefox 
then install firefox-3.5
     Code:
     sudo apt-get install firefox-3.5 
That is not the recommended way to upgrade to Firefox 3.5.   The correct way is to download Firefox 3.5 is via a PPA.

---

