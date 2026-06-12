---
title: "Lenovo Yoga Slim 6 (14IAP8 - intel) OK with 24.04 LTS but w sound issue i can't solve"
date: 2024-07-19
forum: Hardware
---

### Post by ntpolylogue on 2024-07-19
Hi, i installed Ubuntu 24.04 LTS (kernel 6.8.0-38) on a Lenovo Yoga Slim 6 (14IAP8 - intel). 
First : it  works smoothly with no big issue (wifi, camera, mic work out of the box - did not try face recognition with IR camera though) I met two inconveniences, for the second one i'd be happy to get a little help :

1. The OLED screen is too saturated under Ubuntu. (did not find an ICC profile that compensates this, nor have a device to calibrate, so i installed Gnome extension Colorblind filter, which has an adjustable desaturate option to handle this). 

2. the speakers' sound, on the other hand, is really weak and trebble pitched (sounding more like a birthday card speaker :-) the woofers (it seems there are in this machine) definitely don't work. I found very few info on this topic for this model. Tryed this workaround [https://wiki.archlinux.org/title/Lenovo_Yoga_9i_2022_(14AiPI7)#Audio](https://wiki.archlinux.org/title/Lenovo_Yoga_9i_2022_(14AiPI7)#Audio) just in case. Did not work. 
Does anywone met this issue and found a way to fix it and get a proper sound out of it ?

---

### Post by currentshaft on 2024-07-22
Have you run fwupdmgr to install the latest hardware/firmware revisions? For the OLED issue, maybe try installing the "icc-profiles" package?

---

### Post by ntpolylogue on 2024-10-06
After a Kernel update (6.11.0 - did not change things, i think my driver is OK)

The best solution i found for the weak sound for now is the one described in the link below : 

install pulseaudio easy-effects,
 then use the convoluer module with the profile settings for Dobly atmos you can download in the linked post :

 [https://www.reddit.com/r/thinkpad/comments/q5pt38/x1_extreme_gen_4_dolby_atmos_setup_for_linux/](https://www.reddit.com/r/thinkpad/comments/q5pt38/x1_extreme_gen_4_dolby_atmos_setup_for_linux/)

Sound output of the laptop built-in speakers is vastly improved. Not as great as the one of a macbook would be, but OK.

---

