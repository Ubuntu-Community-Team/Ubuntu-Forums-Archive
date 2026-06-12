---
title: "T400 - screen dims on reboot."
date: 2009-03-29
forum: Hardware
---

### Post by j0hn00 on 2009-03-29
Ubuntu 8.10 x64
Lenovo T400
Intel X4500MHD

I've only been using Linux for about a week, so please be understanding... Every time I reboot, the screen dims quite a bit during and after the boot process. I currently have it set to 85% brightness through "Power Management Preferences". I've unchecked the "Dim display when idle" option in both AC and battery modes. I have to manually increase the brightness one notch and then lower it again a notch to get back to my preferred setting. Any ides why this is? Any solutions? Any advice is much appreciated. Thanks for looking.

---

### Post by bobbarker on 2009-04-03
Check the BIOS settings. There are settings that say "dim screen during bootup and before login" where it'll push the screen down to minimum brightness.

---

### Post by nbotticelli on 2009-04-05
Here is your fix:

[thinkwiki]("http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Brightness_control_broken_-_lowest_level_after_Booting.2FSuspend.2FHibernate.2FScreen-off")

I just setup Intrepid Ibex on a new Thinkpad T400 and had the same exact problem. 

It's actually a bug or something along those lines. You basically just have to end a line into a config file and your set.

---

### Post by j0hn00 on 2009-04-05
thanks!

---

