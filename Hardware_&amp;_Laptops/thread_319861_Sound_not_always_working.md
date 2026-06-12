---
title: "Sound not always working"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by Kreuger on 2006-12-16
Once in a while after I reboot my computer, the sound doesn't work. I usually have to reboot another dozen times or so for it to come back. I tried looking to see if there was an alsa daemon that needed to be run or something but I cant figure it out. Can anyone help? Hope I picked the right forum, maybe I should've posted in multimedia?

---

### Post by dbbolton on 2006-12-17
some of my sound problems were fixed by doing

sudo killall esd

---

### Post by Amarack on 2006-12-21
I want to say that I am having the exact same problem as the original poster. The sound works sometimes and is great, but then I will start up the computer other times and it will not work at all. Everything appears to be the same, with one exception. When sound doesn't work and I look at the volume properties, for some reason pcm has been set to mute. When I unmute it nothing is fixed, but it is still strange that it gets muted at start up in these situations (for me at least). 

Does anyone know what could be causing this?

---

### Post by Amarack on 2006-12-21
Okay... well I found the problem. Maybe it is the same as for the first person. It turns out that ubuntu likes variety, and will sometimes choose the built in audio chip (on the motherboard) as the default, and other times chooses the SB Audigy I actually use as the default. When went to:

System->Preferences->Sound

Then the Sounds tab, and changed the default sound card at the bottom to the one I actually use everything worked. It is strange that this gets changed without me doing anything though.

---

