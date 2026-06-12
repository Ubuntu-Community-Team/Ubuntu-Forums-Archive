---
title: "microphone not working"
date: 2005-05-31
forum: Hardware &amp; Laptops
---

### Post by leo.nava on 2005-05-31
[COLOR=DarkGreen]i dont know if it my sound card...
i have an Intel D865GBF desktop board with its integrated sound card
----
Audio  	SoundMAX 4 XL with AudioESP audio subsystem using the Analog Devices AD1985 codec
----

the system sounds are ok, i can listen music and hear everything but my microphone
is not working. i already tried moving the volume properties etc. but i get no results.

i've been reading on the net about it and they say something about turning the
Mic Boost on... how can i do that?, but i dont know if that will work aswell.

help please!
[/COLOR]

---

### Post by Zingam on 2005-05-31
Have you tried to turn on the mic from the mixer?

I have a similar problem. Actually I can hear that the sound recorder records my voice but it plays so low I can barely hear it.

---

### Post by nocturn on 2005-05-31
Same here!

I figured the mic I bought was broken...

---

### Post by leo.nava on 2005-05-31
i solved it...

in the OSS mixer...go to "file"--"change device" and go to the ALSA mixer
and in there go to the "switches" menu and enable the option:
"Center/LFE jack as mic"
then..my mic started to sound but very sensitive, like with lots of static
to eliminate this i went to the "capture" menu and diabled the small
microphone icon in "line in"
then i went to change device again to ALSA mixer and in there
i went to "capture" menu and in "volume" i diabled the small microphone
icon that says "toggle capture from volume"...and thats it...
my mic now works prefectly :)

if this doesnt work for you..just mess a lot with it...changing from ALSA to OSS mixer...and at the same time try your configuration by trying to record something with the sound recorder at every time you do some changes in the mixers.

it worked for me :P

---

