---
title: "Updated gfx drivers, system will not boot now"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by jr2 on 2009-07-26
Hi,
I have been using ubuntu 9.04 x64 for a few months now, and just tried to update the drivers for my laptop's ATI Radeon HD 3200 card.  I downloaded the .run file from AMD, and put:
sudo ./<atidriverfile>.run

It came up with a dialog box, I installed the driver, and it closed saying it was going to do some basic configuration or somesuch.  Well, nothing came up after I closed the dialog box.  So I clicked "Display" from the appearance menu - ubuntu asked me if I wanted to use the ATI config utility, I hit "yes".  As soon as I hit that, the (XWindow client?) disappeared and was replaced by a bunch of text.  Great.  So I forced the computer to turn off, started it back up.  Now it boots to a blank screen.  Oook... so i boot the next most recent kernel in the list (the .11 one, current is .13 IIRC).. same thing.  So I boot the .13 in recovery mode and select "try to automatically fix graphics problems"; it said it was going to reset a possible custom configuration, I told it to go ahead... then tried booting - it now displays weird little blue lines at the top of the screen.  I tried using recovery mode and telling it to "fix broken packages (dpkg)" - it removes 4 obsolete packages and still displays blue lines.

Should I start in command-line mode and re-install the ati drivers?  I actually don't quite know what's going on.  But I am stuck booting Vista until I fix it.  Any help appreciated.

---

### Post by jr2 on 2009-08-08
:dustbunnies:

---

