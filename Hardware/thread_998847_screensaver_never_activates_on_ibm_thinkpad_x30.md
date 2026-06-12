---
title: "screensaver never activates on ibm thinkpad x30"
date: 2008-12-01
forum: Hardware
---

### Post by elliah on 2008-12-01
i've searched around a bit and found these 2 posts [http://ubuntuforums.org/showthread.php?t=621882](http://ubuntuforums.org/showthread.php?t=621882)
[http://ubuntuforums.org/showthread.php?t=52067&highlight=ibm+thinkpad+x30](http://ubuntuforums.org/showthread.php?t=52067&highlight=ibm+thinkpad+x30)

however, after i edited xorg.conf to that of the one in the second post, xubuntu wouldn't even run (restored it with a backup)
is there anyway to fix this?

---

### Post by seren6ipity on 2008-12-01
I figured that xubuntu does not come installed with **xscreensaver** which triggers the screensaver.
On terminal type - 
sudo apt-get install xscreensaver

After install is complete. On terminal
xscreensaver <- This will bring up a menu. Click on Settings

1. Set your screensaver preferences here. Set Mode and Time.
(the preferences on Settings-> Settings Manager -> Screensaver will not be considered)

2. Select Screensaver from the list

3. Go to file -> Restart Daemon

4. Quit

Your screensaver will be activated after set time.

---

