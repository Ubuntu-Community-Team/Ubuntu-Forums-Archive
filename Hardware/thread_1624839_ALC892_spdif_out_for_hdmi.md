---
title: "ALC892 spdif out for hdmi"
date: 2010-11-18
forum: Hardware
---

### Post by tuxscooter on 2010-11-18
hi!
1st of all, sorry for my bad english...

I have a Gigabyte 870A-ud3 motherboard with ALC892 integrated soundcard.  This card has 3 spdif out:
1. optical, 
2. coaxial, and 
3. internal for connection with videocards for HDMI sound output. 

All spdif out are unmuted in alsamixer, however i can't find a switch for the internal spdif_out.

I can't make the 3rd to work. Any ideas?

cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
uname -r
2.6.35-22-generic

thx for help in advance!

---

### Post by jocko on 2010-11-18
On my motherboard, the spdif to hdmi connection works if I set pulseaudio to use either "Digital Stereo" or "Analog Stereo", then it's just a matter of activating the hdmi output from my nvidia graphics card...

---

