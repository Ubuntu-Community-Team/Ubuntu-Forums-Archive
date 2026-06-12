---
title: "Sound card needed"
date: 2015-12-15
forum: Hardware
---

### Post by asigurnjak on 2015-12-15
I need a separate sound card  for headphone output  for MIXXX.  After looking around  there is zero info on Ubuntu compatibility anywhere and ALSA website is bunch of gibberish for me  . 
I prefer to shop [http://www.memoryexpress.com/](http://www.memoryexpress.com/)  at local store in Winnipeg  , Canada . 
Could some one take a look at their offering and see if  an of their PCI/ PCI-E  sound card are compatible with Ubuntu 14,04 .  I was looking at 
[h=1][SIZE=1]Creative Labs
[/SIZE][/h]
[SIZE=1]             [/SIZE][h=1][SIZE=1]Sound Blaster Audigy Fx 5.1 Sound Card, PCIe  [http://www.memoryexpress.com/Products/MX55197](http://www.memoryexpress.com/Products/MX55197)[/SIZE][/h]they are sold out right now but  they are coming in a weeks time .  
My needs a minimal really . I have working onboard audio  and just need additional  headphone output  to  mess with MIXXX a little bit.

---

### Post by Yellow Pasque on 2015-12-15
I think I would avoid the Audigy FX. [http://www.linuxquestions.org/questions/linux-hardware-18/getting-a-soundblaster-audigy-fx-to-work-4175505881-print/](http://www.linuxquestions.org/questions/linux-hardware-18/getting-a-soundblaster-audigy-fx-to-work-4175505881-print/)

Consider the Asus Xonar DGX (PCI-e): [http://www.memoryexpress.com/Products/MX40246](http://www.memoryexpress.com/Products/MX40246)
One thing that might not work on it is the automatic switching/detection of front headphones connection. But if you don't frequently switch back and forth between the front panel connector and other outputs, it's not a big deal. You just have to set it once in alsamixer and be done with it.

---

### Post by Bucky Ball on 2015-12-15
If you only need an additional headphone output and not a separate headphone *_mix_*, then why not by a stereo mini-jack double adapter? It plugs in to the headphone jack and gives you two stereo headphone jacks with identical output (there is no way of changing that pre because they are coming from the same output jack). 

You could also consider a small headphone amp. Headphone jack out of the computer to 2/4/6 output headphone amp ...

Just suggesting. :)

---

### Post by Yellow Pasque on 2015-12-15
Another solution that could work is retasking an extra jack to be a headphone jack. [http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/](http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/)
I don't know if that would be sufficient for mixxx or not. Also, it may require some wrangling to get pulseaudio to see the new headphone jack as a separate device.

---

### Post by asigurnjak on 2015-12-15
Thank you all for your suggestions . First i will try to reassign mic port  . it will cost nothing if it works . If no luck Xonar it is  . 
I guess this is solved for now .

---

