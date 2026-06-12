---
title: "Top and bottom bar not showing in Ubuntu 8.04"
date: 2008-07-25
forum: General Help
---

### Post by jsblackmaro on 2008-07-25
Hello all!
I have been running Ubuntu 8.04 for a week or so now, and its been running great!!!  No issues!  I turned on the PC this morning, and there were no bars on the top or the bottom.  It makes it very hard to use the system without those bars.  I tried atl+F2 to run the menu or any other program, and I had no luck.  Any ideas??  Please help!!!!

Josh

---

### Post by gimlithedwarf on 2008-07-25
Josh: try restarting x with ctrl-alt-backspace if that doesn't work under the login screen click actions->safe gnome and then try logging in, if either of those work tell us. Otherwise post some hardware details

---

### Post by fooman on 2008-07-25
did you get the run dialog box when you tried alt - f2 ?

if you did....then type the following into the space:

```
gnome-panel &
```

then clik on "run"

---

### Post by jsblackmaro on 2008-07-25
for gimlithedwarf:
The Crtl Alt backspace did not work.  I tried all the sessions under change session except for the remote terminal and failsafe terminal.  So no luck.
Heres the hardware

Dell Optiplex GX270
Maxtor 120GB SATA Primary
Segate 160GB SATA Slave
ATI Radeon X Proo 700 Video Card Running DVI to VGA
WD 250GB My Book External USB Drive

Need anymore?

To fooman:
I did not receive the run dianlg when I hit Alt-F2.  It just sat there and did nothing...

---

### Post by fooman on 2008-07-25
try this...ctrl - alt - f1

that should take you to a prompt.  log in as root.  type this:

```
apt-get install nautilus-open-terminal
```

reboot

when you get back to your desktop...right click and choose "open terminal"

type:

```
gnome-panel &
```

that should do it.

---

### Post by jsblackmaro on 2008-07-25
fooman:
I got all that to work, and I got the panels to load.  Some of them failed..  Heres what I got.

** (gnome-panel:6166): WARNING **: panel-applet-frame.c:1270: failed to load applet OAFIID:GNOME_Panel_TrashApplet:
System exception: IDL:Bonobo/GeneralError:1.0 : Couldn't spawn a new process:Failed to execute child process "/usr/lib/gnome-applets/trashapplet" (No such file or directory)

(gnome-panel:6166): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24

** (gnome-panel:6166): WARNING **: panel-applet-frame.c:1270: failed to load applet OAFIID:GNOME_MixerApplet:
System exception: IDL:Bonobo/GeneralError:1.0 : Couldn't spawn a new process:Failed to execute child process "/usr/lib/gnome-applets/mixer_applet2" (No such file or directory)

** (gnome-panel:6166): WARNING **: panel-applet-frame.c:1270: failed to load applet OAFIID:GNOME_FastUserSwitchApplet:
(null)

Any ideas?  Do I have to find these applets and install them?

---

### Post by jsblackmaro on 2008-07-25
I got it!!1  I downloaded the applets it was looking for out of the package manager, logged out, and back in again, and presto!!!  I dont know how that happened, but its good now!!  Thanks Fooman!!!

---

