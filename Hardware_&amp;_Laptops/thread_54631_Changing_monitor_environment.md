---
title: "Changing monitor environment"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by s_p_a_r_k_y on 2005-08-05
Sometimes I have another monitor attached to my laptop as a 2nd display (another screen not clone). Its useful at work so I can maxamize desktop real estate, but if I'm traveling with the laptop I don't have a 2nd monitor plugged in. However, I find myself having to plan before I shut off the computer what my next setup will be as X wont load if I had the dual display xorg.conf file in place when I don't have the dual display (only laptop monitor). So then I have to copy the xorg.conf.single file I created over xorg.conf and restart gdm.

Is there a way for a dual display setup to work with just one config file, so that if the 2nd monitor is missing it just disregards it? Its silly to have to constantly copy over xorg.conf with a new config file depending on the setup.

---

### Post by s_p_a_r_k_y on 2005-08-06
no thoughts? No quick bash script I can throw into /etc/init.d/gdm which would decide which config file to use?

---

