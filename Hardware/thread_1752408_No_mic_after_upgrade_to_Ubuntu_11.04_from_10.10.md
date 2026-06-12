---
title: "No mic after upgrade to Ubuntu 11.04 from 10.10"
date: 2011-05-07
forum: Hardware
---

### Post by Kentucky88 on 2011-05-07
I upgraded from Ubuntu 10.10 to Ubuntu 11.04 (64-bit).  Since the upgrade, all hardware works as before except that I have no mic.  I also installed an updated nVidia driver for my video card after the upgrade so that could be related.  What information can I post to diagnose this problem?

---

### Post by ankarajasekar on 2011-05-08
> **Kentucky88 said:**
> I upgraded from Ubuntu 10.10 to Ubuntu 11.04 (64-bit).  Since the upgrade, all hardware works as before except that I have no mic.  I also installed an updated nVidia driver for my video card after the upgrade so that could be related.  What information can I post to diagnose this problem?

hello  i also face the same  problem
 my  headphones mike is not working while  i installed  11.04  
but  10.10  it worked  so let me know
 how to solve this
but  in my  friend  i checked it works

---

### Post by ECPCLINUX on 2011-05-08
I thought until today all was well with my Upgrade from 10.10 to 11.04 64 bit till I tried to use Skype. I went to the sound setting and no sound at all. If anyone figures this out please help.  In the mean time I'm backing up all my files again.  I need more hard drive space,lol

---

### Post by ECPCLINUX on 2011-05-08
I believe I found the answer.  Open a Terminal and type alsamixer --> then enter-->next choose F4-- then I choose Rear Mic in my case since I have my headset plugged there. I used the left, right arrows to get there then up and down arrows to raise or lower the volume. Once done I pressed ESC. That was all I needed to do.  I should mention make sure you have the correct sound card and other setting on sound preference.  Hope this helps! :D

---

### Post by leonkou on 2011-05-14
Congratulations, this IS the answer! THANX!

Leo

---

### Post by ECPCLINUX on 2011-05-14
> **leonkou said:**
> Congratulations, this IS the answer! THANX!

Leo

It's still working for me as well, your welcome and glad it helped.

---

### Post by Emanuele_Z on 2011-05-30
> **ECPCLINUX said:**
> I believe I found the answer.  Open a Terminal and type alsamixer --> then enter-->next choose F4-- then I choose Rear Mic in my case since I have my headset plugged there. I used the left, right arrows to get there then up and down arrows to raise or lower the volume. Once done I pressed ESC. That was all I needed to do.  I should mention make sure you have the correct sound card and other setting on sound preference.  Hope this helps! :D

This works, but **every** time I logout/login (or restart) I lose this settings.
Where/how can I fix this?

Cheers,

---

### Post by ECPCLINUX on 2011-05-30
Hi Emanuele_Z,  I honestly would not know why the setting is not staying for you. For me it stays without any issue. Hopefully, someone who know more than me can help you. If no one answer may I suggest you start a new thread? Maybe that way you'll have better luck. Sorry I could not be of more help. Good luck!!!

---

### Post by Emanuele_Z on 2011-05-30
Thanks man, I'll try.

Cheers,

---

### Post by ECPCLINUX on 2011-05-30
No problem Hope you find your answer soon.

---

