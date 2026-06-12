---
title: "Sound card Realtek ALC662"
date: 2008-09-29
forum: Hardware
---

### Post by resolv_25 on 2008-09-29
I'm using Ubuntu 7.10 - Gutsy, and have sound card Realtek ALC662, integrated on ASUS M2N MX SE.
Now, loudspeakers are working fine, but not a microphone. 
By default, sound capture is ALSA-Advanced Linux Sound Architecture, 
device: HDA Nvidia (Alsa mixer).
I changed this to Realtek ALC662 that is shown on the list (and this is correct device indeed).
Still, microphone is not working properly with any of combination, sound capture OSS, or ACL analog, device set as Nvidia or REaltek, microphone set as front, or line in.

I've read that is possible that ubuntu switches the microphone and loudspeaker , tried to switch the jacks, also, front or back, no success.

From the Realtek web site, I've downloaded and installed their latest driver.
Still, no luck. 

Also, tried to change configuration on Skype, from default to Nvidia, but this doesn't make much sense, and it is not working anyhow.

Pity, because, I put effort to install several ubuntu in company that I'm working for, and this could be the reason to return to Windows, which I wouldn't prefer.

---

### Post by resolv_25 on 2008-09-29
Of course, microphone is not set to mute, as well as line in.

---

### Post by resolv_25 on 2008-10-16
Uf, no replies at all...
I've upgraded machine to Ubuntu 8.04 Hardy, but no success.
It might be that Skype isn't working properly with this sound card.

Does anyone have suggestion which sound card is certainly working with skype on Ubuntu ?  :confused:

---

### Post by goohman on 2008-11-11
I have the same bord I didnt tuch a thing and skype works.....my sound I very low though

---

### Post by resolv_25 on 2009-02-26
Interesting
Can you tell me how is setup in your System-Administration-Sound 
I have option Sound playback autodetect, sound capture OSS, device Realtek.
On skype, there is a default option ( Nvidia is other option) ?
Although , I beleive that I've tried all other combinations, with ALSA, and so on.
Actually, I've added an old PCI card - ensoniq, it is working.
Still, there are some other same machines in company where I'm working, and would be fine to have this possiblity.

---

