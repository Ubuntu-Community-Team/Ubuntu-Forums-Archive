---
title: "Sound only on right channel - snd-ice1724"
date: 2005-09-10
forum: Hardware &amp; Laptops
---

### Post by cgreentx on 2005-09-10
After going through all the battles required to get Hoary installed and working on my Dimension 8400 with dual head operation on my NVidia 6800 I'm down to one last major hurdle before I can use this as my primary desktop OS.  

At installation, sound worked fine on my M-Audio Revolution, but only on the right channel.  I found lots of comments about earlier releases and having to install drivers to get it working at all, so I grabbed the latest ALSA drivers and libraries from the site (1.09b) and jumped through all the hoops to compile and install these modules.  After installation I am still in the same place I was prior, only sound fromt he right channel.  Everything has worked great for years in Windows with this sound card so I know that everything is connected properly.  ;-)  

I'm looking for any help that can point me in the right direction. 

1.  How can I verify that I'm running the modules I installed and not the default ones?
2.  Has anyone successfully gotten at least stereo, if not multi-channel, out of this card?

Chris Green

---

### Post by Pyroman[FO] on 2005-09-10
I had this same problem, I got it figured out.

Go to the volume control, by default there won't be any channels listed.  Enable all the channels.  Now on the first one, I went and muted it (clicked the speaker at the bottom of the slider) and unmuted it, and that fixed it.  It's coming out the left and right speakers, but it's not surround.

---

### Post by cgreentx on 2005-09-12
[QUOTE='Pyroman[FO]']I had this same problem, I got it figured out.

Go to the volume control, by default there won't be any channels listed.  Enable all the channels.  Now on the first one, I went and muted it (clicked the speaker at the bottom of the slider) and unmuted it, and that fixed it.  It's coming out the left and right speakers, but it's not surround.[/QUOTE]

That worked...  I apparentlyhave to do it on every single boot, however.  :(  This is the case in both 5.04 and 5.10 Preview.

Chris Green

---

