---
title: "problem enabling nvidia-glx-new"
date: 2008-09-22
forum: Hardware
---

### Post by alejaaandro on 2008-09-22
ok guys, i d really appreciate some help here, i ve been bustin my head all day long:

trying to fix an smplayer problem, i decided to reinstall the nvidia-glx-new driver...

i uninstalled it using envyng and when it finished i tried to install it again, but it failed.. i tried installing it through system> administration> hardware drivers and through synaptic, but it kept failing.. i finally managed to install it after searching the forum as i had to sudo dpkg-divert --remove some files.

i reboot, get the configuration screen, choose my monitor and driver (i ve tried it with both nvidia drivers that are available in that selection) and finally login to having a 800x600 resolution.. Besides that, desktop effects refuse to be enabled..

I'm not even sure the driver is enabled: system> administration> hardware drivers shows it's enabled, but when running nvidia-settings i get a message that the driver does not appear to be running, and tells me to run nvidia-settings and restart x, which i do , and nothing changes...

how can i see if it's really enabled and if not, how can i enable it?

i m running on hardy, with an nvidia geforce fx5700, if you need any more info just ask...

---

### Post by alejaaandro on 2008-09-22
nevermind, i finally got it working after purging and reinstalling the driver a few more times... dunno if i was doing something wrong but envy didn't seem to work for me..


i lost my compiz configurations though... :(

---

### Post by tuxxy on 2008-09-22
Maybe you had not removed all drivers installed

---

