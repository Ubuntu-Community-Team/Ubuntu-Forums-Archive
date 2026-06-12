---
title: "How to permanently set volume to 150%?"
date: 2010-07-05
forum: Hardware
---

### Post by vickoxy on 2010-07-05
Hi,
i have ubuntu 10.04 64bit running on my ThinkPad R500. Watching movies i noticed that on 100% volume the sound is not so powerful. Ok, i knows that speakers in R500 are not the best, but then i saw  in volume settings (panel volume icon) that i could set volume to 150%. And the sound is then far more better. But as soon as i  set with my keyboard or mouse  volume to less than 150% it drops to 100% and bellow. And i can not adjust it back to 150% with keyboard or mice (scrolling wheel)- i have to go back to panel icon and manually set it back to 150%. Is there any way to set volume to be always available till 150%?

Thanks

---

### Post by lidex on 2010-07-05
You can probably do that using paman (pulseaudio manager). If not installed, install these:
```
sudo apt-get install padevchooser paman pavucontrol
```
Run Pulseaudio Device Chooser from Sound&Video menu, click on the icon that appears in the notification area, and select "Manager". On the devices tab select the correct entry then click "Preferences" and bump up the level there. See below.

---

### Post by vickoxy on 2010-07-31
Well, the same thing as before. I can go up to 400% of sound volume, but as soon as i go down, it goes to 100% and bellow and i can not increase sound volume above 100%.

So, the problem still remains: how to use volume increasing option above 100% with keyboard (without going to audio setup menu)?

EDIT: it seems that i found solution. If i run in VLC some movie, i get a new channel to setup audio-i increased there sound volume up to 250-300% and it seems to be keeping this volume increasing permanently. So now is 80 or 90 % volume in panel much louder as before. The quality is not perfect, but that is another problem. Now i can at least hear movie dialogs/sound clearly...

lidex, thanks :popcorn:

---

### Post by lidex on 2010-07-31
You can also change levels on your sources just below the sink as well as the main sink. Try playing around with those, it may get the effect system-wide.

---

### Post by vickoxy on 2010-08-01
Well, thanks for advice-i´ll try it if there will be problems with other apps. The only problem was vlc playing dvds. With other apps sound volume is just ok.

---

### Post by vickoxy on 2011-06-18
I will push this thread. Have still the same problem with 11.04 and Macbook pro. If i use Speakers at 100% there are for me not enough loud. With keyboard keys i can increase Volumen to 100%. If i open Sound Preferences (see Picture) i can go to 150%. But can not keep this 150 as Maximum. As soon as i go low with sound, maximum with keyboard is again only 100%. Is there any way to use all this 150%?

---

### Post by lidex on 2011-06-18
Have you seen this:
[http://ubuntuforums.org/showthread.php?t=1317562](http://ubuntuforums.org/showthread.php?t=1317562)

---

### Post by vickoxy on 2011-06-19
I made suggested changes, but it doesn´t change anything at me. I have decent sound on my MacBook Pro, but the question is how to use 100-150% sound volume with keyboard keys?
After changes i made, i still can not move sound volume above 100% (except in sound properties, but, as said, as soon as i change the volume level, can not go back above 100%)

---

### Post by lidex on 2011-06-19
Yeah, I don't have any ready answers but these links may provide a clue:
[http://ubuntuforums.org/showthread.php?t=496180](http://ubuntuforums.org/showthread.php?t=496180)
[http://ubuntuforums.org/showthread.php?t=1568423](http://ubuntuforums.org/showthread.php?t=1568423)

---

