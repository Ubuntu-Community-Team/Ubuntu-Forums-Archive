---
title: "Problem when boting up Intrepid Ibex"
date: 2008-11-17
forum: General Help
---

### Post by AlexisMclovin on 2008-11-17
I recently made the switch to the new upgrade, but every now and then i get a big X on my screen when booting it up. I run the recovery console, then select normal boot and it works fine. Anyone know what the problem is?

---

### Post by giuspen on 2008-11-17
> **AlexisMclovin said:**
> I recently made the switch to the new upgrade, but every now and then i get a big X on my screen when booting it up. I run the recovery console, then select normal boot and it works fine. Anyone know what the problem is?

I tried just once to do the upgrade and it failed, so will never do it anymore... better to do a new clear installation but do not format the home partition (where u keep all ur data).
the problem with the automatic upgrade is especially when u install packages from not official repository or from websites like getdeb.net... in this case the upgrade fails almost 100%.
regards.

---

### Post by MeURi on 2008-11-17
Hmm...

Alexis, could you be more detailed, please? For instance, does the big X come up after usplash? Or you see this X just after having chosen an option from GRUB?

Also, when this X happens, investigate the most recent log files placed in /var/log and search for warnings and errors, and post them here if you don't find a quick and simple solution.

I also prefer clean installs, but every problem should be fixable without using a Windows-like approach (format and reinstall). Correct me if I am wrong :-P

PS: I currently use Windows most of my time, so please don't take this a flaming post ;-)

---

### Post by AlexisMclovin on 2008-11-17
Sorry for the name misunderstanding. Im Alex is Mclovin lol. Anyway the X always seems to come before the Login screen. I sifted through the /var/log and i found no outstanding errors. Not that i really knew what all the .log files i was looking at were about. I always see GRUB loading on the installation but i dont really know what it is, so i dont think i have made any choices from there.

---

### Post by MeURi on 2008-11-18
First, sorry for the name misunderstanding :-)

Now, let's move on.

If you get the X before the login, it means that the system boots well, and there are problems starting the X session (maybe related to the display manager you use).

When you get the next X instead of the login screen, switch to another VC (Ctrl+Alt+F2 should be ok), login, check your *Xorg.0.log* under /var/log/ and look for lines beginning with (EE).

Maybe copy that file into your home directory and paste it here for investigation ;-)

Notes: GRUB is the bootloader used by Ubuntu and other Linux distros, you see it before the system actually boots; it's configured by default so it loads the kernel without the failsafe option, which is used for recovery instead of a normal boot.

---

### Post by AlexisMclovin on 2008-11-18
Alright so next time i get the X ill post the Xorg.0.log . Thanks

---

### Post by MeURi on 2008-11-18
You're welcome.

And, by the way, I hope I *can* be of some help :-P

---

### Post by AlexisMclovin on 2008-11-18
O.K i just got the X again and all i found that started with EE in the Xorg file was this

(EE) intel(0): underrun on pipe A!


it was on there multiple times right next to each other

---

### Post by MeURi on 2008-11-19
Googling around, I found some bugs on Bugzilla, mostly similar to yours. It's definitely a bug with the intel driver for Xorg, but no one solved it by tweaking his/her configuration.

Somewhere else (can't remember where, and can't find it in the browser history :oops:), I read that a user solved the issue by building the new unstable version of the driver from sources.

So, the new packaged version for Ubuntu should be the simplest solution.

Either way, you can build the driver by hand (and I can't be of much help, in this case :-P), grabbing the code from [here](http://intellinuxgraphics.org/download.html).

---

### Post by AlexisMclovin on 2008-11-22
oh nooo, no source building for me, but thanks for the help.

---

### Post by MeURi on 2008-11-22
You're welcome

---

