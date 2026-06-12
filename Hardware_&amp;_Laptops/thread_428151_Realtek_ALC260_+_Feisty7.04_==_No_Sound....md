---
title: "Realtek ALC260 + Feisty7.04 == No Sound..."
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by zhfm622 on 2007-04-30
i really don't know what the problem is, it seems that my hardware is recoganized automatically by ubuntu Feisy, but there is no sound at all. 

Here are packages that i installed related to "alsa" 
"alsa-base",
 "alsa-firmware-loaders", 
"alsa-oss" "alsa-utils",
 "gstreamer0.10-alsa", 
"libasound2"
"libesd-alsa0"
"libpt-plugins-alsa"
"linux-sound-base"

Also, i tried the official released drivers from realtek web page, but more worse, if i installed  any of them, the driver will remove my "libasound.so.2" file, which causes me even not able to start my system ! ( i had to reinstall the whole Feisty! )

i'm not sure about this, but maybe someone could help me ????

"System" ->"Peferences" ->"'Sound", there are many options, most of them can choose "autodetect", but there are two categories that i 'm not sure which to choose. 
1) "Sound Capture" -> options are "ALC260 Analog", "ALSA - Advanced Linux Sound Architecture",  "OSS - Open fSound System",  "Test Sound " and "Silence";
2) "Default Mixer Tracks" -> options are "Realtek ALC260 (OSS Mixer)" and "HDA ATI SB (Alsa Mixer)" ;

i almost tried every one, but no one has ever any sound. ...

i'm really desperate.

---

### Post by Rospo Zoppo on 2007-04-30
Have you tried this [http://ubuntuforums.org/showthread.php?t=418360&highlight=alsamixer%3A+function+snd_ctl_open+failed+for+default%3A+No+such+device]("http://ubuntuforums.org/showthread.php?t=418360&highlight=alsamixer%3A+function+snd_ctl_open+failed+for+default%3A+No+such+device")?

---

### Post by zhfm622 on 2007-04-30
> **Rospo Zoppo said:**
> Have you tried this [http://ubuntuforums.org/showthread.php?t=418360&highlight=alsamixer%3A+function+snd_ctl_open+failed+for+default%3A+No+such+device]("http://ubuntuforums.org/showthread.php?t=418360&highlight=alsamixer%3A+function+snd_ctl_open+failed+for+default%3A+No+such+device")?

ok, thank you for the information first,  but i tried, but when i codes this:
>  mv .asoundrc .asoundrc.bak 

The terminal says 
> mv: cannot stat `.asoundrc': No such file or directory  

what should i do then???????

---

### Post by Rospo Zoppo on 2007-04-30
Hm, nothing, go ahead :)

---

### Post by zhfm622 on 2007-04-30
this is a really wired problem!!!

i followed instructions, and it seemed to be fine, no error or anything. 
But after i rebooted system,  there is still no sound at all!
:confused: :confused: :confused:

---

### Post by larukunst on 2007-04-30
Hi, I'm in the same situation... somebody knows something else? 
I've tryied out that thing of making alsa recognize my default sound card but even rebooting nothing happens... 

Help!!! XD

---

### Post by zhfm622 on 2007-05-01
> **larukunst said:**
> Hi, I'm in the same situation... somebody knows something else? 
I've tryied out that thing of making alsa recognize my default sound card but even rebooting nothing happens... 

Help!!! XD

here is another thread that i posted on kubuntu forum ( i have both on my laptop and both of them don't have sound .....) 
[http://kubuntuforums.net/forums/index.php?topic=3082502.0](http://kubuntuforums.net/forums/index.php?topic=3082502.0)

Though neither of their suggestions works for me.... 
But i put it here, just in case,  maybe some of them work for you.

---

