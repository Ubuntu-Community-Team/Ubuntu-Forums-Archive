---
title: "All audio plays through my microphone when I don't want it to"
date: 2021-01-27
forum: Hardware
---

### Post by adalogic on 2021-01-27
Hello everybody. Apologies if I'm doing something wrong in here, I am brand-new to this forum.

I'm not sure whether to post this in hardware or multimedia-software, but I think it fits better here.

I've downloaded Discord on my Ubuntu OS and am trying to play some youtube videos through Firefox while in a call with friends. Problem is, I don't want them hearing what I'm watching. And my mic is doing the exact opposite of that. It seems that my microphone picks up absolutely everything, from my speaker audio to even me clicking on my touchpad (which is super quiet). I don't know how to fix this. Is anyone able to help?

---

### Post by TheFu on 2021-01-28
Mute your mic?

---

### Post by adalogic on 2021-01-28
Kind of hard to do when you're also trying to talk to your friends while listening to your music. Additionally I lack headphones :/

---

### Post by TheFu on 2021-01-28
> **adalogic said:**
> Kind of hard to do when you're also trying to talk to your friends while listening to your music. Additionally I lack headphones :/

So ... you want a microphone that doesn't actually listen to A, but hears B perfectly.  Mmmmm-k. Most people want all the sounds in the room captured and if they don't, then they create a space with sound deadening materials. 

Use a cell phone that has background noise canceling?
Buy some earbuds for the music?

Google found this: [https://askubuntu.com/questions/18958/realtime-noise-removal-with-pulseaudio](https://askubuntu.com/questions/18958/realtime-noise-removal-with-pulseaudio)
using the "**noise canceling**" keywords.
Some other things to search: 
[LIST]
[*]"acoustic echo cancellation"
[*]"noise suppression"
[/LIST]

There are mixed claims - some like mine - which aren't useful and some claiming amazing results.  The PulseAudio documentation: 
[https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/#module-echo-cancel](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/#module-echo-cancel)  I have doubts that music will be removed, but bet fan noise can be.

---

### Post by adalogic on 2021-01-28
I'll check it out after work. Thank you.

---

### Post by adalogic on 2021-01-28
Thank you so much for linking the Ask Ubuntu thread for pulseaudio noise cancellation. It doesn't completely remove the audio problem, but it reduces it to the point where I can up the input sensitivity until it rarely plays through my microphone during calls. Again, thank you.

---

