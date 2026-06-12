---
title: "auto915resoluton is not working :( HELP"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by ralphz on 2007-08-01
Hi 

I have acer 5570Z with Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03). I have red few post on the forum and installed 915resolution and run the script auto915resiolution.sh but after restart I'm still stuck on 1024x768. Is there any HOWTO for people like me (ones that auto915resolution does not work for) ?

Please

---

### Post by wjp.reg on 2007-08-01
> **ralphz said:**
> Hi 

I have acer 5570Z with Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03). I have red few post on the forum and installed 915resolution and run the script auto915resiolution.sh but after restart I'm still stuck on 1024x768. Is there any HOWTO for people like me (ones that auto915resolution does not work for) ?

Please

Don know anything about auto915resolution or where you got that ????, but you might want try dropping down to text mode by pressing alt-ctrl-F1 and running the following after logging on:

```
sudo /etc/init.d/gdm stop
```
to stop the graphics manager
and then;

```
sudo dpkg-reconfigure xserver-xorg
``` and go through all the prompts, defaults will do, and make sure the resolutions you want are checked.

then you can ```
startx
``` or reboot to be sure :-)

Good luck!

---

