---
title: "audio on ubuntu."
date: 2008-09-21
forum: Hardware
---

### Post by spriizha on 2008-09-21
Ok i know u gona kill me of this. I'm searching for some h, but i can't find answer.
Problem : sound works- but no effect of jack plug in ( still sounds the laptop )
model: benq Joybook p52

ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)


sorry for be dum.. :( but i just can't find it. :confused:

---

### Post by lisati on 2008-09-21
Are you using a laptop by any chance? I've occasionally seen reports in these forums that sometimes the use of the "headphone" jack is problematical. If memory serves correctly, there is a workaround.

---

### Post by spriizha on 2008-09-21
> **lisati said:**
> Are you using a laptop by any chance? I've occasionally seen reports in these forums that sometimes the use of the "headphone" jack is problematical. If memory serves correctly, there is a workaround.

i had it done year ago. i just had a xp again for a while, and just can't find the problemfix again. it was working on ubuntu year ago. :/

---

### Post by spriizha on 2008-09-21
dam it. messed up things.. now i don't have sound at all. :(

and in volume mixer file-->change device i got 5 of them. X_X

0:HDA ATI SB (Alsa Mixer)
1:Realtek ALC262 (OSS Mixer)
2:Playback: ALSA PCM on front:0 (ALC262 Analog) via DMA (PulseAudio Mixer)
3:Capture: Monitor Source of ALSA PCM on front:0 (ALC262 Analog) via DMA (PulseAudio Mixer)
4:Capture: ALSA PCM on front:0 (ALC262 Analog) via DMA (PulseAudio Mixer)

is that normal? O.o ehh.. im so stupid in linux..

---

### Post by DakoCwerf on 2008-09-21
yes, its normal.
0 - its standart output using alsa mixers
1 - standart output using oss mixers
2 - pulseaudio is a helper utility for alsamixer to redirect sound from front speakers to headphones, usb speakers etc.
3, 4 - capture things, i dont know the difference.

try to compile alsa driver/util/lib of the latest version from source.

---

### Post by spriizha on 2008-09-21
> **DakoCwerf said:**
> try to compile alsa driver/util/lib of the latest version from source.


mmkey. just 1 more question then. how? :D

---

### Post by DakoCwerf on 2008-09-21
i'd say google it, but here is the small instruction.

download latest stable packages from [http://www.alsa-project.org/](http://www.alsa-project.org/)

extract them somewhere, open that folders in terminal and for each package do
> ./configure
sudo make
sudo make install

if no errors appear - you are done, reboot and hope you get your sound. if errors happened - google them. usually that means you are missing some packages or dependencies and its easy to fix.

---

### Post by markbuntu on 2008-09-21
If you are having problems with your ALC 262 you should look here:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

If you are having problems with headphone/speaker control with your HDA sound device you can try this threads:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

### Post by spriizha on 2008-09-21
heh... i didn't read last post, cus was busy with all this thing :D
I tried like Dako sad, but there was errors while using sudo make in alsa driver stuff..
then i continue searching and used [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) this one. it works, but now the speakers and laptop sounds together.. :( 

so now im just using ```

sudo apt-get install m-a
sudo m-a prepare
sudo m-a a-i alsa

```

and will se the results. will post when everything will be fine. thx for now.

---

### Post by spriizha on 2008-09-21
mmkey looks like im done. Only thing - i have to mute Front in volume mixer, so the laptop shut up and the headphones only is playing. Nice. Thx u guys.. and looks like i got something off compiling too.. a little bit hot to :)

have a nice day :P~

---

