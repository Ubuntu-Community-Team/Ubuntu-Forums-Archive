---
title: "No sound on my laptop period. 7.10"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by jsschulz on 2008-02-13
Alright I recently installed ubuntu 7.10 and it works flawlessly, aside from not having sound. now I read other threads that said to go to sound, tab switches and mess with external amp, though when I open my sound preferences there is no tab for switches.

Also my laptop has a touch control for sound etc, and it shows the mute button being turned on even though when i touch it it toggles on and off on linux, just the external orange light on the touch doesn't change back to blue. help please.

---

### Post by jsschulz on 2008-02-13
Also now when I try to click "test" under preferences I get this

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

---

### Post by jsschulz on 2008-02-13
Nevermind the problem got fixed by upgrading to 8.04

---

### Post by littletinman on 2008-02-14
how did you ubgrade to 8.04? i', about to reinstall ubuntu 7.10 with 64 bit instead of 32 and start from a clean slate but if 8.04 works i'll try that. how do i get it?

---

### Post by jsschulz on 2008-02-14
Its technically a beta upgrade so its not 100% compatable, I took the chance though and upgraded. If you just google upgrade hardy heron, there should be a link that will let you. It fixed my problem, and worse case scenario if it fails for you you just reinstall 7.10 like you were going to anyways.

---

