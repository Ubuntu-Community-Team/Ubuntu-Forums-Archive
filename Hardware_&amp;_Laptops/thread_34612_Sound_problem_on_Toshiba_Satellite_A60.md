---
title: "Sound problem on Toshiba Satellite A60"
date: 2005-05-15
forum: Hardware &amp; Laptops
---

### Post by der_kaiser on 2005-05-15
Hello,
I've installed Kubuntu last week on my Toshiba Satellite A60 and almost everything is working flawlessly..except the sound card (a Realtek SL250).
After booting, I get a message telling :
--------------------------------------------------------------
 Sound server information message
Error while initializing the sound driver
device : default can't be opened for playback (No such file or directory)
The sound server will continue, using the null outpout device.
-------------------------------------------------------------

I've installed all Alsa stuffs, but I have still the same message, and the sound isn't working..

Any body can help me?

---

### Post by der_kaiser on 2005-05-17
Really no idea??

---

### Post by der_kaiser on 2005-05-31
I also have a Toshiba A60, and I had the same problem with the sound.
You have to follow the instructions on this page : [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

And after add these lines to:

/etc/hotplug/blacklist : snd-atiixp-modem
snd-atiixp

/etc/modules : snd-atiixp

You also have to type "chmod 777 /dev/dsp"

Good luck!

---

### Post by c_dawg on 2005-09-05
Hi, I also have a toshiba A60, I cant get sound working either. I am a total linux newb, I followed several "get alsa working" threads to no avail. When i follow the thread referenced earlier it does nothing. when i notice that the first step is "killall esd" I noticed that it didnt kill any process. and when i try to run esd out of curiosity i get the error "ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave" Whatever that means. Please any help would be greatly appreciated as I have been trying for weeks

---

