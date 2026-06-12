---
title: "ubuntu toshiba m750 built in microphone"
date: 2009-06-02
forum: Hardware
---

### Post by X-Kent on 2009-06-02
Hello everyone.
I can't get my built in microphone to work in ubuntu 9.04 jaunty.
I followed this guide to get the sound working: 
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700)
All sounds work perfectly, but not a built in mic (if I connect the external one to the front mic port it works)
I have tried all options I have in the volume manager and all combinations but still my microphone doesn't hear any sounds.
If I rise the "mic boost" volume in volume manager I can hear that my microphone is working (it makes noise like there is something on the line) but the noise is not related to what I hear, even if I scream there is no change in that noise.
Can anyone land me a tip where I may continue searching for solution ?
Toshiba portage m750 s7202, ubuntu jaunty. Realtek ALS268 chip.

Thanks in advance, S.A.

---

### Post by X-Kent on 2009-06-09
Still no solution

---

### Post by twiggyness2000 on 2009-06-15
I had the exact problem last week when I tried to get a mic working for skype.

Try different settings in the [Recording] tab of your volume control settings.
Still not working?  Then go to System > Preferences > Sound > Sound Capture and test all the different devices in that drop-down box.  My mic has about a half-second delay before the sound outputs to speakers during the test.  Mine finally worked when I set it to Analog ALSA.

---

### Post by Yonco on 2009-06-22
Hey. 
I had the same problem with my m750. 
what I did was open up kmix (I'm using kubuntu) and change the input source from 
"mic" to "front mic" now I can use my mic. 
hope it works. 
BTW 
any advancement on the Xjournal jumps problem? 
what about the graphics card? do you utilize it to the full? 
all the best. 
Yoni

---

### Post by X-Kent on 2009-06-30
I tried switching it to front mic, mic seem to start working in skype but after a minute or two it starts lagging and I see my CPU usage go crazy.

There is still nothing about Xournal bug, I just click "undo" every time I get strange lines, and it seems having "pressure sentensivity" turned on reduces the chance of getting one. Anyway it's very annoying.

Utilize the video card ? It just works OTB and I didn't try to do anything special with it... "World of Goo" game worked perfectly under wine.

---

