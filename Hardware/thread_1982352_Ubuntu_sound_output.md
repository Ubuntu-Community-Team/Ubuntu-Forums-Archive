---
title: "Ubuntu sound output"
date: 2012-05-18
forum: Hardware
---

### Post by Asaru on 2012-05-18
Hello, I have a little issue.
I have a laptop (Dell Studio 1535) and since I upgraded to 12.04 from 11.10, I've been experiencing problem with audio. In fact, regular internal speakers work correctly, but when I plug in any device (speakers/headphones), the internal speakers turn correctly off, but no sound is sent to my speakers.
Do you have any idea, what could it be?
Thanks for any help in advance
Asaru

---

### Post by Asaru on 2012-05-22
bump
still no solution found anywhere
but I found out that speakers are recognised by system (preferences-sound show headphones, when I plug them in).

---

### Post by idoitprone on 2012-05-22
> **Asaru said:**
> bump
still no solution found anywhere
but I found out that speakers are recognised by system (preferences-sound show headphones, when I plug them in).

Rant: ALSA stack is a piece of **** that should never be in a modern operating system. Rant done

[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio.txt)

Go down to Speaker and headphone output
It says to check if the sound is muted
there is couple places to check

First is pulse audio,  there should be a place in ubuntu settings
I dont know where because I left ubuntu years ago

Second
type
```
alsamixer
```
in terminal

If I am correct
f6->sound card

unmute your card
press escape to exit

---

### Post by Asaru on 2012-05-27
Ok, I tried both. In System settings GUI, nothing is muted and the volume is maxed.
and in alsamixer, Everything is maxed and unmuted. Then I plug in speakers/headphones... System recognises both as headphone (in alsamixer) and set speakers to muted, volume 0.
But from what I found out, the system sends some sound to speakers. To hear it, I had to turn volume to max and then, I heard a very very quiet sound. Only from speakers, headphones are still quiet.

---

