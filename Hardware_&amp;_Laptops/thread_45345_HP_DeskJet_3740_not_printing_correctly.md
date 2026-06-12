---
title: "HP DeskJet 3740 not printing correctly"
date: 2005-06-29
forum: Hardware &amp; Laptops
---

### Post by pgavin on 2005-06-29
Ok, so I just bought a cheapo HP DeskJet 3740, and it prints. The problem is that when I print anything through cups, it doesn't start printing until about an inch down the page, and the last inch or so gets cut off. It also looks like the output might be shifted right slightly. This only occurs if I'm printing in Letter mode; if I switch to A4 mode, it looks fine, except that (of course) I'm printing on paper that's a different size, so its trying to print on paper that isn't there.

The problem doesn't occur if I print a test page from hp-toolbox, only if I print through cups.

Can someone help me out? Thanks in advance for your help.

---

### Post by apollo2011 on 2005-06-29
Welcome to the forum pgavin!

I am not familiar with the CUPS interface in Gnome, sine I use KDE, but there should be several settings that might affect that...Have you tried looking through the page setup settings in CUPS?

---

### Post by apollo2011 on 2005-06-29
I just went into Gnome and looked at the setup for my printer.  Is Letter set in both the Paper settings and the Advanced settings tabs?

---

### Post by pgavin on 2005-06-29
[QUOTE=apollo2011]I just went into Gnome and looked at the setup for my printer.  Is Letter set in both the Paper settings and the Advanced settings tabs?[/QUOTE]

Well, it was... but now the printer has completely disappeared from CUPS. It shows up if I do hp-probe, but not in hp-toolbox... :/   Now I'm trying to figure out where it went.

---

### Post by pgavin on 2005-06-29
[QUOTE=pgavin]Well, it was... but now the printer has completely disappeared from CUPS. It shows up if I do hp-probe, but not in hp-toolbox... :/   Now I'm trying to figure out where it went.[/QUOTE]

Ok, well, I figured out what the problem there was... but I'm still getting the margin issues.

---

### Post by pgavin on 2005-06-29
Ok, so, its (mostly) working now.  The only problem I'm having now is that once a job gets finished, its not removed from the queue, it just sits there, even though its been reported as completed.

---

### Post by apollo2011 on 2005-07-06
sounds like a driver problem...

---

### Post by David Haas on 2005-07-08
What PPD file did you select for your Deskjet 3740? I see that Ubuntu Hoary contains  one for it: HP-DeskJet_3740-hpijs.ppd.gz. It's located in the HP directory at /usr/share/cups/model/foomatic-ppds/HP. Did you set up the printer with the Gnome printer manager, selecting the printer model and then the PPD file (driver) here?
David

---

