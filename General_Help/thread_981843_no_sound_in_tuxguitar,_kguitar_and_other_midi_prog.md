---
title: "no sound in tuxguitar, kguitar and other midi programs"
date: 2008-11-14
forum: General Help
---

### Post by supertonsil on 2008-11-14
I have tried to play songs in tuxguitar and kguitar.
But I can't hear any sound output.

kguitar gives the error:
TSE3: Alsa: Received invalid input type &#65533;

While tuxguitar doesn't give an error at all.

Both of them play the song, but I can't hear any sound

I think it has something to do with the midi output, because I have tried playing midi files with pmidi and it I also cannot hear anything.

pmidi -l
>  14:0     Midi Through                      Midi Through Port-0

Please help
Thank You

---

### Post by SnakeHips on 2008-11-14
Hi,

I had the same thing and fixed mine thus:

from package manager install timidity

then:

tuxguitar/tools/settings/sound.......set midi port to -

TiMidity port 0 #1 (or play around with the other ports till you find one that works.)

---

### Post by supertonsil on 2008-11-16
Thank You.
I just needed to try all the ports.
Most of them don't work, but some of them do.

Now I just need to find a better sequencer or something,
because there is still a little bit of lag and the sound quality isn't that good (it has artifacts).

Do you have any idea what the problem might be?

I am using TiMidity port 0 [128:0] and the TuxGuitar Sequencer.

Thank You for already being a great help! :)

---

### Post by www.rzr.online.fr on 2008-11-26
> **supertonsil said:**
> 
Now I just need to find a better sequencer or something,
because there is still a little bit of lag and the sound quality isn't that good (it has artifacts).

Do you have any idea what the problem might be?


Does this happends also with tuxguitar-snapshot-jsa :

[http://rzr.online.fr/q/tuxguitar](http://rzr.online.fr/q/tuxguitar)

---

### Post by supertonsil on 2008-11-28
This is quite a lot of effort to add another repository.
Isn't there a way I could just download it somewhere and make?

---

### Post by Jonomac on 2008-12-03
Thanks a lot this post helped me as well.  Settings that worked for me was to use TiMidity port 1 #2.  I guess each system is different and you just have to mess around till you get the right one.

---

### Post by frostwyrm333 on 2009-01-01
After installing timidity, still no port works for me. I have only some generic onboard sound card.
EDIT. I just had to reboot. Workds fine now.

---

### Post by kjeldsteen on 2010-06-10
hey i'm very new to kguitar and i need a guide or toturial to help me and i can't find one. can some of you guys help me find one plz!! :D

---

