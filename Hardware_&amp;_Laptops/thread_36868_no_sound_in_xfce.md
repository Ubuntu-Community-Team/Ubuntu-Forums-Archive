---
title: "no sound in xfce"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by bw32 on 2005-05-25
i have installed a xfce desktop on hoary 5.04. the sound works in Gnome but not in xfce. does anyone know what might be the problem?

---

### Post by eric71 on 2005-05-25
It's possible that you have the output plugins of your various multimedia apps set to use the ESD sound daemon, which is the default in Gnome.  THis is not started in XFCE.  You either need to go into the settings for each program and set them to use ALSA, or you need to run ESD by typing "esd" in a root terminal, logging out of XFCE and telling it to save settings.  Then ESD will start automatically each time you start XFCE.  If you plan to use Gnome a lot, I'd go with running ESD in XFCE.  If you plan to use XFCE exclusively, use the ALSA plugins for your sound apps, because there are some programs that you might come across that don't play nice with ESD (Skype or Audacity, for instance).

---

### Post by bw32 on 2005-05-25
thanks for your reply.

when i run ESD thru consle, it worked.

few questions here, how do i set it to run thru ALSA in GAIM? or instead how do i run esd as a doemon when xfce starts up?

the problem occured when i have ESD running back at the console. Opera doesnot sound any more. i think i should disable ALSA when ESD is running. do you know how?

---

