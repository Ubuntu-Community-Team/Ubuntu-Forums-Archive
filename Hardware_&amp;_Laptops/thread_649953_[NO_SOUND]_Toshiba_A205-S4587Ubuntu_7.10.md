---
title: "[NO SOUND] Toshiba A205-S4587/Ubuntu 7.10"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by malkateb on 2007-12-25
Hi,

I'm having hard times with the sound of my laptop. My laptop is Toshiba A205-S4587 and I'm using Ubuntu 7.10. The problem is that I do NOT have any sound on my laptop. That's, the sound does NOT work and the volume control does NOT work as well!

Any idea to help would be much appreciated!

---

### Post by eggdeng on 2007-12-25
Post the output of ```
aplay -l
```( lowercase L, not 1).

---

### Post by malkateb on 2007-12-25
aplay: device_list:205: no soundcards found...

---

### Post by eggdeng on 2007-12-26
From another thread [http://ubuntuforums.org/showthread.php?t=643593&highlight=Toshiba+A205-S4587]("http://ubuntuforums.org/showthread.php?t=643593&highlight=Toshiba+A205-S4587")
it looks as if your sound card is a
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
You can check this by running ```
lspci | grep Audio
```
The driver for this card is snd_hda_intel. Run ```
lsmod
``` to see if it is loading. If not, add the line ```
snd_hda_intel 
```to your /etc/modules file and reboot. If all goes well, you should now see output from aplay -l but you will not have sound at this stage. This should help to get you started,but be prepared for a long slog.
There is a thorough sound troubleshooting walkthrough at
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by malkateb on 2007-12-26
Thanks for your attention. But, your solution did NOT work. I still get the same error from the "aplay -l" command:

aplay: device_list:205: no soundcards found...

---

### Post by malkateb on 2007-12-27
Experts, 

I'm still looking for help...

---

### Post by allforcarrie on 2007-12-31
I cant find anyhting that works on this model for my friend.

---

### Post by hsuwb on 2008-01-06
Hey malkateb, 
I'm no expert, but I got my sound working on the exact same computer A205-s4587 with 7.10 using the instructions in this thread:[ http://ubuntuforums.org/showthread.php?t=568463]("http://ubuntuforums.org/showthread.php?t=568463") I had to make some changes in the instuctions to get it to work for 7.10, I explained the changes in my reply on that thread (Post #10).

---

