---
title: "HP dv9542 songs/movies play but i hear no sound"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by sotos on 2007-10-15
Hello,I'm pretty new to Linux so please bear with me :)

I've installed Ubuntu 7.10 release candidate and so far i love it.except for one thing.
I have no sound and the mute/unmute button on my HP dv9000 series remaing orange (muted).By pressing it i can see the onscreen sound display mute and unmute,but the button remains orange at all times.
Now,when I start a song/movie it opens up the corresponding player normally and i can see the equalizer going up and down which means the song/movie is playing.

However i can hear no sound from either the speakers or headphones.

I've typed "aplay -l" in the terminal and i got this:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

by typing "alsamixer" I get:
 Card: HDA Intel                                                             
&#9474; Chip: Realtek ID 268                                                        
&#9474; View: [Playback] Capture  All                                               
&#9474; Item: Master [dB gain=-3.00, -3.00] 

Then below that i get two vertical columns entitled  "MASTER" and "PCM".They're maxed and unmuted.I also get two boxes called "CALLER I" and "OFF-HOOK".Those are unmuted too.

On device manager i get:82801H(ICH8 Family) HD audio controller

I tried adding options "snd-hda-intel model=realtek" on .modprobe.d/alsa-base but still no luck.

Any help at all would be greatly appreciated.I love the functionality of linux and i'd like to get rid of windows asap,but not being able to listen to music is a deal breaker I'm afraid :(

---

### Post by sotos on 2007-10-16
Really?nobody has ever encountered this problem?

---

### Post by antido on 2007-10-19
I have also encountered this problem, I installed ubuntu 7.10, and didn't get the sound to work.
I also have a Realtek ID 268.

I'm pretty new to linux, so any help would be appreciated 

(my laptop is an acer aspire 5710)

---

### Post by DRAGONPOWER on 2007-10-19
hello. i have an HP dv9000 too and i have the same issue u mentioned.

There's a thread which will be updated about these HP laptops to get sound working. hopefully tomorrow there will be a fix ... 

PS: i have indeed tried all the methods u can possibly find to get alsa, realtek, ich8 intel hd audio working ... even compiling the alsa modules and that ... still nothing.

---

### Post by jhong on 2007-10-21
I have the same problem too.

---

### Post by jumpoutofatree on 2007-10-22
i have the same problem as well, but i have gotten it working before i just don't remember how so it's twice as aggravating

---

### Post by iPhant on 2007-10-22
This is what i did on my laptop(Toshiba u305), and it actually worked:):

First I found a guide to install alsa-source, (  [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") ) f.ex


sudo nano /etc/modprobe.d/alsa-base 

and edit(wrote this line at the end:

options snd-hda-intel model=[COLOR="Red"]ALC268[/COLOR]

rebooted and suddenly the sound worked :D

---

### Post by rulodos on 2007-10-24
HI, I just try your solution, i have an HP Pavilion 9535nr model, with realtek 268 driver in it, but it didt't work, my master volume is in high volume,but no i cant hear anything, i just follow your solution but nothing happens, i apreciate if you can help me, thank you.

---

### Post by Agnus on 2007-10-24
I have the exact same problem with HP Pavilion 6600. The mute led stays always orange and I hear no sound no matter what.

---

### Post by alterKrieg on 2007-10-25
I've got this same problem and can't figure it out.  I've looked through every forum string I could find.  Is there nothing else to  be done?

---

### Post by micahthepenguin on 2007-11-04
I finally got my sound working after looking [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133").

I have an HP Pavilion dv9500t running Ubuntu 7.10 Gutsy.  My audio chip is "Realtek ID 268".  Previously I had the exact same problem described by sotos.

Instructions:
Using System>Administration>Synaptic Package Manager, install **linux-backports-modules-2.6.22-14-rt**.

Then in a terminal run **sudo gedit /etc/modprobe.d/alsa-base**
At the bottom of the file, add the following line:
**options snd-hda-intel model=hp**
(If you have a different model laptop, you may need to replace "hp" with something else.  Look in /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz under the "Module snd-hda-intel" section for other options here.)
(Also, from the bug report referenced above, it is sometimes necessary to add "position_fix=1" as well as "model=<MODEL>".  I don't know why or what this means.)

Restart your computer and hopefully sound will work.

One problem with this fix is that the laptop speakers don't mute when you plug in headphones.  I don't yet know how to fix this permanently, but you can manually mute/unmute the laptop speakers with the alsamixer utility (type **sudo alsamixer** in a terminal, use arrow keys to move to "Front" and press 'm' to mute).

Hope this helps.

---

### Post by antido on 2007-11-05
Fantastic!!! That fixed it!

I installed the backport modules as you described, and everything works!

You truly are, an hero.

---

