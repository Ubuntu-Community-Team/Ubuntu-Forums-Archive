---
title: "Keyboard and mouse stop responding during install"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by ChickenDuck on 2009-04-10
I have a new Acer Aspire M4361 and I am attemting to install Ubuntu.  I've downloaded the 8.10 ISO and can boot from the resulting CD.  The first prompt asks if I would like to "Install without changing my system," "Install" and a few other options.

At this point, I am able to use keyboard keys to cursor through the selection and choose "Install".  Ubuntu then loads from the CD.  The progress bar moves along, and eventually a screen comes up where I am supposed to select a language for the install.  (I seem to recall it says this is step 1 of 7).

The problem is, at this point the mouse and keyboard do not respond.  I have now tried 3 keyboards and mice: a wired USB set, a wireless USB set, and an old PS2 style serial set.  All do the exact same thing.

It's very strange because all 3 keyboards work to select the first option (Install) but are dead by the time I am next prompted to do something.  None of the mice ever appear to do anything, even if I jiggle them as soon as I see a mouse cursor during the boot screen.

Perhaps the system is hung at this point - but I can't think of any way to test that.  I'm a linux newbie so maybe there's a way I don't know of.

I spent some time searching but could not find anything like this.  I must be doing something wrong but I can't figure out what since I really haven't done much of anything at this point.  Maybe my new computer is not compatible with Ubuntu?  Any advice or ideas is appreciated.

---

### Post by tlois on 2009-04-10
Is the number on that Acer correct?

---

### Post by ChickenDuck on 2009-04-10
Oops, no.  It is an Acer M3641.

---

### Post by ChickenDuck on 2009-04-10
One more recent observation that might be a clue.  I've retried this several times to see if I can get any different results, but nothing concrete yet.  However, in one instance after the initial "Install" selection was made, a text screen came up and the boot seemed stalled.  This screen displayed the status of several daemons and processes that had started (please forgive my ignorance of what most of it meant since I'm new to linux).  A system logger had started, a kernel logger and a few others had started with an [Ok] over on the right edge of the screen.  It looked to be hung trying to start something to do with Bluetooth.  There was no [Ok] on that line.  I waited a couple of minutes but then had to press & hold the power button to get it to restart.

This computer does not have any Bluetooth capability, so maybe something is getting hung up there?  Is there any way to step through the initialization process to see if something is going wrong?  Also, is there any way to get at any of the system log or kernel log?  I don't suppose that debug information shoots out the com port or something like that?  I have another computer and a null modem cable I could check it out with.

---

### Post by ChickenDuck on 2009-04-10
It does appear to be something with Bluetooth.  I tried installing Ubuntu using the wubi.exe in Windows Vista.  The installer ran OK and told me to reboot.  There is now a boot option for either Vista or Ubuntu. When I select Ubuntu, it hangs every time trying to do something with Bluetooth.  Again, this computer does not have any Bluetooth capability.  I've attached a "screen shot" of the status screen I get when it freezes.

Update: when I boot in verbose mode, while starting Bluetooth I get the message 

pan0: Dropping NETIF_F_UF0 since no NETIF_F_HW_CSUM feature.

Any hints?

---

### Post by ChickenDuck on 2009-04-10
OK, I have managed to solve this problem.  Unfortunately I cannot document exactly what I did, because when I finally got the system to boot it overwrote the file I edited, but here is what I remember:

1) I ran the wubi.exe program to install to a file under Vista.
2) After rebooting into Vista, I browsed through the files that were created and found a folder called "boot" which had a text file (forget the name - something ending in.lst I believe) that had options for different kinds of boots.
3) I created a new option based on the verbose boot and added "acpi=off" at the very end of the kernel line.  This was a shot in the dark for me but I came across a suggestion to try that by googling around for this problem.
4) Rebooted into ubuntu.  The installer ran this time and now I am up & running.

Hope this helps anyone else who has similar problems.

---

