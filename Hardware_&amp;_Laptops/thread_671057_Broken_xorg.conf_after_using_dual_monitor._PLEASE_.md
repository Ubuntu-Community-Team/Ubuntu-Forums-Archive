---
title: "Broken xorg.conf after using dual monitor. PLEASE HELP!"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by yesint on 2008-01-18
Dear All,
Today I tried to connect my laptop with Ubuntu 7.10 to the beamer. I set up the second screen with the "mirror default screen" option and it works just fine. However after that I can't switch the screen resolution back to 1280x800. "Screen and Graphics preferences" just doesn't start showing some python errors. The xorg.conf is messed up completely and the screen is 640x480.
Our local "expert" suggested to just delete xorg.conf and reboot. I did this. The screen is back to 1280x800 now, but compiz is broken completely now ans screen settings show complte mess. 
What can I do to restore my system? I'm really sick of thinking about reinstall...

---

### Post by glennzo on 2008-01-18
See if there's a file called xorg.conf~ in the /etc/X11 folder. It's a backup of the last edit, assuming everything was working correctly at that point, restore it as xorg.conf.

---

### Post by Yellow Pasque on 2008-01-18
If you want help with xorg.conf, then post what you have.

---

### Post by perixx on 2008-01-18
You might - or might not - be able to recover from that mess with: ```
sudo dpkg-reconfigure xserver-xorg
``` You'll have to follow all steps carefully and afterwards you'll maybe have to re-set your keyboard layout and language settings of your desktop.

If screen resolutions are missing, you could have a look at my post here: [http://ubuntuforums.org/showpost.php?p=4090032&postcount=7]("http://ubuntuforums.org/showpost.php?p=4090032&postcount=7")

For dual-screen setup, use either your driver's configuration tool (probably 'amdcccle' or 'nvidia-settings') or 'XINERAMA' in your xorg.conf, analog to this description: [http://ubuntuforums.org/showthread.php?p=1773624]("http://ubuntuforums.org/showthread.php?p=1773624")

perixx

---

