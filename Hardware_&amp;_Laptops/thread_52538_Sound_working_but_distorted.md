---
title: "Sound working but distorted"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by Psyche on 2005-07-28
Hello!

I've managed to configure my SB Live! 24 bit using the tutorial posted on this forum. The sound is working, but it's very distorted. How can I correct this issue? 

Thanks in advance.

---

### Post by gray-squirrel on 2005-07-28
If you have ALSA, then this [resource](http://www.sabi.co.uk/Notes/linuxSoundALSA.html#issueList) should help you.

[http://www.sabi.co.uk/Notes/linuxSoundALSA.html#issueList](http://www.sabi.co.uk/Notes/linuxSoundALSA.html#issueList)

I have the same card.  I thought the distortion was a sound card issue - I was previously using the integrated audio chip on the Abit VA-20, and had the same issues with that.  I keep thinking that the volume controls work the ones in Windows, but that will definitely have to stop.  If I can get the speakers plugged elsewhere without having to worry about anything, it will be great.  Otherwise, I'll just have to turn up the speaker volume more than usual.

---

### Post by orb_nsc on 2005-07-28
Thanks for that first link, Gray-squirrel.  That fixed my distortion problem that was nagging me as well.  Mine is just a cheap onboard VIA AC97 deal, but it sounds a lot better now...just had to lower its output in alsamixer.

---

