---
title: "Toshiba Satellite A135-S4527 Sound Help"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by vanden12 on 2007-05-12
I been a Long time ubuntu user but i cant seem to figer this out 

My dad laptop broke a short while ago so i went along and got this great 600 laptop from best buy the Toshiba Satellite A135-S4527

specs if you like [http://notebookreview-cnet.com.com/Toshiba_Satellite_A135_S4527_Pentium_Dual_Core_T2080_1_73_GHz_15_4_TFT/4507-3121_7-32405589.html?tag=sub](http://notebookreview-cnet.com.com/Toshiba_Satellite_A135_S4527_Pentium_Dual_Core_T2080_1_73_GHz_15_4_TFT/4507-3121_7-32405589.html?tag=sub)


After i got rid of all the crap that Toshiba put on there i made vista nice and clean,then i put sabayon on there all the hardware was working great even the sound expect for 1 major thing the wifi card so i posted in there forums and dident get any help.After trying to get it to work for hours i gave up and install ubuntu.THis got my wifi crad right away i was so happy i forgot 1 major thing the sound so after hours of install apps and fixing up for my dad i tryed to tell him how to put song on his ipod and no sound there was playback but no sound i tryed playing with the sound setup but got nothing out of it.


So any help you can give me to get sound working on there it will be great

---

### Post by vanden12 on 2007-05-13
Still need help can any one help me.

---

### Post by culorut on 2007-05-13
In terminal type in the following,

gksu gedit /etc/modprobe.d/alsa-base

Add the following to the bottom of the file,

options snd-hda-intel model=3stack
 
Save the file and reboot.

I cannot figure out how to disable the main speakers when plugging in my headphones but at least I have sound.

---

### Post by vanden12 on 2007-05-13
I fixed the headphone problem it a easy fix. All you do is in the volume control go under pcm click the chain and move the first one all the way down and there you have it headphone sound without pc speaker.

Also how did you finger out what to put so sound can work.

---

### Post by culorut on 2007-05-13
I had the same problem and found this thread,

[http://ubuntuforums.org/showthread.php?t=392350&highlight=toshiba](http://ubuntuforums.org/showthread.php?t=392350&highlight=toshiba)

---

### Post by Maverynthia on 2007-07-06
> **vanden12 said:**
> I fixed the headphone problem it a easy fix. All you do is in the volume control go under pcm click the chain and move the first one all the way down and there you have it headphone sound without pc speaker.

Also how did you finger out what to put so sound can work.

Doesn't work, it just mutes the left channel.

---

### Post by gwanath on 2007-07-08
> **Maverynthia said:**
> Doesn't work, it just mutes the left channel.

Yup...Same here

---

### Post by fletch229 on 2007-07-14
try this it worked on my toshiba l35-s2151 [http://ubuntuforums.org/showthread.php?t=473425&highlight=headphone+on+toshiba](http://ubuntuforums.org/showthread.php?t=473425&highlight=headphone+on+toshiba)

---

