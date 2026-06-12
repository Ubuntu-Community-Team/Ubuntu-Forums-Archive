---
title: "No sounds after bluetooth disconnect"
date: 2016-03-15
forum: Hardware
---

### Post by neil.the.blue on 2016-03-15
Hello,

I am running ubuntu 15.10. witih a bluetooth USB dongle. 

When I connect my bluetooth headphones I can switch the audio output to bluetooth fine. However when I disconnect the bluetooth there is now only the sound card listed in the output devices but there is not sound in the speakers, even when I select the sound card output in the sound settings. To get sound back again I kill off the pulseaudio server and restart my app (normally youtube) to get sound. 

Is there a better way to get audio back to the soundcard and am I doing something bad?

Thanks
Neil

---

### Post by neil.the.blue on 2016-03-16
Looking into this a bit more it seems the s/pdif settings are getting lost or messed up.

---

### Post by tea for one on 2016-03-16
> **neil.the.blue said:**
> Hello,

I am running ubuntu 15.10. witih a bluetooth USB dongle. 

When I connect my bluetooth headphones I can switch the audio output to bluetooth fine. However when I disconnect the bluetooth there is now only the sound card listed in the output devices but there is not sound in the speakers, even when I select the sound card output in the sound settings. To get sound back again I kill off the pulseaudio server and restart my app (normally youtube) to get sound. 

Is there a better way to get audio back to the soundcard and am I doing something bad?

Thanks
Neil

Good evening

When you mention "disconnect the bluetooth", is this via software or physically switching off the bluetooth speaker?

I am sure that you should be able to switch the sound output by just toggling the direction i.e. to choose which speaker receives the sound.

I have attached two screenshots which I hope will help to explain what I mean.

[ATTACH=CONFIG]267841[/ATTACH][ATTACH=CONFIG]267842[/ATTACH]

Please notice the different "profile" in the lower half of each screenshot.

It may be better to leave all speakers connected and simply toggle between the two, Then you can practise and start to feel more comfortable with the relationship between the blutooth/sound configuration and the hardware devices themselves.

I must admit that there are many settings to play with and it is quite easy to end up with sound difficulties.

Best wishes

---

