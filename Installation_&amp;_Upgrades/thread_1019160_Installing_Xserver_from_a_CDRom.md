---
title: "Installing Xserver from a CDRom"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by mr.vanker on 2008-12-22
Alright, so I'm not completely sure how it happened, but somehow it seems that the Xserver has been uninstalled from my Intrepid install. I don't remember doing anything with it, but it happened.

When I pass Startx, it says that the X11 folder does not exist. So, I want to know how I can install the Xserver from the Intrepid CDRom. I can't seem to connect to the internet, so I think that it needs to be done from the CDRom. Any ideas?

Thank you very much!

---

### Post by taurus on 2008-12-22
You mean something like

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install xserver-xorg
```

---

### Post by mr.vanker on 2008-12-22
hmm, when I do

```
apt-cdrom add
```

it says:

```
W: Skipping non-existing file /cdrom/dists/intrepid/main/binary-i386/packages
W: Skipping non-existing file /cdrom/dists/intrepid/restricted/binary-i386/packages
```

and then when I run sudo apt-get update, it adds the CDRom as a repository. But when I try to instal Xserver-xorg, it says:

```
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing.
```

---

### Post by taurus on 2008-12-22
What's the output of this command?

```
sudo apt-get update
```

---

### Post by mr.vanker on 2008-12-22
```
W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg Could not resolve 'wine.budgetdedicated.com'
```

That's one of the "W:" outputs, tharte are a lot of them, but at the bottom, it says:
```
W: You may want to run apt-get update to correct these problems
```

I can't see if it failed to fetch the CD though, because I can't scroll up to see the other W: messages.

---

### Post by taurus on 2008-12-22
Looks like you have some dead repos in /etc/apt/sources.list.  Can you post it?

```
more /etc/apt/sources.list
```
Tab the space bar for the next 24 lines.

---

### Post by mr.vanker on 2008-12-22
```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
## deb http://archive.canonical.com/ubuntu hardy partner
## deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
deb-src http://ppa.lauchpad.net/cdemu/ubuntu intrepid main
deb http://ppa.launchpad.net/cdemu/ubuntu intrepid main
```

---

### Post by taurus on 2008-12-22
> **mr.vanker said:**
> ```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
## deb http://archive.canonical.com/ubuntu hardy partner
## deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
[COLOR="Blue"]dep[/COLOR] http://security.ubuntu.com/ubuntu intrepid-security universe
[COLOR="Red"]deb-src http://security.ubuntu.com/ubuntu intrepid=security universe[/COLOR]
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
[COLOR="Red"]deb-src http://security.ubuntu.com/ubuntu intrepid-=security multiverse[/COLOR]
deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
deb-src http://ppa.lauchpad.net/cdemu/ubuntu intrepid main
[COLOR="Blue"]dep[/COLOR] http://ppa.launchpad.net/cdemu/ubuntu intrepid main
```

What happens to the top half?

Instead of using the = in the two repos in red, it should be -.

There are typo to the ones in blue.  It should be deb, not dep.

You can edit /etc/apt/sources.list with

```
sudo nano -Bw /etc/apt/sources.list
```
When you are done editing, save it and exit with <Ctrl>x and y to the question.

Then, run those commands again.

```

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install xserver-xorg

```

---

### Post by mr.vanker on 2008-12-22
whoops, sorry... Those are my typos. My system has it correct.

---

### Post by mr.vanker on 2008-12-23
Well, I finally decided to just boot with the LiveCD, transfer my home folder to an external drive, and then reinstall. Thanks for your help though!

---

