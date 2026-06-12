---
title: "Start Ubuntu With No Monitor?"
date: 2010-06-06
forum: Hardware
---

### Post by xLinkToMidnightx on 2010-06-06
Hey
I have Ubuntu 10.04. I'm trying to auto boot to the GUI with no screen or keyboard for I can access it using remote software, but when I try to boot, nothing happens....so I plug in my screen and it gives an error. Annddd...then boots into command.

Any way to auto boot into GUI with no screen attached?

It's a old 2400 dell

---

### Post by Windows Nerd on 2010-06-06
> **xLinkToMidnightx said:**
> Hey
I have Ubuntu 10.04. I'm trying to auto boot to the GUI with no screen or keyboard for I can access it using remote software, but when I try to boot, nothing happens....so I plug in my screen and it gives an error. Annddd...then boots into command.

Any way to auto boot into GUI with no screen attached?

It's a old 2400 dell
When you start the computer with the monitor unplugged I believe the error is coming from the fact that you are trying to boot to a GUI without the monitor: Ubuntu sees no monitor and then drops to a CLI because quite frankly there is no use from running a GUI with nothing to display and use it with.

Once you acess the computer remotely (depending on how you do it) you will probably connect with only command-line functionality and (and again, depending on how you connected remotely) have to get into a GUI from there. Some methods only allow CLI functionality via remote access.

It is possible for computers to run perfecly capably without monitors and the acessed remotely becuase most (if not 97%) of servers are ran that way (except to set them up and set-up remote acess.

Scott

---

### Post by Austin25 on 2010-06-06
When you access it remotely, if it is in cli use this:
```
sudo startx
```
it will start the gui

---

### Post by xLinkToMidnightx on 2010-06-06
hm
is there anyway to just disable this check?
I'm using teamviewer, and it only works after the user logs in

---

### Post by xLinkToMidnightx on 2010-06-06
also, i tried editing xonf  file. it worked....buuut it loaded at 640/480 and i couldnt change the res.

---

### Post by Hugolp on 2010-08-20
I am interested in this also.

I have a home server but I need the GUI part because it is running Mythtv server, and it needs it. But it runs on a headless server and I would like to be able to reboot it without a monitor, mainly for the kernel updates, that are the only reason I have to reboot it.

---

### Post by Hugolp on 2010-08-20
> **Austin25 said:**
> When you access it remotely, if it is in cli use this:
```
sudo startx
```
it will start the gui

But this only works if there is a screen attached.

Seriously, there has to be a way to do this. Everytime there is a kernel update I have to move a monitor from one of the computers to the server, plug it in, restart the server and then move the monitor back. Its ridiculous.

---

