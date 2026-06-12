---
title: "nvidia-settings"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by Cresho on 2007-05-13
Hi all!

I am having problems with my nvidia settings.  My situation is when I set the values to the nvidia-settings for antialiasing and anisotrphic filter, they work just fine even for games and desktop when using beryl.  Now my real problem is when after a reboot, the settings are reset to default.  Is there any way to make the changes permanently?

---

### Post by Cresho on 2007-05-14
hmm-no luck yet

---

### Post by Cresho on 2007-05-14
hmm.  I found a few commands which work pretty good so when I launch ubuntu, beryl has antialiasing and anisotrphic filter enabled automatically at launch.  I can't remember where i got the info but thanks goes to that person.

here is the info.......works best for nvidia!

open up "nvidia-settings"

and then in the "Antialiasing Settings" set them to however you want them

and then before you start beryl you must activate the nvidia-settings.....

to do that go into the terminal and type

Code:
sudo gedit /usr/bin/beauty


which will open up an empty text document

put this into it

Code:
#! /bin/bash
nvidia-settings -l && sleep 2 && beryl-manager


and then in the terminal again, type

Code:
sudo chmod +x /usr/bin/beauty


which makes it executable
and then in the terminal still
Code:
gnome-session-properties


and go to the startup programs tab and replace the entry you use to start beryl with "/usr/bin/beauty" (this is assuming you use gnome, i'm unsure how things are defined to start at startup in kde Very Happy)

and then the last step, which i didn't know about for a very long time (and so didn't have antialiasing for a very long time) is if you use blur, you must make it non-FBO (in the bsm, under blur, there is an option to force non-FBO

Here is the original link
[http://forum.beryl-project.org/viewtopic.php?f=39&t=2433&start=0](http://forum.beryl-project.org/viewtopic.php?f=39&t=2433&start=0)


option 2 is to

startup sequence to run "nvidia-settings -l" before beryl - this will turn on the settings and can be setup in System->Preferences->Sessions

option 3 is here

[http://forum.beryl-project.org/viewtopic.php?f=44&t=5320](http://forum.beryl-project.org/viewtopic.php?f=44&t=5320)

---

