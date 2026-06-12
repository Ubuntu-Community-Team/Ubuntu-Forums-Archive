---
title: "soundblaster live 5.1 no sound on version12.10"
date: 2013-01-22
forum: Hardware
---

### Post by sdowney717 on 2013-01-22
googling shows quite a few people have a no sound or sound issue with this card.

Anyway, the card is detected, I have all sorts of options for recording and playback, just no sound. I can get staticy crackly sound when putting the speaker plug from black port to the orange digital out port on the card. (sp/diff?)

It does work in windows, so it is not a hardware issue.

So lend me your thoughts.

---

### Post by sdowney717 on 2013-01-22
I can hear sound if do this

rm -rvf ~/.pulse/
reboot


then set to surround 5.1
then test rear speakers plays sound

front speakers no sound
speaker cable plug is in the black port
I only have 2 stereo speakers.


[http://ubuntuforums.org/showthread.php?t=1845555](http://ubuntuforums.org/showthread.php?t=1845555)

---

### Post by sdowney717 on 2013-01-22
black port is ok for youtube, play movie then just the rear sounds
with it set this way, must plug into orange port for main speakers

For movie to actually hear dialog and background sounds, put in black port and set to analog mono output.

So IMO, it is sort of messed up.

I think it is solved, by putting into the green port and selecting stereo output. Few days ago, I ran alsamixer and using arrow keys cycled thru the various outputs, but dont know if that has to be done or no.

This card will also work in win7 with the KX driver.
Select waveout 4/5 for playback

some info on the black vs green ports
[http://kxproject.lugosoft.com/qguide.php?language=en](http://kxproject.lugosoft.com/qguide.php?language=en)
black supposed to be best.

---

