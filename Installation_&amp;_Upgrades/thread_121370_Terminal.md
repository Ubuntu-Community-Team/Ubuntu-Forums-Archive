---
title: "Terminal"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by suessw on 2006-01-25
Hello,

I would like to connect a terminal to the ubuntu system (like Wyse Terminal).
Would this work and which kind of terminal you recommened. 
Also are there different concentivity (serial or network)?

Thx

---

### Post by RavenOfOdin on 2006-01-25
Not quite sure, but I think Starnet XWin32 is supposed to connect to a *nix system from Windows.

---

### Post by d1337 on 2006-01-25
A google on "ltsp+wyse" brings some interesting results.  LTSP is the Linux Terminal Server Project.  A [link]("http://www.gutschke.com/wy60/") (specific to wyse60).  I'f I'd have thought that wyse was still an interest to someone, I would've hung on to the 10+ dummy terminals I had up until about a year ago.  The current move is towards diskless workstations, so wyse terminal hardware seems to be getting more scarce...one of the reasons I changed.  When we did use them, wiring was a beast...at least for the serial conectivity that we were using.  I have a digiboard with ethernet out, but I had to build custom serial ends (db12's ?) which was rather tedious.  If you get something going, I'd be willing to share whatever knowledge I've managed to hang onto as well as any schematics that I might still have.  Drop me a PM (I'll be out of pocket for the next week or so).

d1337

---

### Post by lees on 2006-01-28
Hi,

You could look a product like the ones offerd by at [www.equinox.com](www.equinox.com). Check the bus-based serial adapters. Basically its a card you put in a pci slot in you system and then you can hook 4-x number of serial termials to it depending upon the size of the card you select. You can use either rj11 or rs232 connections.

Our old legacy software at work ran on wyse emulation serial terminals and we used this hardware to support 128 serial terminals / printers from on sco unix server.

Lee

---

### Post by tattoo_wolf on 2006-04-01
[QUOTE=suessw]Hello,

I would like to connect a terminal to the ubuntu system (like Wyse Terminal).
Would this work and which kind of terminal you recommened. 
Also are there different concentivity (serial or network)?

Thx[/QUOTE]
Hi.. it is possible to do this.  I have a wyse 60 amber hooked into my box here.   make sure that you have your terminfo files loaded and in the \etc\inittab file put in

T0:23:respawn:/sbin/getty -L ttyS0 19200 vt100-s 

OR something like this

T0:23:respawn:/sbingetty -L ttyS0 19200 wy60

change ttyS0 to whatever serial port you have and then your term type.  I run the wyse term
for an ipfraf monitor so I can keep a quick check on some of the other puters on the network.

The only problem that I am having with it is I am used to using the old termcap entries not the terminfo ones.  If I try to run say MC on it it doesnt to the graphics right and I cant remember how to change it on this system yet.

---

### Post by internetauto on 2007-01-24
sorry to dredge up an old post.
But I need to do the EXACT opposite of this.
I need the linux box to emulate a Wyse 50 terminal connecting via an rs232 port.
I've doing it via Alphacom in windows, but windows I am trying to phase out.
Any help would be greatly appreciated.

---

