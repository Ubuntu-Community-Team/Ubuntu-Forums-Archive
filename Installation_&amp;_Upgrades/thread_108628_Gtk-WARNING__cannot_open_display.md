---
title: "Gtk-WARNING **: cannot open display:"
date: 2005-12-26
forum: Installation &amp; Upgrades
---

### Post by Scribe_05 on 2005-12-26
I have done a new install, ie I haven't yet had time to mess anything up, and I get this message when I try to edit Files.

I am the only User and have only set up one Password, so there should be no Security issues.

Would anyone have any idea as to how I can resolve this. :confused:

---

### Post by mijohnst on 2005-12-26
I was just about to post this exact same problem.  I also have a completely new install and anytime I try to open any GUI from a remote location or or even as root I get your same error.

```

(gksu:7642): Gtk-WARNING **: cannot open display:

```

I've tried the following, which did not help....

```

xhost +
xhost +hostname
xhost +localhost
set export DISPLAY=LOCALHOST:0.0

```

I've also made sure there is "X11Forwarding" in my sshd_conf file.  It's kind of a pain in the butt and since I've installed Ubuntu I've sent most of my time just trying to figure out this one problem...

---

### Post by kaamos on 2005-12-26
[QUOTE=mijohnst]I was just about to post this exact same problem.  I also have a completely new install and anytime I try to open any GUI from a remote location or or even as root I get your same error.[/QUOTE]
When you are on a remote connection you also have to enable x11 forwarding on the machine where you are making the connection from. And if the machine does not use X you need a program to handle X windows.

Hope I'm not stating the obvious here.

---

