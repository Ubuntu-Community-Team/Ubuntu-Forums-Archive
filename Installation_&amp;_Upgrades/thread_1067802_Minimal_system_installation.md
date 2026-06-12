---
title: "Minimal system installation?"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by J.L.S. on 2009-02-12
Greetings,

[SIZE="1"]Forewarning: while I have recently gained quite a bit more experience with using ubuntu, shell commands and the like, I do not profess to be an expert on the subject; bear with me if I am ignorant in some situations.[/SIZE]


To cut to the chase, I am seeking to install ubuntu without any of the bundled software packages. I will never use Evolution or the Bluetooth resources, so I would like to install a bare system, and then selectively add programs.


Yesterday, on the recommendation of a friend, I installed the Server Edition of Intrepid. I then was told that if I were to [FONT="Courier New"]apt-get install firefox[/FONT], it would automatically download and install the GUI, as FF is useless without it. I soon found out that this is not true, it does not install the GUI. Next, I unwittingly undid my plan with [FONT="Courier New"]apt-get install ubuntu-desktop[/FONT], which of course installed all of the bundled packages.


Is there any true way to do this? I have read ([http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)), and I'm wondering if this is what I want. I've also heard of things like "overriding" the Minimal or Alternate install?


All insight is appreciated.


*Edit:* Note that&#8212;while preferred&#8212;if this is not easily possible, I'm willing to simply deal with it.

---

### Post by snowpine on 2009-02-12
"The GUI" is called a desktop environment or windows manager. If you want to use Gnome as your desktop environment:

```
sudo apt-get install gnome-core
```

Rather than ubuntu-desktop, which as you found out, gives you lots of applications too.

The psychocats guide you linked to is excellent, great place to start your research. It assumes you want to use icewm as your windows manager, so just substitute gnome-core (or give icewm a try). Good luck!

---

### Post by J.L.S. on 2009-02-12
Okay, cool. I think I'd like to stick with Gnome, so taking the psychocats instructions and replacing icewm, I would get...

```
sudo apt-get install xorg xterm gdm gnome-core menu firefox gksu synaptic
```

Correct?

Now, for my own good, I'll analyze all of the commands...

```
sudo apt-get update
```
... Updates the system if necessary?

```
sudo apt-get install xorg xterm gdm gnome-core menu firefox gksu synaptic
```
... Downloads and installs the Gnome enviroment, as well as xorg, xterm, gdm, menu, firefox, gksu, and synaptic. I'm guessing that menu is the ubuntu Menu application (duh), Firefox is obvious, Synaptic must be the Synaptic Package Manager, and gdm is the Gnome Login Manager? xorg, xterm, and gksu must be necessary and/or useful applications for the system? Are there any more that I really should have? In any case, others can be added via Synaptic, right? Should I ask another question? :P

```
sudo /etc/init.d/gdm start
```
... Starts the Login screen.


Thanks a lot for the help!

---

### Post by J.L.S. on 2009-02-12
Reading the forum CoC, I do not see any restrictions toward "bumping"; I hope that seven hours is not too short at time before double–posting.


Should I move this to the *Desktop Environments* forum now, as it doesn't have much to do with the actual installation of the ubuntu system?

---

### Post by marshimaro on 2009-02-13
```
sudo /etc/init.d/gdm start
```
... Starts the Login screen.

In fact, you can replace gdm by editing your xinitrc as well.

---

