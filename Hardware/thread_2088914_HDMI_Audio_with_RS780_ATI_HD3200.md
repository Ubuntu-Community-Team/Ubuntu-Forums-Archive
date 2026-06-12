---
title: "HDMI Audio with RS780 ATI HD3200"
date: 2012-11-27
forum: Hardware
---

### Post by robn30 on 2012-11-27
So I have been doing a lot of looking on Google to try and figure out  how to get HDMI Audio with my laptop with HD3200 graphics.  I am  currently running Ubuntu Precise 12.04 with Kernal 3.2.0-33.  I have tried the Grub  modification using radeon.audio=1 and still nothing.  I did that to the  /etc/default/grub and /boot/grub/grub.cfg files.  I then ran  update-grub.  Still no audio to my TV.  When I run pavucontrol and run  speaker test from the sound settings, the sound indicator under  pavucontrol for output shows an indication like something is happening  but nothing is heard at my TV speakers.  BTW this occurs with  radeon.audio=1 and not turned on in the grub at all.  So no difference  with or w/o this switch.  Can someone please tell me what to do here, I  would really like some HDMI audio.  Also the Kernal Module listed for  HDMI is snd-hda-intel.  Not sure if that is the correct driver or not  for the RS780.  Any help would be much appreciated.

---

### Post by Yellow Pasque on 2012-11-27
snd-hda-intel is the correct driver. Make sure you're using a good HDMI cable (preferably 1.3 or higher compliant).

---

### Post by robn30 on 2012-11-30
> **Temüjin said:**
> snd-hda-intel is the correct driver. Make sure you're using a good HDMI cable (preferably 1.3 or higher compliant).

Wow, I don't know if it was the simplicity of your post or what but it got me thinking.  I knew the cable was good cause I have used it with my other laptop with Intel Graphics and Audio.  Either way I tried hooking that up to my TV and to my surprise no sound.  At that point I instantly knew that I had been a big donkey!  Cant have sound when you have disabled your TV speakers in the settings of the TV.  Guess all those years with the surround sound has jaded me when it comes to simple basic sound from your TV.  Anyway I am thrilled that both my machines due in fact produce sound from the HDMI port.  Yea.  Got to just laugh at yourself sometimes.

---

