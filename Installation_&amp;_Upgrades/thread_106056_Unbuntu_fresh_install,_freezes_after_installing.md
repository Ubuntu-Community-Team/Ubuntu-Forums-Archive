---
title: "Unbuntu fresh install, freezes after installing"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by Tyfoo on 2005-12-19
Hi guys. Im a linux noob and ubuntu came highly recommended. Anyway I just installed ubuntu and it went through all the procedures, removed disk, started installing other packs from HD. Everything went well, infact it hit 100% then all of a sudden it just goes to a black screen with a command prompt dialog at top left but it wont let me type anyhting to do anything for that matter.

Im running 450 mghz celeron with nvidia geforce 4 mx and 500 megs of ram. Any ideas? I installed Slackware fine back in the day but decided not to keep it because i couldent install my wireless drivers on them. Thats another story, but for now I wish i could get this working. BTW I have not tried live install and infact i formatted everything so i would have to install windows again to retrieve all my files. PLZ HELP!

EDIT: When I reboot, it brings up a ubuntu screen and brings up a lot of loading dialogs so it seems as if its installed. After just 2 minutes of it loading the files, it comes up with the black screen i was speaking about.

---

### Post by 23meg on 2005-12-19
Maybe you should switch to the vesa driver instead of nv to get your video card working. Can you boot into recovery mode? If so, enter ```
nano /etc/X11/xorg.conf
``` to modify the "Driver" line in the "Device" section of your /etc/X11/xorg.conf file to "vesa" and reboot.

---

