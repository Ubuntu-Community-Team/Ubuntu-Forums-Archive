---
title: "Laptop Sleeping Partway?"
date: 2008-07-14
forum: General Help
---

### Post by MadeTheSwitch on 2008-07-14
This is a followup to [my post from yesterday]("http://ubuntuforums.org/showthread.php?t=858306").

System: Lenovo x61s
OS: Ubuntu Hardy Heron

**Revised problem description**: 

Sometimes, when trying to suspend my laptop, instead of finishing the suspend process, the laptop will "crash" into text mode. The sleep light will begin (and never stop) blinking, the GUI will disappear. 

What I found today by playing around is that if I press CTRL-ALT-F6 (specifically), I will get back to a running GUI, can log in back to the desktop, etc. HOWEVER, certain actions will fail - specifically, any action that requires SUDO, such as shutdown or restart. What happens when I try one of those is that the machine starts the shutdown process, then hangs with a blank screen and cursor blinking in the top left. 

At that point the keyboard can still be used to issue REISUB, for example, but the B fails; I can switch to a console (say by pressing CTRL-ALT-F1) but typing anything does not register on the screen.

Note that the sleep light is blinking the entire time. 

It seems like the OS is caught in a "zombie" state - half sleeping half awake. I have on idea where to look. Anyone have any ideas?

---

