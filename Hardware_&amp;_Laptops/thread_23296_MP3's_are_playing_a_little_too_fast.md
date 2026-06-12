---
title: "MP3's are playing a little too fast"
date: 2005-04-01
forum: Hardware &amp; Laptops
---

### Post by Dracontopes on 2005-04-01
Only a **little**, it's not distorted or something like that, but just, too fast. I'm listening to internet radio very frequently and because the sound is going too fast it's hitching like madness, because you can't play music that has not been broadcasted yet... Doh! 

I'm using the ALSA drivers for everything (in gnome and beep etc) and the symptoms started today. It also happens in Rhythembox.

---

### Post by phend-one on 2005-04-01
Hi,

It took me a while to figure it out, hopefully it applies to your situation.

"Applications" > "Sound & Video" > "Volume Control"

You might need to do this step:
In "Volume Control", "Edit" > "Preferences"
Find: "Multi Track Internal Clock", put a tick next to it. Close Dialog

Now in the "Options" tab, select 44100. 
Close and restart the application you're using to play the sound.

It should play at "normal" speeds. 
One problem I haven't been able to solve is: this setting won't "stick" after a reboot. Anyone know how?

Hope this helps!

---

### Post by Dracontopes on 2005-04-01
Thanks for your reply :)

Unfortunately, the option Multi Track Internal Clock is not listed in Edit > Preferences... I guess it's not available for my soundcard? (nforce 2 soundstorm, snd-intel8x0)

But luckily, I rebooted and mp3's are playing normal now... :-? Weird!

---

