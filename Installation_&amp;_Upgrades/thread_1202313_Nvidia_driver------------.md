---
title: "Nvidia driver------------"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by npm1 on 2009-07-02
help guys i want to set the screen resolution for my ubuntu desktop 9.04---


currently i went to SYSTEM > PREFERENCES >APPEARANCE chose the VISUAL EFFECTS tab and selected NORMAL it then downloaded and installed my NVIDIA DRIVER which in turn asked "NEXT TIME WHEN RESTART PLEASE SELECT THE VISUAL EFFECT U'D LIKE AGAIN."


so far all goood but-----

---

### Post by npm1 on 2009-07-02
when i go to ADMINISTRATION > NVIDIA X SERVER SETTINGS > X SERVER DISPLAY CONFIGURATION > and change my resolution from auto to 
1280 x 1024 resolution then click SAVE TO  CONFIGURATION FILE and click SAVE an error comes uo with "UNABLE TO CREATE NEW X CONFIG BACKUP FILE '/ETC/XORG.CONF.BACKUP'."


this is a clean install of ubuntu
i am a new user

my graphics card is Nvidia geforce4 mx 420

basically i want to make the 1280 x 1024 resolution perminent

---

### Post by hal10000 on 2009-07-02
All you have to do is to run /usr/bin/nvidia-settings with root privilegs, so from a terminal window run [COLOR="Red"]sudo /usr/bin/nvidia-settings[/COLOR] and make the changes you like.

---

### Post by npm1 on 2009-07-02
thanks man------

know i want to install compiz and awn----

---

