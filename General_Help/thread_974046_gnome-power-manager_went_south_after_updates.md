---
title: "gnome-power-manager went south after updates"
date: 2008-11-07
forum: General Help
---

### Post by SamNSane on 2008-11-07
Ubuntu 8.10 with backports repository enabled running on Panasonic CF-R3 subnotebook.

I installed updates via Update Manager and, since then, the gnome-power-manager applet has been crazy. I was used to setting it to hang out in the notification area. But suddenly I was getting only two tabs on it (as though the computer wasn't a laptop), and I was getting an application popup from Ubuntu when I tried to shut down telling me that gnome-power-manager was still running. Sometimes I would click on the shutdown symbol and would get a truncated list which gave me no choice for shutting down -- only logging out or switching users. The system even became unresponsive (I could move the mouse, but clicking on selections did nothing. System was unresponsive to keyboard input, too.), forcing me to perform a hard shutdown.

I was finally able to get enough cooperation from the system to tell it to be visible in the notification area only when battery was critically low, and I haven't had problems with it (yet) since then.

Has anyone else seen this sort of behavior?

---

### Post by DigitalRonin on 2008-11-08
I've got similar issues with my Panasonic CF-R4.

When I had just installed Ibex, the power management seemed to be fine - sleep when I close the screen, wake when I open it. But, sometime after that it got weird. Now, when I try to choose power management via the menu, it often seems to try to start the applet but then give up after 10 seconds or so. Later, as you said, it says that gnome-power-management is still running when I try to logout/shutdown manually.

If I ever do get the power management applet running, it doesn't have the right options for a laptop.

The power management stuff was the big win for me when I went from Gutsy to Hardy - it just worked. This, and an issue with the SD card reader, are problems that have only cropped up since Intrepid (although I can now dual-head with an external monitor, which is sweet).

David

---

### Post by SamNSane on 2008-11-08
Yes, I'm thinking it's a system-specific drivers issue -- the worst kind for us end users. The fact that a couple of Panasonic CF-R# users are -- so far as I've been able to find -- the only people complaining about this issue may be an indicator.

I'd like to try to figure out whether or not the trouble starts with a particular set of updates. As I said, I have the backports repository enabled in addition to recommended and important security. But I don't have proposed enabled -- since it's the only one of the repositories in the standard synaptic software sources repository lists that I've really seen cause trouble.

I believe my problem started with updates from a couple of days ago. I'm not sure which repository they came from. I've become pretty lazy about checking, and the update-manager has stopped showing any interesting information about updates.

If we can get some kind of decent feel for when and why the problem started I'd feel better about filing a bug report.

---

### Post by SamNSane on 2008-11-11
With this much basic functionality broken on the CF-R3, and other basic functionaltiy broken on another system, I went back to 8.04 LTS. Everything (except nVidia restricted drivers, of course) works just fine now.

---

