---
title: "Problems with Gateway Solo 2500"
date: 2004-12-19
forum: Hardware &amp; Laptops
---

### Post by AE86_Racer on 2004-12-19
Hey all

Im kinda new to linux and did my first install last nite.  Im very impressed

One thing though, I cant seem to get any sound out of my soundcard

its a Neomagic MagicMedia256AV (nm256) and I get an error from something called alsactl saying there is no soundcard

I read a post earlier about this and got very lost trying to figure out what to do.  can someone help me out?  Im new to all this so I have no clue what does what and so on

thanks in advance

---

### Post by thelusiv on 2005-04-14
I have been trying to get sound working on one of these machines. It uses Alsa's snd_opl3sa2 driver. The modprobe line I use to load it is this:
```
sudo modprobe snd_opl3sa2 io=0x370 mss_io=0x530 irq=5 dma=0 dma2=1
```
I got this from [this page](http://www.thehayesweb.org/jhayes/solo2500.html#sound) on that laptop. When I load this it seems to work fine but then when I restart alsa I get lots of crazy errors. It says "Warning: 'alsactl store' failed with error message 'alsactl: save_state:1194: No soundcards found...'. Invalid card number."

Then, it beeps, pauses, outputs the usage instructions for amixer, and then beeps, pauses, outputs amixer usage... and keeps doing that until I press control+C a lot.

Any ideas anyone?

btw this is hoary.

---

