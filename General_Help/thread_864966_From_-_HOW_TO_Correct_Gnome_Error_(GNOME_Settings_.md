---
title: "From - HOW TO: Correct Gnome Error (GNOME Settings Deamon)"
date: 2008-07-20
forum: General Help
---

### Post by Frogster on 2008-07-20
Having now reinstalled 8.4 for the fifth time I am about to consign it to the bin as its not going to work on the PC.

All works well until I hit the Update button. 

Every installation gets the "(GNOME Settings Deamon)"error, I have read all the threads on here and elsewhere but all involve entering code. 

How do I enter the codes when I cant get past the error notification? 

Is it worth the extra time or should I just stick to 7.10 and wait for this issue to be cleared up in a later release

---

### Post by Frogster on 2008-07-20
Bump

---

### Post by macaholic on 2008-07-20
When people are referring to entering code they mean in a terminal, or console. To open one up in GNOME, simply go to Applications > Accesories > Terminal Paste whatever code you need to in, and hit enter.

---

### Post by Frogster on 2008-07-20
> **macaholic said:**
> When people are referring to entering code they mean in a terminal, or console. To open one up in GNOME, simply go to Applications > Accesories > Terminal Paste whatever code you need to in, and hit enter.

 Thank you for the reply. When I get this error message I cant get to a terminal as the close button doesn't work, I just have a screen with the error message. If I can get to a terminal I am quite happy to enter the code.

Its the getting past the message and to a terminal that I need help with :confused:

Any help is greatly appreciated as I like the look of Heron but I am spending far to many hours trying to get it to run.

---

### Post by pauper on 2008-07-20
> How do I enter the codes when I cant get past the error notification?
1) Try switching to TTY (press Ctrl+Alt+F2; to go back--Ctrl+Alt+F7), login and
kill update-manager, update-notifier from here:

Find their <pid> numbers:

```
pgrep update-notifier
pgrep update-manager
```

Try to terminate:
```
sudo kill <pid>
```

If it fails use -2, -1, -9 signals in order, i.e.

```
sudo kill -2 <pid>
```

If that doesn't work restart gdm:

```
sudo /etc/init.d/gdm restart
```

2) You can leave update-manager alone if it's broken and do updates other way:

In CLI:

```
sudo apt-get update
sudo apt-get upgrade
```

Use aptitude

```
sudo aptitude
```

Use Synaptic:

System--Administration--Synaptic Package Manager

Click Reload.

3) Download different version of update-manager, update-manager-core, update-
notifier, update-notifier-common. There are .deb packages and source code here:

[http://packages.ubuntu.com/hardy/update-manager](http://packages.ubuntu.com/hardy/update-manager)
[http://packages.ubuntu.com/hardy/update-manager-core](http://packages.ubuntu.com/hardy/update-manager-core)
[http://packages.ubuntu.com/hardy/update-notifier](http://packages.ubuntu.com/hardy/update-notifier)
[http://packages.ubuntu.com/hardy/update-notifier-common](http://packages.ubuntu.com/hardy/update-notifier-common)

An advice: Do some heavy testing with Live CD before doing full upgrade. Gutsy
is supported till April 2009.

---

### Post by Frogster on 2008-07-20
Thank you pauper. I will give these options a go and hopefully be able to get this problem sorted and also learn some more. 

Luckily the machine Heron is on is my test machine

---

