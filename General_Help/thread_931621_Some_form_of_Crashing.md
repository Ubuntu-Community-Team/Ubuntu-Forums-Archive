---
title: "Some form of Crashing?"
date: 2008-09-27
forum: General Help
---

### Post by LolItsGriff on 2008-09-27
It's been a while since I've actually had problems, but something has been happening for the last while.


Starting about 5 weeks ago, my computer's sound just started cutting out. Youtube Videos wouldn't load, Firefox would crash, Skype would say there was problem with Audio. I'd go to restart, and the menu wouldn't appear, Forcing me to use CTRL+ALT+BKSP. I've tried letting it run, And I've updated most of the software I've believed to may have caused it, to no avail.

Anyone have any idea? My system restarts particularly quickly.. but it's annoying nonetheless.

PS, I'm still a Real newbie at Linux. So if you have any tech terms or something, I'm gonna need directions. Thank you.

---

### Post by LolItsGriff on 2008-09-27
In the time it's taken to get 12 views, My comp has done this at least 10 times.


Thanks for the help.

---

### Post by Gondee on 2008-09-27
Do you have a sound card?
What version of firefox are you using?
Have you reinstalled non-free recently?
And last of all have you re-installed your sound drivers?

---

### Post by Brain-free on 2008-09-27
That's actually usual - if we 're talking about the same thing.

If every time you watch youtube, the video plays for two secs and then crashes, then I think I know a fix. Even if this isn't your case though, try it.

Change your sound output to ALSA (via System -> Preferences -> Sounds) and then go to Synaptic and check for the package "libflashsupport".

Do all the above if you have installed the "flashplugin-nonfree" package. If you haven't it's also in Synaptic

---

### Post by LolItsGriff on 2008-09-28
> **Brain-free said:**
> That's actually usual - if we 're talking about the same thing.

If every time you watch youtube, the video plays for two secs and then crashes, then I think I know a fix. Even if this isn't your case though, try it.

Change your sound output to ALSA (via System -> Preferences -> Sounds) and then go to Synaptic and check for the package "libflashsupport".

Do all the above if you have installed the "flashplugin-nonfree" package. If you haven't it's also in Synaptic

Yes, All my drivers are working, and I have my Sound Se to Alsa, with Flashplugin-nonfree installed.

Youtube doesn't just stop loading two seconds in- It starts playing with sound for a few videos, then crashes my whole computer. It will do this with ANYTHING That makes sound.


Shoot, Another edit: Oh yes, I don't think I mentioned: When this happens, I am prevented from opening Firefox/Any sound-using hardware, and trying to open menus just freeze the screen. I can't get the sysmonitor open, because it just dies immediately.



Oh yes, I have the latest Firefox ver. I think it's 3.0.3?

And yes, I'm assuming I do have a sound card as I got this computer as a Vista, and I doubt, with the price I paid for it, it wouldn't not have a sound card.

---

### Post by Brain-free on 2008-09-28
OK, I see. If it's a flash issue only - just to be sure, check if anything weird happens when you have both youtube videos and music player playing - the only thing I can think of is that you need the newest version of flashplugin-nonfree. It may still be in beta stage - hell, it's been for some months in beta stage! - but for me and many other guys in this forum is even more stable than the current one. Actually, it's the one I am using.

Also you can easily install it and revert back, the how-to is in [this guide]("http://tombuntu.com/index.php/2008/05/16/test-drive-flash-player-10-beta-in-ubuntu/").

Hopefully it works - as I have ran out of ideas....

---

