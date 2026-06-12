---
title: "[SOLVED] 8.10 - No Audio (hp pavilion tx2000)"
date: 2008-11-05
forum: Hardware
---

### Post by a_toff on 2008-11-05
Hi folks, I'm running a fresh install of 8.10 on my brand new HP Pavilion tx2000 (actually tx2617ca), and I've got a number of troubles, but the one I'm focusing on currently is the lack of audio support. I found this post earlier,

[http://ubuntuforums.org/archive/index.php/t-792669.html](http://ubuntuforums.org/archive/index.php/t-792669.html)

and followed the instructions which required that I add the line "options snd-hda-intel model=hp" to my /etc/modprobe.d/alsa-base file. 

Following this procedure has had no effect however. Can anyone suggest a method to get sound working on this laptop?

thx

---

### Post by gali98 on 2008-11-05
You are looking in the wrong threads :)
You need to look in tx2500 threads as that is actually what you have (even though the label says tx2000 :))
the line you need to put is:
options snd-hda-intel index=0 model=toshiba position_fix=1

edit: you might also try:
options snd-hda-intel index=0 model=acer

really you will just have to play with it, since I don't have your exact laptop (I have the tx2000 series. it has a different sound chip)
Just make sure to only have one line at a time.
the best way to search would to go to the main ubuntu screen, then in the search box, type "tx25*" (without the quotes). this will give you a lot of tx2500 threads where you can get help...
Kory

---

### Post by a_toff on 2008-11-06
Thanks very much for the help! 

I used "options snd-hda-intel index=0 model=toshiba position_fix=1" and it works perfectly now after a reboot.

maybe this is why I'm having trouble with your wacom installation guide...

---

### Post by gali98 on 2008-11-07
No.. I posted back to you on the wacom on the other thread. Hopefully we can get it working :)
If you feel this is solved, could you mark it?
(Go to thread tools - near the top and then click on "mark as solved" )
Glad to help in anyway I can.
Kory

---

### Post by jaret100 on 2008-11-14
Thnx gali98. This was what i have been looking for for about 2  months!
I have a hp tx2525 and it worked after reboot.

---

### Post by gali98 on 2008-11-14
Glad I could help!
Kory

---

### Post by dharmabummed on 2008-11-19
quick question regarding this, i added the above line and am getting audio after reboot but it is fairly week, so weak that with full volume on both the media players and the system it is barely listenable

is there any way to fix this?

---

### Post by Favux on 2008-11-21
dharmabummed,
I see no one's answered yet so I'll take a stab at it.  If you go to System>Preferences>Volume Control-or alternatively right click on the sound icon on the top right panel-you'll see the sound sliders.  I'm sure you've turned up Speaker and Master and maybe Front, but also try PCM.  I actually don't know what PCM stands for, it doesn't seem to be defined in Help anywhere, but when I turned it up my formerly faint sound became much more audible.

---

### Post by tekrytor on 2008-12-06
> **a_toff said:**
> Thanks very much for the help! 

I used "options snd-hda-intel index=0 model=toshiba position_fix=1" and it works perfectly now after a reboot.



Adding: "options snd-hda-intel index=0 model=toshiba position_fix=1"

to /etc/modprobe.d as directed worked for me, too! 

I'm running Ubuntu 8.10 on an HP tx2510us with the Intel HDA audio chip. Setting the mixer levels put the final initial touches on my sound config.

Gali98, THANK YOU!!!!

tekrytor ):P

---

### Post by Riverhed on 2008-12-15
Just wanted to say it worked fine for me, too, on a tx2500 with Intrepid. Thanks gali.

---

### Post by RaZoR1394 on 2008-12-23
> **gali98 said:**
> You are looking in the wrong threads :)
You need to look in tx2500 threads as that is actually what you have (even though the label says tx2000 :))
the line you need to put is:
options snd-hda-intel index=0 model=toshiba position_fix=1

edit: you might also try:
options snd-hda-intel index=0 model=acer

really you will just have to play with it, since I don't have your exact laptop (I have the tx2000 series. it has a different sound chip)
Just make sure to only have one line at a time.
the best way to search would to go to the main ubuntu screen, then in the search box, type "tx25*" (without the quotes). this will give you a lot of tx2500 threads where you can get help...
Kory

It works for the Altec Lansing speakers on the tablet but the switches for spdif are gone. No sound with spdif either.

Does anyone have a line that works for both internal speakers and spdif?

---

### Post by akolatronico2021 on 2009-04-30
hey im NoooB in ubuntu, i have a tx 2000 and im having trouble with the sound, everything seems to be working but no sound at all can somebody help me? PLz

thanks!

---

### Post by Favux on 2009-04-30
Hi akolatronico2021,

What version of Ubuntu did you install?  Did you check your System>Preferences>Volume Control and make sure the sliders are up?

---

### Post by jroemusic on 2009-05-18
I'm having trouble. I have a HP Pavilion tx 2000 and I just installed Ubuntu 9.04.

I can't get any sound. Any ideas?

---

### Post by Favux on 2009-05-18
Hi jroemusic,

Welcome to Ubuntu!

What have you tried?  Did you make sure your sliders are up?  Did you try adding "options snd-hda-intel model=hp" (without the quotes) to the end of the "alsa-base" file in "/etc/modprobe.d/"?

---

### Post by redneckProgrammer on 2009-07-06
I would like to add that adding the line:
"options snd-hda-intel index=0 model=toshiba position_fix=1"

worked on my tx2510us with 9.04  

Thanks guys!

---

### Post by cfoy85 on 2009-07-10
hi, first time using ubuntu.
Installed ubuntu jaunty jackalope onto my hp pavillion tx2500 after getting fed up of windows vista and the the amount of hassle required to get xp onto the system (laptop has sata harddrive, and xp doesnt support sata from instillation!)

I'v got ubuntu on the laptop now, but having problems with sound:

I'm attempting to put the code:
"options snd-hda-intel index=0 model=toshiba position_fix=1" into "alsa-base.conf"

I cant get the file to save as i dont have the required privliges. what am i doing wrong? sorry, i know im a nuuuuub and bit of a retarded question.

thx
cfoy85

---

### Post by Favux on 2009-07-10
Hi cfoy85,

Welcome to Ubuntu!

In Jaunty the name got changed from alsa-base to alsa-base.conf.  So you want to add the line:
```
options snd-hda-intel index=0 model=toshiba position_fix=1

```
to the end of the alsa-base.conf file.  To do that in a terminal enter:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add the line to the end.  Save and restart.

Hope this helps.

---

### Post by cfoy85 on 2009-07-10
thank you [Favux]("http://ubuntuforums.org/member.php?u=699990"), work perfect :)

---

### Post by duph on 2009-07-13
Hi!

I have a tx2000 and I'm also running Ubuntu 9.04 and I have the same problem. I've tried adding the following as the last line to "alsa-base.conf", but neither of them seem to work after I reboot:

options snd-hda-intel index=0 model=toshiba position_fix=1
options snd-hda-intel model=hp

I've also reopened the file to verify that it's actually been saved correctly.

Any suggestions as to what I might do to correct the problem?


I also got this link from the Sound Troubleshooting guide, if it's any help: [http://www.alsa-project.org/db/?f=d5703efd92820a394650c66650ef6cb0db5b2648](http://www.alsa-project.org/db/?f=d5703efd92820a394650c66650ef6cb0db5b2648)

---

