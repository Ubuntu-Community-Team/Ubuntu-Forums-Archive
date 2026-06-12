---
title: "My sound is so low i cant hear nothing!"
date: 2008-10-04
forum: General Help
---

### Post by Vertoxic on 2008-10-04
i just did the updates for ubuntu-
was listening to music just fine after restart the sound is super low on the laptop and the speakers that i have hooked up to my laptop!

---

### Post by Locutus_of_Borg on 2008-10-04
run alsaconf followed by alsamixer
both as root
during the second command you can raise the volume for all channels

---

### Post by pbpersson on 2008-10-04
The only thing I can offer is go into the mixer control and play with ALL the levels.

I played with the master, PCM, and CD - but did not get any volume until I turned the FRONT control all the way up.  It makes no sense to me, but that is what I discovered.

---

### Post by Vertoxic on 2008-10-04
> **pbpersson said:**
> The only thing I can offer is go into the mixer control and play with ALL the levels.

I played with the master, PCM, and CD - but did not get any volume until I turned the FRONT control all the way up.  It makes no sense to me, but that is what I discovered.
sweet that worked i don't understand what happend i didnt do anything to the sound. but thank you very much
- 
also **Locutus_of_Borg** could you be a little more specific? i want to understand what u mean...

---

### Post by Vertoxic on 2008-10-04
here is what i got

---

### Post by wolfen69 on 2008-10-04
i just did an install of ubuntu for a customer and had the same problem. i tried ```
sudo apt-get install libflashsupport
``` and it worked. supposedly this fixes a pulseaudio problem. hey, it's worth a shot.

---

### Post by Kinetic Being on 2008-10-04
open a terminal and type:

alsamixer

and navigate with the arrow keys, left and right to go left and right, up and down to conrol volume, and m to mute. make sure everything is unmuted (has a green box around the numbers) and at 100.

---

