---
title: "After Upgrade: Evince and Panel buggy, VBox useless, Amarok 2 &amp; Tracker don't work"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by asdir on 2009-04-25
As you can see from my title, I had quite a few problems with the upgrade and I have to admit, I am really dissappointed.

First of, I cannot listen to music with **Amarok 2**, probably because it is too buggy to be used anyway. I deinstalled a slightly earlier version just a few weeks ago because of that. To be more specific: When I click play or double-click a track, nothing happens, not even the pop-up display shows up.
My only question here would be: How do I safely downgrade to 1.4, as it isn't in the reps anymore?

As for the **VirtualBox**: I had problems after the last regular upgrade to the nvidia driver all along. Now Win XP will start as normal and log me in, even let me see the desktop for a few seconds, then reboots and keeps doing that until after the 5th or so reboot when it finally shows a BSOD, moaning about a problem with nwrdr.sys. What is the problem here and how do I fix it? It would be nice if someone could confirm that switching drivers again would help, since I am a bit reluctant to switch back. Last time I did that, I was back to the CLI.

Every time I reboot the **Icons in the panel** reorder themselves, creating a mess. I made sure that all of them are locked. It does not help. Is that a bug? If so, I could not find anything on Launchpad.

Moreover, **Evince** only seems to recognize the first page of any given pdf-file (I tried a few that worked vefore). The scroll-bar on the right also seems to know only that particular page. Only when I use PageUp/PageDown will it let me go to the next page. Again: I found no bug on Launchpad. Am I missing sth. or should that seriously be posted there?

As for **Tracker**: I guess it fits [this bug]("https://bugs.launchpad.net/ubuntu/jaunty/+source/tracker/+bug/346912").

If there is any advice on this, and if it is only a confirmation so I can compile a useful bug report, please let me know.

Thanks

---

### Post by Frostek on 2009-04-25
I'd certainly agree with your comments concerning Amarok 2. I would have prefered to stick with the version from Ibex until it was subject to less crashing.

Annoyingly, I can't use it at all. It says my soundcard (an old, but reliable Soundblaster Live! Platinum CT4760P) isn't recognised. Everything else in KDE and Gnome works fine with it though!:confused:

---

### Post by asdir on 2009-04-27
As for **Evince**: The update seems to have unchecked the fifth option under view. So, this is neither any major nor a bug. However, it is annoying that an update sets your configs back or sets them differently than before.

As for the **icons**: For some reason order came back. Strange but ok. Still: It should not have happened.

---

