---
title: "No headphone jack sense"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by PurposeOfReason on 2007-12-03
I just got the latest alsa drivers following [this howto](https://help.ubuntu.com/community/HdaIntelSoundHowto). I added the line "options snd-hda-intel model=vaio" to my /etc/modprobe.d/alsa-base file too. After it's all done, I get sound out of the headphones, but it still comes out of the speakers. On the switches tab of the volume control, I have a line-in and microphone option, but no jack sense option. Is there something else I have to do? This is on a Sony Vaio VGN-FZ145E.

---

### Post by jjalocha on 2007-12-03
Maybe you could open a terminal, and try with the 'alsamixer' program. It's a little bit primitive, but does the job very well. Just type 'alsamixer' in the command line. With the LEFT/RIGHT arrow keys move to the field labeled <Line Jac> or something like that. With many cards, you catually can "scroll" outside the screen, when you have many controls. If you have an Line Jack Sense entry, you can try unmuting it with the 'M' key. Do this with the cable unplugged.
Hope this helps!

---

### Post by PurposeOfReason on 2007-12-03
I only have a Master and PCM there.

---

### Post by jjalocha on 2007-12-04
It seems that you are not alone with this problem ([http://ubuntuforums.org/showthread.php?t=624072](http://ubuntuforums.org/showthread.php?t=624072)). Try asking othe VAIO owners for help.

---

### Post by PurposeOfReason on 2007-12-05
The second post in that thread did it. There is still nothing for headphone jack sense, but it still works.

---

