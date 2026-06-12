---
title: "crash during libxine update -- afterwards startx and dpkg fail"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by mltucker on 2009-02-17
Hello,

I did some searching and couldn't find any solutions to this problem.  I backed up my home directory and am ready with a new install disk, so any way to prevent this would be much appreciated.  Many details:

I have 8.10 kubuntu installed.  I was updating my kernel headers and some libxine libraries when my computer crashed.  This means I couldn't switch workspaces, and had basically a white screen and the mouse couldn't move.  I "ctrl-alt-f1,f2,f3,etc"ed my way into a command line, but none would work.  I had some cryptic error messages that I didn't think to write down, and couldn't get a prompt.

A hard reboot gets me to the command line login with the error message 

xmodmap: unable to open display ''

A first startx loaded kde, but I could not move the mouse and I got a series of error messages telling me how badly libxine1 is messed up..  I also did not write these down, and starting x after this gives me the error message:

(EE) config/hal: couldn't intialise context: (null) ((null))

waiting for X server to shut down.

It seemed like a good idea to try to uninstall libxine1, so I did

```
sudo apt-get remove libxine1
```

which tells me 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

then,

```
sudo dpkg --configure -a
```

tells me

dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1: field name `ag' must be followed by colon.

However, nanoing into this file shows me

ag^_^@bg^_^@...

and I'm not sure what I should do with this.  Should I delete the file and hope it will generate a new one?  Putting a colon after ag yields

dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 2: MSDOS EOF (^Z) in field name `'

This file seems to just be trash.  So... I don't even really know what the problem is.  I know that it crashed during update, and I can't start x or run dpkg.

Any help would be appreciated!

-Mark

---

### Post by Partyboi2 on 2009-02-17
Try
```
sudo dpkg --clear-avail
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by mltucker on 2009-02-17
Ah.  Thanks for the help.  Unfortunately I ended up reinstalling.  I wish I had waited.

-Mark

---

