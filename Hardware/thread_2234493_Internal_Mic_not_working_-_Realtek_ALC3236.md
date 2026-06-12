---
title: "Internal Mic not working - Realtek ALC3236"
date: 2014-07-15
forum: Hardware
---

### Post by Prabhakar_Bhat on 2014-07-15
I have [COLOR=#141823][FONT=Helvetica]ASUS X552EA-SX006D laptop. ```
alsamixer
``` shows 2 devices, [/FONT][/COLOR][COLOR=#141823][FONT=Helvetica]Realtek ALC3236 and ATI R6xx HDMI. Default is Realtek. Though sound output works, input doesn't.

Help please![/FONT][/COLOR]

---

### Post by veddox on 2014-07-15
Are you sure you turned the microphone's volume up? In my experience, it seems to be at 0% by default, making it seem like it's not working (took me a while to figure out ;-) )

System Settings -> Sound -> Input    
Adjust the input volume slider.

---

### Post by Prabhakar_Bhat on 2014-07-16
I installed pavucontrol, and it shows two input devices: Internal Microphone and Microphone unplugged. If I select Microphone unplugged, it works. That looks weird to me.

---

### Post by vivichrist on 2014-11-23
you have to invert the mic inputs somehow... because internal mic is actually external mic etc. I tried 'option intel-hda-intel model=inv-dmic' doesn't fix it but I'm going to say the the fix could be something like that.

---

