---
title: "ALSA driver problem in ubuntu"
date: 2011-03-10
forum: Hardware
---

### Post by bogdan. on 2011-03-10
Hello dear community as this is my first post here :)

I'm new to linux in general, although i have some strong knowledge of windows (x86,x64 and all win mobile versions). 
So i got myself one phone, a HTC HD2 and heard it was possible to install ubuntu on it. I currently run ubuntu on one of my tablet pc's and i'm very happy with it. So why not installing it on that phone as a second os. Even better HTC HD2 does support usb host functionality therefore i could really turn it into a small desktop. One problem though... the original build i got from xda developers forum, didn't include audio functions because at the time there was no alsa driver for the internal sound system (phone audio chipset). However i want to use small usb sound cards or usb headphones as it could solve this problem easily. But as i tried with some logitech usb headphones, i still get no sound, although the small remote appears to function (pressing volume buttons will change the volume slider on desktop and the headphones are detected and shown in proprietary drivers). 
I guess (from what i know/heard) that i should update/reinstall the alsa drivers, but as i tried i still got no succes in making those headphones to work. Other then that, my current experience with ubuntu prevents me from trying something else. 
Does anyone know what should be done to correct this problem? 
I also guess that as the kernel is compiled to run on ARM as opposed to standard x86/x64 builds, that could also present some problems. 

Thank you.

---

### Post by Afishionado on 2011-03-10
Sometimes I've had situations where something was randomly muted that was not visible via the gui.

I don't know how easy it will be on a device without a keyboard, but you could try launching alsamixer from the command line and see if there's anything muted in there.

Also, do these headphones work correctly with Linux on any other machine?

---

### Post by bogdan. on 2011-03-10
i made myself a powered hub so i can attach both keyboard and mouse. navigation is easy. noup, it doesn't appear to be a mute problem. in "sound" menu i can't see the headset listed or any audio device. 
this build didn't had any mixer device installed, i downloaded and installed one via synaptic. Also i'm downloading everything alsa related and i'll check to see where it's going...

---

### Post by bogdan. on 2011-03-11
tried with another usb sound card. this one:
[http://karuppuswamy.com/wordpress/2010/10/04/how-to-get-usb-sound-adapter-0d8c000c-working-as-primary-sound-card-in-debian-linux/](http://karuppuswamy.com/wordpress/2010/10/04/how-to-get-usb-sound-adapter-0d8c000c-working-as-primary-sound-card-in-debian-linux/)

also, tried editing alsaconf like in that quide. Still doesn't work. No audio device shown. No speaker icon in tab, no nothing. I don't know what are the dependencies needed by alsa sound system to get full audio support, as like i said, i'm running a trim down version of ubuntu on top of a kernel compiled for arm cpu's.

---

