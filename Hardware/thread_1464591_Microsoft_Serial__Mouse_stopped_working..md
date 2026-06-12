---
title: "Microsoft Serial  Mouse stopped working."
date: 2010-04-28
forum: Hardware
---

### Post by oldspammer on 2010-04-28
[SIZE=2]During tax season, I fire up an old computer with which I do my taxes.[/SIZE]
 
[SIZE=2]I have more computers than computer mice, so I borrowed the Microsoft Serial Mouse (with wheel) from my Ubuntu 9.10 Linux computer for a week or more during the tax preparation sessions.[/SIZE]
 
[SIZE=2]Some software within the Linux box decided upon its own initiative to remove the Microsoft serial mouse from both the character based, and GUI based environments settings files.[/SIZE]
 
[SIZE=2]Searching Google for the answer did me no good because the software designers seem to change how the configuration is performed on a frequent enough basis to invalidate prior years or months methods of correction of this mouse disappearing.[/SIZE]
 
[SIZE=2]However, these methods of correction would be unnecessary if the system's software itself did not self-update its own configuration without the permission of the super user (me).[/SIZE]
 
[SIZE=2]I have now 3 mice attached to this system: MS Serial wheel mouse, MS PS/2 wheel mouse, and a USB Logitech Laser wheel mouse with lots of buttons.[/SIZE]
 
[SIZE=2]So, now I need to know both the current method of undoing this harm, and a way to prevent it from happening in future for all other users by stopping the system itself from modifying its configuration settings without super user (password protected) permission given to it for such permanent hardware reconfiguration changes (that should probably, by default not be granted due to foolishness that this would cause) that are not automatically and completely undone when the same hardware is plugged back in again (and never redetected possibly because of multiple mice being used?).[/SIZE]
 
[SIZE=2]After installation, multiple mice work fine. How do I recover to this initial state of bliss for each new version / edition / flavour of Linux, and how do I prevent it from ever getting undone?[/SIZE]

[SIZE=2]There are several grep keyword strings that could be used: mouse, input, pointer, pointing, and so on which seem to change from one year to the next and thereby are inconsistent between flavours and releases of Linux.[/SIZE]

[SIZE=2]So, starting with a find command within /etc, what keywords and methods would generally work to identify which config files to modify for both character screen terminals, and X windows to get the mouse back working? This should ideally universally work for all versions of Linux regardless if from the 1990s or more recently...[/SIZE]

[SIZE=2]And what mechanism can be put into place to prevent this automatic reconfiguration (damage) from happening.[/SIZE]

---

### Post by oldspammer on 2010-04-28
The first thing that I tried was to unplug my MS PS/2 wheel mouse, but this quickly resulted in my having no mouse functionality at all.

I had to quickly grab my Logitech USB wheel mouse and plug that in to recover any useful GUI functionality.

I seem to recall that mdetect reports when my MS PS/2 wheel mouse is unplugged that it is my mouse which does not make a lot of sense?

---

### Post by oldspammer on 2010-04-28
I found this thread by sifting through the search results of >serial mouse< ...

[http://ubuntuforums.org/showthread.php?t=1331499&highlight=serial+mouse](http://ubuntuforums.org/showthread.php?t=1331499&highlight=serial+mouse)

I don't know, however, how to prevent the removal of the mouse from the configuration files?

---

