---
title: "no sound in 13.04"
date: 2013-04-28
forum: Hardware
---

### Post by Worp8d on 2013-04-28
Hi,

I just upgrade to Lubuntu 13.04 with no problems except no sound. This seems like a somewhat common problem in Ubuntu but I've tried making sure alsamixer isn't muted/low, removing pulseaudio (and reintalling) and I'm about out of options. Is there anything I can do, or a link anyone can recommend?

Thanks.

---

### Post by SJR Dorset on 2013-04-29
After upgrade to Xubuntu 13.04 I also experience no sound. After searching the forums I found that the problem was related to a bug in the kernel relating to HDMI sound.

I fixed my sound by updating to kernel 3.8.8 using the following method:

[http://blog-darryldias.rhcloud.com/tag/debian-kernel/](http://blog-darryldias.rhcloud.com/tag/debian-kernel/)

---

### Post by architectadrian on 2013-04-29
I have the same problem. After an upgrade from 12.10 to 13.04, the video was broken, I couldn't repair so I wanted to reinstall the system. I downloaded an iso image from the ubuntustudio site, but it was broken (wrong checksum), so I downloaded another image and reinstalled the system, but this time I had no sound...
Any suggestions, aside a kernel update?
Thank you!

---

### Post by mathmisfit on 2013-05-02
I recently installed Lubuntu 13.04 and my sound was not working.  Here's what I did that seemed to work:
1. I went to the Lubuntu Software Center.  It can be found in System Tools in the Lubuntu Menu.
2. In the Get Software tab, I clicked on the Audio & Video category.
3. I scrolled down to "Pulseaudio volume control" and hit the Add to the Apps Basket button in the lower right hand corner of the window.
4. I went to the Apps Basket tab and clicked the Install Packages button.
5. Once it was installed, I went to Sound & Video in the Lubuntu Menu.
6. I opened the PulseAudio Volume Control.
7. I went to the Output Devices and made sure nothing was muted.
Here's where things became a little trial and error:
8. I went to the Configuration tab and tried a few different choices on the Profile menus until I found one that worked.  For me, I could turn onboard sound off (this was the first Built-in Audio for me) and chose Analog Stereo Output for the Soundblaster utput Devices tab and made sure that none of the output devices were muted.  (I had two devices which I assume correspond to a Silicon Integrated System (SiS) onboard sound card and a Soundblaster sound card.)
Here's where thicard (this was the second Built-in Audio for me).

Now my sound works!

I hope this helps someone.  This is my first time responding, so my apologies if I was too wordy.  Definitely no offense meant to anyone.

---

### Post by Toitovna on 2013-06-12
I had this same problem - turns out Lubuntu was trying to output the audio through my monitor instead of my speakers - mathmisfit's suggestion worked great! thanks

---

### Post by momist on 2013-07-11
I have had the same problem here.  My machine (old home-brew tower desktop) has had very many versions of Linux on it now, with a separate /home partition.  I had trouble some long time ago with the microphone input to the Asus MB on-board sound system, so I fitted a cheap as chips used soundblaster card.  The output audio from this was rubbish, so I went back to using the on board output but the soundblaster mic input.
When I loaded Lubuntu 13.04 today, I ran into the no sound problem, and looked for something to configure the sound.  There is NOTHING in the default install that lets you choose the hardware configuration, or anything else sound related.  Thanks are due to mathmisfit for pointing me in the right direction.  I had gathered the misinformation that Lubuntu didn't use pulseaudio, and perhaps I would have found the answer myself if it wasn't for that.

Thanks mathmisfit.  \\:D/

---

