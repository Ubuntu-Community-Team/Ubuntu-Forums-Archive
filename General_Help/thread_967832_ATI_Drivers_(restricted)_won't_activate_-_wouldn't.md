---
title: "ATI Drivers (restricted) won't activate - wouldn't in hardy either."
date: 2008-11-02
forum: General Help
---

### Post by nappymonster on 2008-11-02
I've been dual booting ubuntu for sometime now, and remember it was a pain in gusty to set up my screen resolution, though eventually I got it running at 1280X800. About 5 days ago I upgraded to hardy (a little late, i know), and it couldn't install the restricted drivers. Same thing in Ibex.

In system>>Administration>>Hardware Drivers, an ATI graphics driver shows up, but when i click activate, type my password, then it flashes up the box but closes again at 0%.

Any help would be appreciated!

Thanks,
Nappymonster

EDIT: For the second time in about 20 mins (updated 20 mins ago), the system has logged me off unexpectedly...

Any ideas?
Thanks.

---

### Post by oldHat on 2008-11-02
If you are really stuck, ENVY might possibly be the answer.  I'm not on ATI, so my situation is a bit different.

I'm on nvidia, and have always had trouble getting the restricted video drivers to install properly.  In desperation, I keep resorting to envy (now known as envyng).  

It supports both ati and nvidia and it usually gets the job done for me.  It will check your dependencies, grab the latest drivers from the manufacturer's site, compile new kernel modules, and install them.

I don't want to sound like I know more than I do.  I wouldn't be able to back you up if you run into problems.  Research it and decide for yourself.  There should be lots of info on the forums.  The package is available via synaptic/apt-get; you'd probably need the core and the gui; be sure to read the properties data on synaptic for each package.  It will give you a list of drivers to choose from; be sure to choose something that is recommended and compatible.

---

