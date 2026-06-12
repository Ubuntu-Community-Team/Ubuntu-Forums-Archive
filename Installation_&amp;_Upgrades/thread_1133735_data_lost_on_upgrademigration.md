---
title: "data lost on upgrade/migration"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by nulall on 2009-04-23
Long story short, I just recently backed up all of my data, reinstalled Ubuntu (switch from 64-bit Intrepid to 32-bit Jaunty) and then copied back my home directory.
Some things seem to have transferred (overall desktop environment looks the same so nautilus and metacity settings seem to have copied, firefox is laid out the same way with my custom button scheme...), but some things haven't.  Specifically, the things I am having trouble with so far are that ALL of my pidgin settings/logs are gone, and my firefox extensions/userscripts seem to require a reinstall.
So, which things are due to the architecture shift from 64 to 32 bit, and where should I look to try to get back some of this data (specifically, it would be nice to get my chat logs back)?

thanks,
neil

---

### Post by Sam Lars on 2009-04-24
The Pidgin settings are in .purple... and unless that changed between your installations or something, they should have been as simple as your other settings.
Firefox extensions may be a different story.  You can check in the .mozilla/firefox folder to see if it created a new profile folder instead of using your old one.

---

