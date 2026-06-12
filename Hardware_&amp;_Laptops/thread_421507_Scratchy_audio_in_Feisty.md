---
title: "Scratchy audio in Feisty"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by Xeph on 2007-04-24
I've done a clean install of Feisty and I get a static-like, scratchy background noise whenever I'm playing any sound. I have a Creative Sound Blaster Live 5.1 sound card and am using Alsa. Whenver I tried switching to OSS, i got no sound at all. 

And ideas? Please help, it's getting really really annoying... This never happened in previous Ubuntu versions.

---

### Post by DocHoliday52090 on 2007-04-24
This worked for me:

Double click the speaker next to your clock and lower the "PCM" volume down to aroudn 70 to 75%.

---

### Post by Xeph on 2007-04-25
Hey Doc

No, it's not that. None of my volume controls are even around 80%. The audio is still scratchy. :(

Xeph

---

### Post by Tomy on 2007-04-27
> **Xeph said:**
> I've done a clean install of Feisty and I get a static-like, scratchy background noise whenever I'm playing any sound. I have a Creative Sound Blaster Live 5.1 sound card and am using Alsa. Whenver I tried switching to OSS, i got no sound at all. 

And ideas? Please help, it's getting really really annoying... This never happened in previous Ubuntu versions.
I get the same background noise on a new Feisty install. If I listen up close to the speakers there is a constant background noise even when no audio is being played. I have messed with Volume Control  settings and both devices (HDA ATI  SB (Alsa mixer)  and  Realtek ALC883 (OSS mixer) give me the same results.

I have a MSI K9AGM motherboard that has integrated everything.
North Bridge: ATI RS485/RS485C
South Bridge: ATI SB600
Audio: Realtek ALC883/888 chip integrated 

Any ideas?

---

### Post by boringryu on 2007-04-30
> **Xeph said:**
> I've done a clean install of Feisty and I get a static-like, scratchy background noise whenever I'm playing any sound. I have a Creative Sound Blaster Live 5.1 sound card and am using Alsa. Whenver I tried switching to OSS, i got no sound at all. 

And ideas? Please help, it's getting really really annoying... This never happened in previous Ubuntu versions.

I also had that static-like noise from all my speakers but it was all the time the machine was on.  Same soundcard as above - the SB Live 5.1.  Didn't happen in Dapper or Edgy.  Even if I muted the volume control the noise was still there.  After a fair bit of time tinkering with settings though I found a fix that worked for me and may be the same for you.

Open the volume control (double click on the volume control - don't use the preferences->Sound which is where I wasted most of my time) and click on the switches tab.  Uncheck the SB Live Analog/Digital output jack.  It should instantly stop the noise if it is the same problem.

---

### Post by jastonas on 2007-05-03
same thing here!
Scratchy noise while playing music or video!
Realtek and Feisty

---

### Post by philldo on 2007-05-03
Hi All,

I had this issue, what i did to solve it, was the opposite to some of the posts here.

I was using VLC and some other players to play the music, i turned the volume down on VLC to about 5-10%, and then used the PCM and Master to increase the volume...

Fixed it perfectly, haven't had a problem since...

Hope this helps!

---

### Post by moneypenny on 2007-05-03
I don't have any kind of "SB Live Analog/Digital output jack" option in my Volume Control, and fiddling with PCM, Master, etc., doesn't seem to do anything.  I've got headphones plugged in now and there's this constant crackly noise mixed with humming and slight beeping in the right ear.  It's annoying as heck, especially since it's ALWAYS there.  I have no music playing, when I log out I still hear this crackling even.

---

### Post by lancest on 2007-05-04
Same problem scratchy sound sometimes. HDA intel (Alsa) ASUS W7J
Also at boot a popping noise when sound starts.
After several installs and manual Alsa install same problem. Seems like this is a Gnome problem?  If I keep the volume slider down I don't notice it.

---

### Post by neomi on 2007-05-04
same problem here

I tryed to turn down the volume but the noise just got hardly heard

---

### Post by imon9 on 2007-05-04
Hello, i just want to say for the longest time, i had the same problem but with some help from #alsa IRC channel ppl, i had them SOLVED!!

here's my story: i have a laptop with VIA AC97' Soundcard. Installed xubuntu edgy (now upgraded to feisty) with alsa, the sound doesnt come right..with some long dragging echo...

after upgrading myself to ALSA version 14RC3, things got better.... but comes the problem with static noise. My long research of the problem give me a few explaination:
(1) static electric from my hardward like harddisk (which is funny, since on my dual-boot XP, my soundcard work just normal)
(2) wrong installation of codec, which in many thread point to gstreamer-fuendo. It seems some solved their problem by removing this pakage (instead, use -good, -bad and -ugly)
(3) bad mixer program...which i tried install a few ..and find QAmixer to have the best control interface.. (might help u deal with your mic recording setting)

Now here is the real reason and solution: (only for my case...AND MAYBE yours)
VIA AC97 soundcard comes with the feature call DXS
(if your soundcard has DXS support, it will show its control bar in alsamixer)

the DXS is suppose to help the soundcard to channel sound from different programs that play sound simultaneously, up to 4 sound channel at 1 moment of time. Meaning, it make it possible for 4 different program to play music at the same time.

HOWEVER, this feature is a bit buggy and it causes the static noise! 

my proble is solved by the following command:
> echo options snd-via82xx dxs_support=2|sudo tee -a /etc/modprobe.d/alsa-base

NOTE: do not do the same command for your soundcard... read the following instruction...

the command above changes the dxs-support to '2' which in human language means 'turn it off/disable it'

IF your soundcard has DXS support and you want to turn it off to try if it solve your problem, then do the following:

> sudo nano /etc/modprobe.d/alsa-base
or 
> sudo gedit /etc/modprobe.d/alsa-base
or 
> sudo mousepad /etc/modprobe.d/alsa-base

find the line that says <your soundcard name> dxs_support (or anything that sound similar) then change the value to 2

IF your are sure that your soundcard has dxs support but there is not such line int he alsa-base that say <your soundcard name> dxs_support, then you can add the line:
> options <your soundcard name> dxs_support=2

save the changes and restart computer/ restart alsa sound service.
to  restart alsa-sound service, use the following commandline=
> sudo /etc/init.d/alsasound restart

Okay, that is the end of my tutorial.. hope that helps someone!!

NOTE #02: for those who is wondering if turning this option off could cause any problems when your computer needs to play simultaneous stream of sound... the answer is NO. It is okay to turn it off since alsa-sound has the feature build-in. So, what you do is just turning off the hardware feature. Alsa got you covered from the software side! Cheers for alsa!

---

### Post by neomi on 2007-05-04
thanks imon9

it works!

---

### Post by neomi on 2007-05-06
i have no idea what to do

it seems that the noise come out randomly, at least now it doesn't

---

### Post by Xeph on 2007-05-08
My scratchy audio is gone! I came home one evening, did the usual Ubuntu updates et voila! No more scratchy audio :) Not sure what updates were done...

---

### Post by regomodo on 2007-05-08
I had sound issues that you are describing.

Look at my signature and remove the codec in synaptic. No dodgy sound anymore. 

I think my chipset is a Realtek AC'97 for the audio

---

### Post by joaopmsantos on 2007-05-13
Unchecking the SB Live Analog/Digital output jack did the trick for me. It's now working 100%!!!
Thanks! :guitar: 

> **boringryu said:**
> I also had that static-like noise from all my speakers but it was all the time the machine was on.  Same soundcard as above - the SB Live 5.1.  Didn't happen in Dapper or Edgy.  Even if I muted the volume control the noise was still there.  After a fair bit of time tinkering with settings though I found a fix that worked for me and may be the same for you.

Open the volume control (double click on the volume control - don't use the preferences->Sound which is where I wasted most of my time) and click on the switches tab.  Uncheck the SB Live Analog/Digital output jack.  It should instantly stop the noise if it is the same problem.

---

### Post by doctorwho on 2007-05-19
I have had a problem in Feisty where I have heard constant static crackling through my computer speakers all the time. The sound would be worse whenever I did anything. Even moving the mouse caused a louder sound. After reading the other posts here, I opened up the KMix applet (I use Kubuntu), and simply muted the PC speaker. Instantly the constant static was gone! To think I've been putting up with this for months and the solution was so simple! I hope this helps someone else.

---

