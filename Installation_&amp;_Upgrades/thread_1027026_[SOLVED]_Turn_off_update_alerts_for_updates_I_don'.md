---
title: "[SOLVED] Turn off update alerts for updates I don't want?"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by xarte on 2008-12-31
Daft question time.

since I've downloaded an awful lot of software, updates, distros and patches this month, I'm trying to minimize any extra download activity. 

Ubuntu (in both 8.04 and 8.10) keeps making little red alert signs in the toolbar telling me that I need to update. Some of the stuff I DO want - but some - like help files for openoffice - I don't. It's annoying having to unselect them each time.

Is there some way to configure the updater?

---

### Post by secondstage on 2009-01-01
To my knowledge, you change a couple settings, but not specifics. Go to System > Administration > Software Sources, and click on the Updates tab. This is where most of the settings are. You can change when to check for updates, whether or not you want a notification for distro upgrades, etc.

If you plan to change the setting for this month only, I would make sure to write the setting down, so that you can change them back later on.

---

### Post by xarte on 2009-01-01
Ah, thanks. I'll check that. I'm running Mint today, it is a little different. (though very similar).

I guess the degree of control I've got over software with Linux is pretty good - I probably shouldn't quibble over the odd few kbs of help files or whatever. It does seem that 'user friendliness' seems to end up equating to 'software bloat' though.

---

### Post by secondstage on 2009-01-01
Yes. That is very true. Just yesterday, I had to sit down, and clean up my computer from programs that were long forgotten, or only used once, and from the mess of a home directory I had created. 

Would you mark this thread as solved for others? To mark it, click "Thread Tools", and choose something about "Mark as Solved".

---

### Post by Shazaam on 2009-01-01
Open Synaptic. At the bottom left click "Status". Above that you will see a list, highlight "Installed (upgradeable)". Highlight each of the the update(s) you don't want, then go to "Package" and check off "Lock version" for each one.
In the future if you want them re-checked do the reverse.

---

