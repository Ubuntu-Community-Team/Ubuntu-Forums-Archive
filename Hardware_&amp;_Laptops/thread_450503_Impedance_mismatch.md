---
title: "Impedance mismatch"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by theonlykman on 2007-05-21
So Im not at all an audiophile nor am I an expert in the field of circuitry. But heres the deal: 
When I use my headphones (koss earbuds, impedance rated at 32 ohms) in ubuntu the audio is terrible but its fine/normal in windows. I previously posted this problem under multimedia and video. Not the best place for a hardware issue I realize now :p. Instead of going into the details here, Ill just refer you to that thread:

[http://ubuntuforums.org/showthread.php?t=428940](http://ubuntuforums.org/showthread.php?t=428940)

So, is there any way to change the impedance output (if thats the correct term) of my soundcard  (Intel HDA ICH7)? I could get a different pair of headphones with a higher impedance, but apparently earbuds dont have a higher impedance than 50 ohms. For reasons of portability and subtlety Id like to stick with earbuds. Im really frustrated that they work in windows fine but not in ubuntu.

Also, is my diagnosis correct?

Thanks

---

### Post by Ken_Lewis81 on 2007-05-21
If it helps, try turning down the volume on your soundcard.  I've had crackly sound from my soundcard under Ubuntu, which sounded fine in the other OS, and the trick was to set the volume to 80% at most.  The sound was as loud as I've experienced elsewhere, but I expect it crackled because too much signal was let onto the sound chips by a badly-calibrated ALSA. 

Take care.
Ken.

---

### Post by theonlykman on 2007-05-23
No sorry, doesnt work...or at least not the way I want it to. Ive tried messing around with every channel and the best quality is at a volume where its pretty much pointless to use headphones. Its irritating. Also, this occurs only through my headphones...I can crank up the volume all the way, and hook up the headphone jack to a pair of desktop speakers and its pretty nice. Basically, (I think) the impedance output is such that its better for desktop speakers and not for headphones. But, like I said this isnt the case in windows meaning that its probably variable. If thats the case Im hoping the way I can change it back to the way its set in Windows.

---

