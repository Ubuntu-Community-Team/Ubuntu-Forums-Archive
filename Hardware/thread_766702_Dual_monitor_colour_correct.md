---
title: "Dual monitor colour correct"
date: 2008-04-25
forum: Hardware
---

### Post by obidose on 2008-04-25
I have been having trouble with my dual monitor set up for a while.

Hardware = Acer 5920g laptop (Nvidia 8600m Graphics chip)
           Philips 190 WV monitor


With the restricted Nvidia drivers the dual screen works ok, however the second screen is allways excessively bright and with very high contrast. This happens in Vista aswell and I can get around it by using Nvidia colour correction on the screen. In ubuntu (7.10) I try to use this feature on the Nvidia settings but it insist on applying the change to both screens at the same time, making my other screen go dark.

Is there any way/ any program which could allow me to colour correct on the second monitor?

---

### Post by obidose on 2008-04-27
Bump

Anybody?

I hear dual monitor support is improved in 8.04 will that help me. The download servers are pretty clogged though so I wanted to wait a bit.

---

### Post by MrHippocampus on 2008-04-27
The improved dual monitor support which you are referring to doesn't affect the nvidia driver as it handles these things on its own, you might have more luck asking at the more official nvidia forums where some of the developers are active, [link]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14").

---

### Post by obidose on 2008-04-28
I upgraded to 8.04 last night and the problem does seem to be solved. Maybe the driver is newer or something but either way it is fixed, so anyone else who has the problem I advise you upgrade.

---

### Post by obidose on 2008-04-28
While this issue has been pretty much resolved, I still have one niggling issue and wonder if anyone could help.

The colour corection only happens after logging into ubuntu and opening nvidia-settings. As soon as i open this the correction is automatically applied.

Why does it not apply on its own before this? and is there a way to make it apply before logging in, so that the brightness is not messed up for the login screen?

---

### Post by MrHippocampus on 2008-04-28
The reason why the colour corrections happens on a per user basis is simply because different users might want different brightness settings, so one user cant force the entire system to use their own preferred settings. Anyway normally this sort of stuff can be put in the xorg.conf file but I don't think nvidia has provided a way to set the brightness in the xorg.conf file (I could be wrong though). 

The only way around this I can think of is to make gdm run 'nvidia-settings -l /home/username/.nvidia-settings-rc' which will apply your settings when gdm (the login screen) starts (without bringing up the actual window itself). I cant remember how to make gdm run things when it starts, but it is definitely possible as that's how people get screen savers running as the gdm background.

---

