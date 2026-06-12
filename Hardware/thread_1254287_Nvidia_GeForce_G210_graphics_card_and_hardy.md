---
title: "Nvidia GeForce G210 graphics card and hardy"
date: 2009-08-31
forum: Hardware
---

### Post by jbcoe on 2009-08-31
I recently got an HP Pavilion Slimline s5128uk Desktop PC.
The graphics card is an Nvidia GeForce G210. I'm using hardy heron on it (LTS release) and am having trouble with the graphics card.
Native X support is good enough for desktop use at 1280x1024 but fullscreen flash playback causes crashes of the browser. I've tried installing the nvidia driver from ubuntu packages, from envyng and fron nvidia's own driver source without success.
As this card is relatively new this may be fixed by a new driver and waiting is probably my best bet. I've started this thread so that other owners of this card can share their thoughts and findings and find out more easily when full support is available.

---

### Post by hairybarrier on 2009-09-01
[COLOR=#333333][FONT=arial][FONT=Arial][SIZE=2][/SIZE][/FONT][/FONT][/COLOR]    I'm having this problem too. I just got an HP Pavilion e9105z with a GeForce G210. The jaunty install went fine, but it will only install the generic drivers for the monitor. I've tried envyng, nvidia glx 180, and nvidia settings, and it just seems to crash the video. It's connected via the HDMI cable now. I'm going to try it with DVI tonight. Any help is appreciated...
  [COLOR=#333333][FONT=arial] [/FONT][/COLOR]

---

### Post by hairybarrier on 2009-09-03
Well, I re-installed jaunty again last night with a VGA cable and the alternate DVD. With the HDMI cable there was a black border around my screen, and this is gone with the VGA cable. After the install the best I could get was 800x600 resolution. I tried some of the hacks on the web, edited the xorg.conf file, etc but it still doesn't work right. I gave up and put my HDMI back on and now I get the option for 1024x768, so it looks better, but the black border box is back. I found the nvidia 190 version on their site. I'll try this over the weekend and update the post.

---

### Post by jbcoe on 2009-09-05
I just installed the 190 drivers from the nvidia website (beta drivers) by running the install script. It works. It works well too. Not only do compiz extensions work but the incredible noise from the PC has dropped to a low contented hum. I've no HDMI kit to test out (yet).

---

### Post by jbcoe on 2009-09-06
compiz support works well with one exception: I get missing characters and failures to update in xterms. This is annoying enough for me to turn off compiz for now. Fullscreen HD flash video (courtesy of BBC iplayer) runs smoothly.

---

### Post by bhaverkamp on 2009-09-15
I just installed nvidia 190.36 drivers and all is well. My dual monitor setup is working and everything.

---

### Post by kenneho on 2009-09-20
I installed the 192.32 beta driver, and everyting appears to work perfectly. Cool!

When the driver comes out of beta, will it be included in on of the Ubuntu repos, or will I have to download updates manually?

---

