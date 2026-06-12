---
title: "Please help: Need to preserve websites between install"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by Darkmoon_UK on 2009-02-24
Hello,
I ran a Edgy box for many months, as a general purpose server, and last night decided to upgrade distro to 8.10. Deciding to take the route through all the intervening versions for safety (ha ha) the first hurdle I encountered was the repositories being moved from **archive** to **old-releases**. So, with sources.list set to feisty on the old-releases server, I did:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```
My first run of **update** reported some truncated BZip2 files, but subsequent runs didn't report this, so I forged ahead with the **dist-upgrade**. Cue 2 hours process of downloading and performing package replacements; which then stopped on a problem with **scim-bridge**. Restarting the box resulted in a completely dead machine with a black screen after the very initial boot. Great... I'm not going to moan too much as Edgy is obviously quite an old distribution and I'd left it a long time. But it does look as though something in the repositories was broken - and the GUI upgrade tool was certainly out of the question, as is well documented. Couldn't Ubuntu Team be more careful to preserve the upgrade path?
**My main concern now**, is to be able to reinstall to the latest version 8.10 while preserving the websites and other data that exist on the machine (basically the AMP configuration). Will a standard install-over-the-top take care of this? Otherwise, what particular locations should I back up and restore onto the fresh box?
Thank you very much for any help, I love Ubuntu but times like this can be trying for a wet-behind-the-ears Linux explorer like myself...

---

### Post by laithbsoul on 2009-02-24
I'd say just install a fresh 8.10

---

### Post by Darkmoon_UK on 2009-02-24
Agreed but your post doesn't address the main concern of retaining my websites - specifically, the Apache Config, mySQL databases and PHP settings. Will these survive a standard 8.10 install process? Sorry if this seems obvious to you but I can't afford to try it out only to be wrong...

---

