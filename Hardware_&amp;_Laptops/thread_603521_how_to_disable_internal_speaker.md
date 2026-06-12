---
title: "how to disable internal speaker"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by biocyberman on 2007-11-05
I am new to ubuntu and newbie to linux hardware management.
I installed Gusty Gibbon Desktop on Dell Optiplex GX620. The internal speaker won't turn off even when I plug in headphone. The "device manager" (device info viewer would be more appropriate :( ) in System>Preferences doesn't help anything to turn off that speaker. I also try to google but nothing applicable was found. Couldn't find out devices' list/configuration file neither :confused:
Would appreciate any direction.

---

### Post by smurphy_it on 2007-11-05
I used to have a similar problem at one point with different flavours of linux.  In my case, I had to re-compile my alsa sound drivers to fix the problem.  Thankfully, I don't have that problem anymore since Gutsy has been released.

Right click on the volume meter in your system tray and choose preferences I believe, then have a look at the different ones you have.... If you have one called pc speaker you may be able to disable it, otherwise, you may be stuck having to hack your driver or recompile it.

---

### Post by biocyberman on 2007-11-05
@veerakumar, smurphy_it: Thaks alot for your advice. Both ways may work. And even though I would avoid both of them if there was a quicker, dirtier way, I find re-compiling alsa more tempting to try first.  You know, I am kind of fond of programatically setting things :D
Thanks again and I will report the result.

---

### Post by biocyberman on 2007-11-05
Hey, for the time being I just went to Volume Control: File>Change Device>Intel ICH7 (Alsa mixer).
Then also in Volume Control Window, went to Edit>preferences>tick on "Headphone Jack Sense" and "Line Jack Sense". This showed check boxes in "Switches " tab. I had to
selected Switches and tick on those check boxes again. 
I silensed my internal speaker when I plug in headphone/line out speaker :)
I also went to System>Preferences>Sound and unchecked the "Enable system beep" so I don't get those anoying beeps even when I unpluged external speaker.

That's enough for me. Thanks you guys for your suggestions.

---

### Post by robmoore on 2007-11-20
Thanks, biocyberman. I had the same problem and your post helped resolve it.

---

### Post by raucous1 on 2007-11-24
Unfortunately I am still having trouble with this on my Dell Inspiron Laptop. The device I have listed is Intel ICH6 ALSA mixer (as well as Sigmatel STAC 9750). 

No matter what I do, the internal speaker will play any output even If I mute the external speakers. The only way to kill it is mute PCM in volume control, but then I dont get any output out of my externals either.

I dont know how to recompile ALSA, any advice? Is there not anotherway to disable the external speaker. I dont feel like opening my laptop and pulling off stuff unless its the absoulte last resort.

---

### Post by raucous1 on 2007-11-24
Alright, so I think I solved it. Using this threads advice:

[http://ubuntuforums.org/showthread.php?t=620928&goto=nextnewest](http://ubuntuforums.org/showthread.php?t=620928&goto=nextnewest)


I installed the Gnome ALSA mixer, and in it there is a slider for MAster M along with regular master. By muting Master M it killed the internal speaker, and no sound only comes out of the externals.

The only problem NOW, is that the master volume control doesn't change the volume of the headphones! If I plug the headphones in, it automatically kills the externals, but the speaker buttons on the laptop and the master slider dont change the volume level.

---

