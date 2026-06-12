---
title: "Console switching, log-out, or killing X server results in black screen! GDM problem?"
date: 2005-11-20
forum: General Help
---

### Post by treanus on 2005-11-20
Hello All,

just performed a fresh install of  my pc of which VGA card is an ATI radeon X700.
The install did not configure X, since X700 is not supported.
Used the ubuntu forums howto for ATI X700 support and now X WORKS fine. X is now up and running.

Have 1 problem though:
Console switching (ctrl-alt-F1), log-out, or killing X server (ctrl-alt-backspace) results in a black screen, i.e. my lcd screen goes into power-save mode (LCD says "no input signal"). Nothing works, I cannot get back to X with ctrl-alt-f7. Only thing I can do is to reboot with crtl-alt-del.

Perhaps this has to do with GDM? GDM was diabled by the install since X did not start during install...

HELP please!

---

### Post by bulldogzerofive on 2005-11-21
It is not GDM it is X.

I think you are SOL on this one unless your card is less than a year old.  I had the same issue with the same card in KDE and Gnome, under Mandrake, Debian, and Ubuntu and was never able to narrow the causes down any further than the fact that X and the card did not get along and that the problem has something to do with memory allocation.  I only fixed it when i bought a NVIDIA card.

The sad fact is, the card is just not supported.  You can try a few things:  1.  Look for a new driver for the card (maybe one has been released since i messed with it)
2.  Search the forums for "Howto configure X" and follow the thread to try to configure X by hand
3.  Add more memory.  I noticed that a side effect of adding memory was that the black screen happened much less frequently, although it still happened on occasion. 
4.  Try some very memory-lite desktop managers, like xfce.  I think this is your best bet other than:
5.  Buy a new card that is supported.

Sorry, but it does suck.  I feel your pain.

---

### Post by sal on 2005-11-21
i have this same problem with the gdm on a ctrl-alt-backspace.

i posted about it here:
[http://ubuntuforums.org/showthread.php?t=92508](http://ubuntuforums.org/showthread.php?t=92508)

i think it is the GDM because i thought when it was happening to switch back to the kde desktop with the KDM and lo and behold when i do a ctrl-alt-backspace,
i am returned to the KDM.

---

### Post by bulldogzerofive on 2005-11-22
We may be talking about different problems.  In my case i am sure it was X... that was the only common factor in all the installs that i did.

Edit:  Also, it completely locks the system; i cannot go into another terminal and restart gdm or kdm or anything.  Moot now; i have a new card and it does not happen.

---

### Post by jimchristopher on 2005-12-27
same problem here with a X800XL and a Shuttle SN25p

---

### Post by jimchristopher on 2005-12-31
I swapped out my radeon X800XL for a friends nv 6600GT and now everything video related works great!  def sounds like a bug/feature of the ATI/fglrx driver

---

### Post by Irony on 2005-12-31
Similar thing here though I think it is related to my monitor.

On my old monitor when I shutdown text would scroll by informing me of the shutdown process.

With my new monitor I had to alter the xorg.conf file to get full screen resolution - but now I shutdown and I get a blank screen and power save mode led. Similarly Ctrl+Alt+Fn gives a blank screen and power save mode led - I have to do a hard reboot.

I wonder if its related to specifying resolutions in console - how does console know what resolution to use?

---

