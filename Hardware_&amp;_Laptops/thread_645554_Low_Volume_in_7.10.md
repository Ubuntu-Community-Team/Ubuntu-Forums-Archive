---
title: "Low Volume in 7.10"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by sorryd on 2007-12-20
I can only get very low volume on my desktop system. I believe it is a realtek chip but it shows up as HDA Intel ALC880.

I have checked every post I can find and I have exhausted all my options (including doing the steps at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) )

I have PCM and Front maxed, and can only get the speakers to the level where I can listen to music quietly, but the level is about 1/5 that in Windows.

My system is a Sony Vaio VGC-RA73S. I believe it contains an ASUS mobo with an INtel 945P chipset. 

Any assistance would be appreciated as I really don't want to go back to Windows because of something so trivial.

Cheers.

---

### Post by morppheu on 2007-12-20
Use alsamix to configure it. :)

---

### Post by nickoli_02 on 2007-12-20
I'll just expand on the above post. open up a terminal, type alsamixer. In there try playing with the volume controls on the different channels. I think I had this problem before where one channel was muted and I couldn't hear anything. Hope this helps ;)

---

### Post by sorryd on 2007-12-20
I should have been clearer in my initial post. I have tried alsamixer and I have the sound maxed out in that.

---

### Post by Bartender on 2007-12-22
Also having problems with sound, on an Acer 5920.  Headphones work fine, only getting the right channel on the laptop speakers.
Until I read this post didn't realize that access to alsamixer was so easy.
The utility says I have HDA Intel card, and Relatek ALC888 chip.  I learned something right there, thought it was one or the other!
Still, resetting everything I could find under "Sound" and in gnome applet to Realtek didn't seem to fix problem.  Still only right channel on laptop, both with headphones, and headphone doesn't kill laptop speakers regardless of the switch setting in gnome applet.

---

### Post by srunni on 2007-12-22
I have a Sony VAIO RC110G and have this exact same problem. I modified a configuration file and it works now. Let me see if I can find the solution again.

EDIT: I modified /etc/modprobe.d/alsa-base to have "options snd-hda-intel model=vaio" in it, though when I checked it now, that line is commented out, and everything is working OK. The problem is only partially remedied however - since I have a sound system capable of high volumes, I just turn up the volume all the way, and it sounds fine. I'm guessing that after upgrading to Gutsy (I did a clean install) I didn't bother to edit the config file again.

---

### Post by jcsteele on 2007-12-22
[http://ww2.coastal.edu/jcsteele/gutsy-S4134.html](http://ww2.coastal.edu/jcsteele/gutsy-S4134.html) has the solution for this exact problem on my Toshiba Sateliite notebook.

//jcs

---

