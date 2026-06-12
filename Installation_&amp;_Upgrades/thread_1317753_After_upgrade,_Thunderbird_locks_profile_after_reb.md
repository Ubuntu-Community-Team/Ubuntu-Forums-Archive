---
title: "After upgrade, Thunderbird locks profile after reboot"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by timpreza on 2009-11-07
After upgrading to Karmic Koala, my Thunderbird is severely broken.  After rebooting my computer Thunderbird will not start and gives me the error message "Thunderbird is already running, but is not responding..."  I've deleted the .parentlock file in the profile folder, I've renamed the profile folder and edited profiles.ini, I even removed and reinstalled Thunderbird.  I've tried anything I can think of to no avail. No matter what I do I can't get Thunderbird to open my profile after rebooting.  The only thing that fixes the problem is is creating a brand new profile and copying the old profile into the new folder.  Needless to say it is very inconvenient to create a new profile and copy everything over every time I reboot my machine.  Any ideas on what to try next to fix the problem?  I've searched high and low for a fix and am at wits end.  ](*,)

Perhaps applicable information:
My profile is on a network drive in order to share with another computer.
This setup worked flawlessly until I upgraded to Karmic Koala
Thunderbird doesn't delete the .parentlock file when it's closed (is it supposed to?)
The .parentlock file has a timestamp approximately 35 minutes in the future (what's up with that?)
I've used Ubuntu since Hardy Heron.

Thanks
-Tim

---

### Post by timpreza on 2010-01-06
OK, so I reinstalled Karmic and that took care of the problem for a while.  Unfortunately the same problem has cropped up again.  Every time I reboot my computer, Thunderbird (2.0) refuses to open my profile, even after removing .parentlock.  I have a spare computer that has Jaunty installed and it opens the profile every time, and if I wait a couple days, sometimes my main computer will open the profile again. What else, besides the .parentlock file would cause Thunderbird think another process is running?  What about Thunderbird causes time sensitivity to opening a profile?  I am trying to avoid another Ubuntu re-installation (that will not be Karmic).  I've tried removing, purging, and re-installing Thunderbird, but am out of ideas.  Anybody?

---

### Post by kansasnoob on 2010-01-06
Maybe try version 3.0 using Ubuntuzilla:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)

If you have more questions about Ubuntuzilla they have their own section here at the forums:

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

---

### Post by timpreza on 2010-01-06
Thanks Kansasnoob.  I actually did install Thunderbird 3.0.  It currently refuses to remember any of my passwords, which is highly inconvenient as well.  However it did open the profile.  I'm still trying to fix either one.  I guess I'll use whichever I can mange to fix first.

---

### Post by m0o on 2010-01-07
Use the create new profile option, but when you create a new profile make sure you click on "Choose Folder" button and direct it to your old profile folder.

---

