---
title: "realtek audio static very hard to hear audio"
date: 2017-12-27
forum: Hardware
---

### Post by michael14 on 2017-12-27
My motherboard is the ga-970a-ds3p fx.. It has realtek 887 audio and whatever reason for a few seconds the audio is very distorted/static very hard to hear anything at all.. You can hear the distortion/static in this video i have uploaded describing the issue. Please help

[https://www.youtube.com/watch?v=iirmn9KKz7k&feature=youtu.be](https://www.youtube.com/watch?v=iirmn9KKz7k&feature=youtu.be)

I just installed Ubuntu today and i just want it to work as it should.. :(

I'm on Ubuntu 16.04.3 LTS

---

### Post by michael14 on 2017-12-28
It seems the these commands fixed it.. 
```

killall pulseaudio; rm -r ~/.config/pulse/* ; rm -r ~/.pulse*
wait 10 seconds then doing
pulseaudio -k 




```

But its not a full fix as rebooting makes the issue of course come back. How do i make this fix a permanent fix?

---

