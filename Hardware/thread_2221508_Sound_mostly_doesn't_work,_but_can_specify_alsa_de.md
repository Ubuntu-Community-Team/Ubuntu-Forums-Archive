---
title: "Sound mostly doesn't work, but can specify alsa device directly"
date: 2014-05-02
forum: Hardware
---

### Post by moriarty00 on 2014-05-02
I think this is an alsa config issue, but I've been Googling for so long that I'm beating my head against a wall.  Hopefully someone can help.

I have a mythbuntu 14.04 setup. Sound has not worked for months (since before the 14.04 upgrade), with two exceptions.  One is that mythtv sound does work. (Mythtv specifies an alsa device directly.) The other is that this command will play sound:

aplay -D plughw:2,7 /usr/share/sounds/alsa/Front_Center.wav

But this command won't:

aplay /usr/share/sounds/alsa/Front_Center.wav

And nothing else will play sound either. Banshee, browser videos...nothing. Clearly I need to set 2,7 as the default device, or something like that, right? So how do I do that? I've tried so many configurations of ~/.asoundrc and /etc/asound.conf (currently I have no files with either of those paths), but I can't make anything work. Can anyone help me with the magic incantation?

Thanks in advance!

---

### Post by moriarty00 on 2014-05-04
Problem has been solved. I needed to use pavucontrol to configure  pulseaudio, fiddling with turning off various inputs and/or setting them  as fallback until I got it to work. More info:  [http://ubuntuforums.org/showthread.php?t=1999015](http://ubuntuforums.org/showthread.php?t=1999015)

---

