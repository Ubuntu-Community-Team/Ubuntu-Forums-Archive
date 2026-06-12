---
title: "Mic not work"
date: 2008-05-26
forum: Hardware
---

### Post by max246 on 2008-05-26
I have the sound card integrate 
"00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)"
and not work mic!
I have update the driver alsa but nothing is not changed...

My laptop is HP Compaq nx6325

I have the second problem with this card, on insert the jack of headset the speaker not switch off but I listen the sound between.
Only I insert the jack before boot the sound in the speaker switch off but I remove the jack the speaker not switch on....

Sorry for my bad english...

---

### Post by nicedude on 2008-05-26
try opening a terminal and running the command "alsamixer" without quotes and see if the mic volume is turned up. If not turn it up and try again.

---

### Post by max246 on 2008-05-27
> **nicedude said:**
> try opening a terminal and running the command "alsamixer" without quotes and see if the mic volume is turned up. If not turn it up and try again.
I try but not work!

---

### Post by max246 on 2008-05-27
help!:(

---

### Post by hotweiss on 2008-05-27
This is how I got my mic working:

A) Righ-click on the speaker in the task bar and select Open Volume Control.

B) Select Edit from the menu, and then select Preferences.

C) Click on the boxes besides Capture and Capture 1.

D) Now your microphone should be working.

---

