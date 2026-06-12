---
title: "No Sound on Asus F50 laptop"
date: 2009-11-12
forum: Hardware
---

### Post by Bobob990 on 2009-11-12
Well, I was installed Ubuntu 9.10 today on my laptop an Asus F50 and I cant seem to get any sound to come out plz help me....

---

### Post by Chewable on 2009-11-12
You should try these options first:  
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=1316634&highlight=asus+sound](http://ubuntuforums.org/showthread.php?t=1316634&highlight=asus+sound)
[http://ubuntuforums.org/showthread.php?t=1314788](http://ubuntuforums.org/showthread.php?t=1314788)

But you can cut to the chase and try this instead: 

```
gedit /etc/modprobe.d/alsa-base.conf

```Search for "options snd_hda-intel model = " and put "asus-mode3" after the equal sign. Then save, exit and reboot.

---

### Post by PlankEyeWilly on 2009-12-31
I just wanted to say thanks, and also add a few cents from what I experienced.

When I ran ```
sudo gedit /etc/modprobe.d/alsa-base.conf
``` to edit the config file, i didnt have an "options snd_hda-intel model=" line at all.  I just stuck "options snd_hda-intel model=asus-mode3" with out the quotes at the end of my config file, saved, rebooted and Perfecto!

Thanks again for the fix!

---

