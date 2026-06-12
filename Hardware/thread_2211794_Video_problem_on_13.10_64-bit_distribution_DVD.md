---
title: "Video problem on 13.10 64-bit distribution DVD"
date: 2014-03-17
forum: Hardware
---

### Post by pwabrahams on 2014-03-17
I'm trying to use the "try Kubuntu" option on the distribution DVD for 13.10 to solve a problem ("Gave up waiting for root device") in an existing system.  When I choose the Try option on the DVD, I get the usual screen with a window for Try and Install.  The trouble is that this is all I get.  No taskbar (or whatever it's called) at the bottom of the screen, just a small empty box in the lower left corner.  I suspect some video problem, but I can't get at any tools to investigate it, at least not on the system that's acting up.  I can get into a console, so I do have the command line available.   Is there anything I can do?

---

### Post by Yellow Pasque on 2014-03-18
It might help to tell people what kind of system you have. Huge bonus points will be awarded if you can tell people what GPU you have ;)

---

### Post by SeijiSensei on 2014-03-18
When you click the "Try" button, what happens?  It should launch you into the default Kubuntu desktop.

---

### Post by pwabrahams on 2014-03-18
I'm working with a homebrew system with a 4-core Pentium processor (probably not relevant) and an Nvidia GEForce 7025/nForce 630a graphic processor.  NVidia graphics are known to be problematic; the driver recommendations seem to be constantly changing.  I understand that the sequence ```

sudo add-apt repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331

``` 
is supposed to fix problems with nVidia cards.  The problem I have in the 13.10 installation is that I never have the opportunity to get to a command-line window where I can issue these commands.  There's no chance to do that during the installation itself.  When the system is restarted it gets to the blue screen with four large symbols (as it sshould) and then hangs with a screen of graphics gibberish.  It's really hung, since even CapsLock doesn't work (and neither does Alt-Ctl-F1).  So assuming this fix works, how can I get to apply it?

---

### Post by pwabrahams on 2014-03-18
The Try button does that, but the desktop I get has the same video problems I encounter with installation.

---

### Post by Yellow Pasque on 2014-03-19
Have you tried adding 'nomodeset' to the boot line?

Also note that you do not want nvidia-331 package. The Geforce 6000/7000 series chips are supported by the nvidia-304 branch.

---

### Post by pwabrahams on 2014-03-19
I tried nvidia-304 and got nowhere.  But at least I was able to maneuver my way to a virtual terminal and update with nvidia-331.  And that worked -- at least for me.

We live in a world of wizards with competing spells and incantations, it seems.

---

