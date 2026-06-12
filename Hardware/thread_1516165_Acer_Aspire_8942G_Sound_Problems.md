---
title: "Acer Aspire 8942G Sound Problems"
date: 2010-06-23
forum: Hardware
---

### Post by raoulvb on 2010-06-23
Hello all,
 
i have installed ubuntu 10.4 on my brand new acer aspire 8942G. At the beginning everything looked fine. Sound worked well, until i plugged my headphone / microphone. Mic was dead and headphones did not react.
 
i searched www, and found [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/549514](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/549514) 
 
(the last comment is mine)
 
i installed the linux-alsa.modules (from the alsa dev source) and the microphone and headphonejack worked finally. 
 
The problem is, that the headphones only seems to mute 2 of the 6 speakers inside the laptop. So the other still plays the sound even if the headphone is plugged in. 
 
I did not find any useful information to solve this issue. The only thing i could observe, was that the alsa mixer has a pcm / headphone and speaker leveler, but pcm controls speaker and phones, while phones controls also speaker and phones. Speakerleveler ist without function.
 
I know that the aspire has a ALC 680 Chipset inside (or is it 670?) :)
 
my question is, is there a possiblity to configure alsa this way, that i only uses the 2 frontspeakers, ignoring the "others".
 
This would be a useful workaround, just "deactivate" all speakers except of the "left/right" so everything would be mute when pluging in a headphone :)
 
thank you very much

---

### Post by fballem on 2010-07-02
When I did my clean install of Ubuntu 10.04 on my Acer Aspire 8942G and installed the Linux Alsa modules from ubuntu-audio-dev, I never got sound out of more than one speaker.

I would be very happy if I got sound out of all six speakers. Can you tell me how you did this?

Thanks,

---

### Post by fballem on 2011-03-27
Tripped across this while reviewing my subscribed threads. I have done a clean install of Ubuntu 10.10 and the sound is working correctly.

---

