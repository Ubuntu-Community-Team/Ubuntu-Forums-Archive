---
title: "Random Clicking In Sound After Upgrading to 9.10 Karmic Koala"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by chiques on 2009-11-02
I just upgraded to 9.10 from 9.04. Everything works great except for this random clicking/popping sound in my speakers. Any suggestions on what I should do?

---

### Post by chiques on 2009-11-03
I found something that fixed mine

Go to **/etc/modprobe.d/** and comment the line shown below in ***alsa-base.conf*** by using the **# **symbol as shown below


> # Power down HDA controllers after 10 idle seconds
#options snd-hda-intel power_save=10 power_save_controller=N


I had to reboot for the changes to take effect.


Apparently in the midst of the Ubuntu community trying to be a bit greener, they added this feature to put the sound card in sleep mode to save a little energy. I personally appreciate the effort.

---

