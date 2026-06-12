---
title: "no sound/video on computer/in skype...please help"
date: 2009-04-23
forum: Hardware
---

### Post by stppnwlfn on 2009-04-23
hello,
i am a quite new ubuntu 8.10 user but read a lot about it...so everything worked perfect until i tried skype...first i had sound, but now i dont have any sound and no microphone...although my laptop (hp compaq nx6325) should have it. also the video doesnt work in skype although in ekiga it works perfectly...(its one usb connected webcam)
i have read about the problems that are common with the hp and the sound (sb), but somehow i could not fix it. i tried to download one asa driver, but when i try to install it it says "no such directory found".
i am really a little bit clumsy with these things and since i changed some sound settings (i tried all possible ways when i click on the sound symbol) it doesnt work at all anymore....before i at least heard some noise in the sound test. now i put everything like it was in the beginning and still no sound....
if anyone has an advice for me, would be so perfect!
thanks!

---

### Post by stppnwlfn on 2009-04-23
hello again....now i have tried this:

sudo killall pulseaudio
sudo alsa force-reload

and after:

alsamixer -Dhw

to change my settings.

the playback sound is back, but my micro still doesnt work....and the skype testcall doesnt connect...i have no clue why.

the video is still not working...i idea what to do about that...
regards!

---

### Post by stppnwlfn on 2009-04-23
hello.
it is strange. i set my micro (settings of volume control to prefence "digital") the micro seems to work but is always mute.
when i change it to unmute and close the next time that i open its mute again and i cant hear anything in the micro test (of course because its mute)
but when i leave the volume control open (on unmute) and make the micro test it works....as soon as i close its mute again.
my video still doesnt work in skype...like i said in the ekiga softphone it works normally...but in skype its a grey line....why?
please help

---

### Post by Aq32 on 2009-04-26
Hi,
I recently installed Jaunty and had the same problem. I use the nx6325 too so I know this worked for me.

Open a terminal and enter


```
sudo gedit /etc/modprobe.d/alsa-base
``` 
  

This should give you a text file with (amongst other things) these lines:
```
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
  
```

If you add the line:
```
options snd-hda-intel model=hp position_fix=1 enable=yes
```
to the end then it should work with a restart.

Good luck!

---

### Post by eju on 2009-04-28
I had the same problem on IBM thinkpad R50e.
Now I installed ubuntu 9.04 but the problem still the same as 8.10
I did your suggestion but it's not working.

---

### Post by dragos_iliescu_2005 on 2009-04-28
Take a look here:
[http://ubuntuforums.org/showthread.php?p=6589810]("http://ubuntuforums.org/showthread.php?p=6589810")
It work for me on a Compaq 6715.

---

