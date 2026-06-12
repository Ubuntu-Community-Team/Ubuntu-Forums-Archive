---
title: "alsa/oss/esd with multiple soundcards / audio devices"
date: 2005-05-15
forum: Hardware &amp; Laptops
---

### Post by 23meg on 2005-05-15
i'm using a laptop with two audio devices: one internal soundmax sound chip, and an external usb audio device (m-audio quattro). most of the time, the quattro is on, so i have beep media player's output plugin configured to alsa, pointing to the device identifier of the quattro. but when it's turned off, beep will still look for it, and when it can't find it, displays an error message. choosing "default pcm device" or using esd won't help either. 

i'd like all apps to try to use the quattro by default, and when it's not available, not fail but resort to the internal sound device, like the way things were set up in windows when i'd choose the quattro as the preferred audio device. how can this be accomplished?

---

### Post by ludi on 2005-05-15
[QUOTE=23meg]i'm using a laptop with two audio devices: one internal soundmax sound chip, and an external usb audio device (m-audio quattro). most of the time, the quattro is on, so i have beep media player's output plugin configured to alsa, pointing to the device identifier of the quattro. but when it's turned off, beep will still look for it, and when it can't find it, displays an error message. choosing "default pcm device" or using esd won't help either. 

i'd like all apps to try to use the quattro by default, and when it's not available, not fail but resort to the internal sound device, like the way things were set up in windows when i'd choose the quattro as the preferred audio device. how can this be accomplished?[/QUOTE]
 [http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?company=Generic&card=Generic&chip=Generic&module=Generic](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?company=Generic&card=Generic&chip=Generic&module=Generic)
> 
 Make a file called .asoundrc in your home and/or root directory. 
        vi /home/xxx/.asoundrc

copy and paste the following into the file then save it. 
        pcm.!default {
        type hw
        card 0
        }

        ctl.!default {
        type hw           
        card 0
        }


This will direct all sound to a specif card.
Read the full link.

---

### Post by 23meg on 2005-05-15
i've gone through this doc before, and i skimmed through it once more now, but if i'm not missing something very critical, unfortunately the info in here won't be useful for my purporse since i can't state "if/then" conditions in the .asoundrc file. the only use of this would be to centralize the device choice of all apps via the .asoundrc file, but the choice is still a static one. think of this like having two copies of a document, one on an external drive and one on an internal one, and you want the computer to look for the document in the external one if possible (if it's connected), and if not, in the internal one as a secondary choice.

---

### Post by ludi on 2005-05-15
[QUOTE=23meg]i've gone through this doc before, and i skimmed through it once more now, but if i'm not missing something very critical, unfortunately the info in here won't be useful for my purporse since i can't state "if/then" conditions in the .asoundrc file. the only use of this would be to centralize the device choice of all apps via the .asoundrc file, but the choice is still a static one. think of this like having two copies of a document, one on an external drive and one on an internal one, and you want the computer to look for the document in the external one if possible (if it's connected), and if not, in the internal one as a secondary choice.[/QUOTE]
 Get it.
I don't know, may be a script on boot process?
If /dev/dspX exist, go and direct all sound to hwX if not, direct to hwZ or if /dev/dspX exist then run asound1.rc if not, run asound2.rc.
Something like that...

---

### Post by 23meg on 2005-05-15
right, that's where it's at. is it possible to have more than one .asoundrc file and choose between them? thinking out loud: if not (and probably that's the case), maybe i need a script that creates the .asoundrc file at each boot. and for that i'd need a (preferably) bash command that will detect the on/off status of a specific device.

i'd love it if some experienced scripters would lend me a hand with this.

---

### Post by 23meg on 2005-05-15
..but a startup script alone would only check at startup and "forget" about whether the external device is working or not later on. so maybe a daemon kind of solution is needed. getting more complicated as i think of it.

---

### Post by ludi on 2005-05-16
[QUOTE=23meg]..but a startup script alone would only check at startup and "forget" about whether the external device is working or not later on. so maybe a daemon kind of solution is needed. getting more complicated as i think of it.[/QUOTE]
 Yeah, a simple script to check at startup is a good solution but is static too...
A daemon is better and harder...Well, ask for some tips on dev's irc, may be they help you.
Have fun :)

---

