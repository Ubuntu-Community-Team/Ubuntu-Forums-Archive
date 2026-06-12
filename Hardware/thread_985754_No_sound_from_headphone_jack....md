---
title: "No sound from headphone jack..."
date: 2008-11-17
forum: Hardware
---

### Post by chazdraves on 2008-11-17
Greetings, all!

I have a Gateway t6330u which seems an ideal candidate for Linux except that I cannot get any sound out of the headphone jack... I see all sorts of posts like this across the internet, but none of them seem to have found an answer. I'm running 32-Bit 8.10 and everything else works great (save the screen brightness, but we found a trick for that).

I appreciate the help!
- Chaz

---

### Post by chazdraves on 2008-11-18
Nobody, eh?

- Chaz

---

### Post by barisurum on 2008-11-18
So the normal speaker output works? If it is so then you may have to make a mixer setting to adjust headphone output. In a terminal write: 

alsamixer

And try to adjust headphone volume.

---

### Post by chazdraves on 2008-11-19
The only channel that comes up in alsamixer is "Master".

- Chaz

---

### Post by Trafferth on 2008-11-19
Hey Chaz,

I expect you've already tried some of these, but here goes:

1. Double-click the volume control, select preferences, check all the boxes, go back to the volume control mixer, unmute everything, and turn all the volume controls up.

2. Look along the top of the mixer for a tab labelled 'Switches' or similar; make sure something weird like attempting to send digital sound to analogue speakers (or vice versa) isn't going on...

3. Right-click on the volume control, select preferences, and try a different playback device (there will probably be several to try).

4. Go to System > Preferences > Sound and try switching the devices shown in the drop-down boxes.

5. As a last resort, try using alsamixergui instead of alsamixer.  You will need to fetch it from a terminal:

```
sudo apt-get install alsamixergui
```

Then run it:

```
alsamixergui
```

Good luck!

Trafferth :)

---

