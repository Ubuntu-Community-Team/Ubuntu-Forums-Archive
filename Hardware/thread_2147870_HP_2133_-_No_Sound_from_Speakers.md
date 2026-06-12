---
title: "HP 2133 - No Sound from Speakers"
date: 2013-05-23
forum: Hardware
---

### Post by distortedecho on 2013-05-23
Hi all,

I've acquired an HP 2133 netbook. I've installed lubuntu 13.4 on it (I really miss Ubuntu Remix :( ) and have finally got the wireless working on it.

I'm struggling however, to get the sound working from the speakers. Audio works with headphones only, at the moment.

I can't find any information online on how to resolve this as everyone else (on previous version lubuntu 12.4) audio worked out of the box.

Some expert help would be appreciated. :D

Thanks.

---

### Post by ohnonot on 2013-05-24
i don't know about expert, but try 'alsamixer' in terminal, see if all channels are unmuted and volume is up. also there's an "Auto-Mute" setting if you go right.
also you probably have pulseaudio on top of that, so you have to open your favorite pulseaudio mixer as well.

---

### Post by jacurrie on 2013-05-24
I have a similar problem and have been trying to come up with a solution for a while. I am running Ubuntu on a Dell Inspiron Laptop and since the update to 13.04 the sound has stopped working properly. So far I have found that if I go to the Sound Settings and select test that it shows a four speaker setup. (Obviously wrong) and when I test each of the speakers it is the rear speaker that sends a faint sound to the laptop speakers. I have tried alsamixer and pulseaudio settings but when I change the speaker type to Stereo the system automatically selects a 4.0 setup.

Sorry I can't offer a solution but it might be worth checking to see if you have a similar problem and then others much wiser than me might be able to help.

---

### Post by ohnonot on 2013-05-24
my fault, lubuntu does NOT use pulseaudio by default.
@jacurrie: thus the problems are most likely not related, since you are using ubuntu, which uses pulseaudio.

---

