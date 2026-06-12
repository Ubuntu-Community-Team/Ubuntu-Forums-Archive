---
title: "No sound after hibernate"
date: 2008-09-02
forum: General Help
---

### Post by reffu on 2008-09-02
I know many threads also cover this topic but none seem to help so I thought I'd make my own. 
System: I made my own desktop computer
It contains a Realtek alc662 sound card built in to the motherboard.

Problem: no sound after hibernate. works fine after restart but i don't want to have to restart after every time i hibernate my computer.

Tried fixes:
restart alsa: didn't work
Use uswsusp: still no sound 
Change shutdown mode from shutdown to platform: made no difference
Change volume levels for master and pcm: didnt help.

If there is something i havent tried or you think i should try please post it. 

thanks,

reffu

---

### Post by sv1cdn on 2008-09-04
Have u tried in system->preferences->sound for all playback and captures to change autodetect to another value, like ALSA?

---

### Post by panayk on 2008-09-04
Have you found this?

[https://bugs.launchpad.net/bugs/25896](https://bugs.launchpad.net/bugs/25896)

EDIT: Apparently this is fixed in 2.6.27-2.3

---

### Post by reffu on 2008-09-04
I have tried it with every option in all of the fields.

---

### Post by reffu on 2008-09-04
thanks panayk the entry by tuxo in that bug report fixed my problem. I've looked at that bug report tons of times before and never managed to find that post.

---

