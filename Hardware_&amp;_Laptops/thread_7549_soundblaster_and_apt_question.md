---
title: "soundblaster and apt question"
date: 2004-12-08
forum: Hardware &amp; Laptops
---

### Post by ruwach on 2004-12-08
hello there all, i just installed Ubuntu yesterday and i love it. Great distro. 
i had a couple of questions about the install and need a little help.

i just put a Soundblaster Live 5.1 (24bit) into the system here. i did a modprobe snd_emu10k and it loaded a  bunch of stuff when i looked at the lsmod,it had added more than just the snd_emu10k, stuff like soundcore, and such, so i am pretty sure it found the card. i dont know what to do next. Do i try to configure alsa, if so, how? do i need to use OSS instead? i am kinda confused because it really should be working, but i got no sound.

next question. i was in a hurry durring the install so i elected not to download packages from the net. so i am guessing a net source was not added to my apt sources list. how would i go about doing that, and what do i need to add ?

i thank you guys for a great distro, everything else seems to be just fine. 

again,thanks for your time and attention . any suggestions would be appreciated.

---

### Post by poofyhairguy on 2004-12-08
Hello! I must admit I can't help you with the sound card, as installing sound cards is hard for me too. But I can help you with this:

[QUOTE=ruwach]
next question. i was in a hurry durring the install so i elected not to download packages from the net. so i am guessing a net source was not added to my apt sources list. how would i go about doing that, and what do i need to add ?
[/QUOTE]

The net sources were added. Just use the smart-upgrade in synaptic and you will get the needed updates!

---

### Post by ruwach on 2004-12-08
ok then, thats great. um... do i still use apt-get ?
i have used debian before. 
and to get some stuff from an unofficial apt source, like the flash plugin for mozilla, do i still edit the sources.list?
Thanks for all of your help. 
btw, any one out there, still looking for help with the SB card

---

