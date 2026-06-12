---
title: "Popping noise at shutdown"
date: 2009-11-02
forum: Hardware
---

### Post by kut77less on 2009-11-02
When I shutdown ubuntu there is a big popping noise. This does not happen in Windows 7 because it mutes before shutdown (I know this because the audio button turns red) this does not happen in ubuntu, and cases a big pop, which ruins the hardware. Can I please get some help?


I have an Hp 

Karmic koala. 

Thanks

---

### Post by Dark_Stang on 2009-11-02
The pops don't really ruin hardware. But I too had a few issues relating to alsa in 9.10 after I installed the old gdm. I fixed them by removing alsa-base, alsa-utils, and linux-sound-base.

---

### Post by kut77less on 2009-11-02
> **Dark_Stang said:**
> The pops don't really ruin hardware. But I too had a few issues relating to alsa in 9.10 after I installed the old gdm. I fixed them by removing alsa-base, alsa-utils, and linux-sound-base.


Does removing these things make my sound not work? 

thanks

---

### Post by Dark_Stang on 2009-11-02
> **kut77less said:**
> Does removing these things make my sound not work? 

thanks
Well, it depends on whether or not your sound card works with pulseaudio. Mine works great with pulseaudio(now) and I've had no issues. Worst case scenario: Your sound stops working and you reinstall the packages and everything is back to what it was.

---

### Post by kut77less on 2009-11-09
> **Dark_Stang said:**
> Well, it depends on whether or not your sound card works with pulseaudio. Mine works great with pulseaudio(now) and I've had no issues. Worst case scenario: Your sound stops working and you reinstall the packages and everything is back to what it was.

Well I removed it and I still get that popping noise. I have noticed that when I put my laptop to sleep a red light appears on he mute button. How would I apply this during shutdown.

---

