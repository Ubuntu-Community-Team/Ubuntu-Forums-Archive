---
title: "Issue with Twinview, Metamodes"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by clockwork_alex on 2008-01-04
Hi!
I'm having a problem using a dual monitor configuration through twinview. I already spent a lot of time googling for answers but to no luck, I hope you can help me. 
So the problem is that I'm using  the " sudo nvidia-settings" app and it used to work fine in the beginning  I'd just hook up the cable to the laptop and select detect displays>configure:twinview>position:clones and apply. For whatever reason that stopped working, now I get this message: 

"Failed to set MetaMode (2) 'CRT-0: nvidia-auto-select @1440x900 +0+0, DFP-0: nvidia-auto-select @1280x800 +0+0' (Mode 1440x900, id: 64) on X screen 0

Would you like to remove this MetaMode?"

I click yes and nothing happens, so I click apply again and then get this message:

"Failed to set MetaMode (1) 'CRT-0: nvidia-auto-select @1440x900 +0+0, DFP-0: 800x600@60 @800x600 +0+0' (Mode 1440x900, id: 63) on X screen 0."

And it leaves me at that, with no image ever showing on the monitor.

Thanks in advance,
Daniel

---

### Post by overdrank on 2008-01-04
HI and welcome, I have seen that error on both my and my son's system and I used the rest button in the nvidia settings and then restartx  with ctrl, alt, backspace keys at the same time. Hope this helps and good luck!

---

### Post by clockwork_alex on 2008-01-04
I just tried that about 6 times and it didn't work... It keeps nagging me about the metamodes. Another odd thing is that it thinks my monitor is a CRT when it isn't (it's a SyncMaster 940BW), don't know if that may mean anything.

---

### Post by clockwork_alex on 2008-01-05
I eventually got it to display on  the monitor but now the image on it is all blurry and I can't even see the entire screen (the bottom bar for example). I already tried the configurations on the monitor but that didn't help much. 

thanks.

---

### Post by clockwork_alex on 2008-01-05
it's working fine now. the only caveat is that I have to restart X to either have a good conf for the monitor or a good conf for the laptop, I think that's because it thinks that there's no second monitor plugged.
Thanks everyone who posted/viewed!

---

