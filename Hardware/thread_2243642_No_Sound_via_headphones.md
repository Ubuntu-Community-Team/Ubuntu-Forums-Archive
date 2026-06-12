---
title: "No Sound via headphones"
date: 2014-09-10
forum: Hardware
---

### Post by Dan_Hennighan on 2014-09-10
Hi All!

Brand new user of Linux, so please excuse any lack of knowledge..
Here is my scenario-

I have a late 2012 iMac running the latest Xubuntu as a dual-boot.
I have had a lot of issues getting all of apple hardware to work and most seem to be working now except BLuetooth Keyboard & Mouse (Apple Magic mouse & keyboard) and sound through headphones..
Sound plays ok through the built-in iMac speakers, but the moment i plug anything into the headphones jack, there's no more sound through it.
I can see that something is playing as the settings window shows the moving bar to indicate playing music.

I have tried a few things within my knowledge like playing around with sound settings etc (again not much knowledge to try more)
i had a buddy with more experience take a look and he tried the 'alsa-mixer' settings and a couple of other things to try to get it to work, but no go..

i am not certain if there needs to be the right 'drivers' as it doesn't show up in the driver manager..
i have searched & do see a few threads regarding similar issues, but nothing seems to make a lot of sense to me :(

is there anything i can do to resolve this or linux not compatible with apple h/w?
i have tried linux mint (kde) as well & the issue is the same..

if anyone can direct me to a solution or help me solve this situation, i would be extremely grateful!

thank you

---

### Post by Dan_Hennighan on 2014-09-12
Just dropping by to bump this if anyone has any idea..

i tried as well

> [h=3]iMac 27" & ubuntu 11.04[/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Since kernel 2.6.38, the HD audio model **imac27** is available.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]The following line must be inserted at the end of the file [FONT=inherit]/etc/modprobe.d/alsa-base.conf[/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]options snd-hda-intel model=imac27[FONT=inherit][/FONT]
[/LIST]
[COLOR=#333333][FONT=Ubuntu]force reload alsa configuration[FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]sudo alsa force-reload [FONT=inherit][/FONT]
[/LIST]
[COLOR=#333333][FONT=Ubuntu]then unmute and adjust volume of **front speaker** and **Surround Speaker** with the help of : [FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]alsamixer[FONT=inherit][/FONT][FONT=inherit][/FONT]
[/LIST]
[COLOR=#333333][FONT=Ubuntu]Seen at [/FONT][/COLOR][http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)[COLOR=#333333][FONT=Ubuntu] and[/FONT][/COLOR][http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt)

no go :(

---

