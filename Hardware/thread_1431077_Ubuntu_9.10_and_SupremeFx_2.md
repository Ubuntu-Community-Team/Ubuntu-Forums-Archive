---
title: "Ubuntu 9.10 and SupremeFx 2"
date: 2010-03-16
forum: Hardware
---

### Post by Darkenss on 2010-03-16
Hi, i´ve just recently installed Ubuntu 9.10 on my system, and everything works perfectly except for my Mic!

here is my system.

Intel i5-750
Asus Maximus Formula 3 with SupremeFX 2 soundcard (PCI-e)
ATI 4870 1gb
4gb corsair XMS
and 3.4 tb of disk space. 


so i´ve tried various things around the forum but i cant get the mic to work. 

should i install the creative beta x-fi driver, done it one time but after i had installed it all sound disappeared. 

so right now i´m sitting in windows wanting to go back to ubuntu, but i realy need my mic! :S

---

### Post by ajgreeny on 2010-03-16
Just in case you have not tried this yet, run ```
alsamixer
``` in terminal, and use the cursor keys to navigate and set levels of the various sliders, "M" to mute and unmute, and Esc to quit and save settings.  You may find that there is something in there that is set too low, or the selection of microphone is incorrect.

Alsamixer shows many, many more possible sound configurations than just about all other applications available.

You may also want to make sure you have **padevchooser** installed as well, as it can make things like recording levels much easier to set than any other way.

---

### Post by Darkenss on 2010-03-16
Tried what you said, it made now difference. 

but when pushing "M" in alsamixer i get now diffrence. 

and i can only see 3 things in there. 

Master -> PCM -> Capture

my card should be a 7.1 sound interface with digital + spdif

i don´t use those things so i dont really care but i want to have at least my mic turned on!

---

### Post by ajgreeny on 2010-03-16
Try opening the pulseaudio volume control that will be there from padevchooser which I told you to install.  In the volume control window that opens go to the recording tab, then start a recording program eg gnome sound recorder, and start to record anything at all.  You may find that you can play around with the volume control device setting and choose something that does work by clicking on the box that says something like **analogue duplex stereo**.  Just try everything and you may be lucky.

---

