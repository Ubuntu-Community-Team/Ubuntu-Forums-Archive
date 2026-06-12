---
title: "Vaio Mic configuration - HDA issues.. plz help !!"
date: 2008-07-26
forum: Hardware
---

### Post by Julieee on 2008-07-26
Hi 

I have a porblem I can't solve by myself regarding my new laptop sound configuration. I have a Vaio VGN-AR61E, with a Realtek ALC262 mixer.

Initially:
- Speakers work fine (and still do)
- No headphone sounds
- Impossible to record any sound from the internal mic
- Extremely noisy sound captured from an external mic

What I've done up to know:
Install Alsamixer 1.0.16
Install linux-backports-modules-hardy

I checked several posts 
[http://ubuntuforums.org/showthread.php?t=677746](http://ubuntuforums.org/showthread.php?t=677746)
[http://ubuntuforums.org/showthread.php?t=806620&highlight=hda+vaio](http://ubuntuforums.org/showthread.php?t=806620&highlight=hda+vaio)
and tried to modify the line "options snd-hda-intel model=XXXX" , xxx replaced with sony, sony-ar, 3stack, but nothing seems to work

I a complete Ubuntu noob and i don't know what i should do now :(, so I'll be really glad if someone could help me with that (it's really important, I'm a skype addict :))

Greets, Julie

---

### Post by Toufik on 2008-08-05
There is a known (and old) bug about mic that does not power on during boot (see here: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/37736](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/37736) )

Try this:
 - double click on the speaker icon in the deskbar
 - Click the option tab
 - Change the input source(s) into something else (whatever)
 - Change it back to what you want (normally "Mic" or "Front Mic" for built-in mic)

To be done after every boot :(

---

