---
title: "i hate my small screen"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by caspermac on 2007-05-30
I'm fairly new to Linux but i install Ubuntu most things work well i can play all my media and access my windows partition excel :D. the two problems that i want to fix are the i can't get my monitor to 1650x1080 (philips model: 200w6cs) and i can't get my nvidia quadro FX 550 drivers working. I did the restricted hardware thing and the display disappears when the login screen comes and tried installing the drivers for nvidia same thing.  i know this question has probably been asked several times but i can't find a working solution. if even i could get my monitor at the correct resolution i would be happy but i guess there one of the same thing

---

### Post by mozetti on 2007-05-30
For setting up different resolutions using the standard "nv" driver that comes loaded with Ubuntu, use this command: ```
sudo dpkg-reconfigure xserver-xorg
```.

I'd start with the basic configuarion option (it asks whether you want to do basic, intermediate, or advanced) and choose the resolutions you want available to you.

Regarding the driver, I would check out Envy (do a search) -- it's a program created by tseliot, a very knowledgable member of the forums here. That might get you sorted out for installing the right driver. If you get the driver installed correctly you can use the command above to configure your xorg.conf file again, if you need to do that.

---

### Post by caspermac on 2007-05-30
well the code work like a peach running at full res now still can't get nvidia drivers correctly installed. tried the envy prog work but when i tried to load X it came up with an error saying the it can't load and the i has been disabled.

---

### Post by caspermac on 2007-05-30
does it have any thing to do with the new kernel and is there any way i could check that

---

### Post by srt4play on 2007-05-30
Yes hit escape when it tells you to during boot, and choose an older kernel from the menu.

---

### Post by mozetti on 2007-05-30
Check this forum thread: [http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

Specifically, here is tseliot's HOWTO for Fiesty: [http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty) -- it even has a section called, "What happens if you change your kernel, or your kernel is updated."  Check it out.

As I recall, one method of installing the driver would cause problems during kernel updates. There is probably info about that in the thread.

---

