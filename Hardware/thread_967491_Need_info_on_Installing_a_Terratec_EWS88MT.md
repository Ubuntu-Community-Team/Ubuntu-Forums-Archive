---
title: "Need info on Installing a Terratec EWS88MT"
date: 2008-11-02
forum: Hardware
---

### Post by jparc on 2008-11-02
Hi im relatively new to Ubuntustudio, i installed it once to try it out a version below Hardy Heron I guess it was 7.10, but i don't remember exactly and back then my card was recognized...I just installed version 8.10 Intrepid x86, my main use for computers is music and audio I have a Terratec EWS88MT and i can see the card on the JACK Configuration tool listed as Hw:1 but when I try to start the JACK server using ALSA (or every other type of driver I get an error and JACK server is stopped immediately. 

a) how can I know if the default Ubuntustudio installation installed drivers for my card?

b) if it didn't where I can look for Linux Drivers for my card other than the manufacturers website -i just did that and obviously they don't support Linux? (as a matter of fact they just moved my cards model to an archive of older products, my guess is that they wont be upgrading the windoze drivers either)

c) If some of you know that my card isn't going to be recognized, could you recommend a good multitrack sound card that does work like a charm with Linux.

I just need some info on where to look how to configure my card to work properly, perhaps a link or some pointer that could help, I'm not lazy reader so I thank you in advanced, I really don't want to look back to windows this time I just love the feel of this system.

EDIT: I apologize if I posted this in the wrong category, i just realized that this one is about hardware on laptops and I'm on a desktop computer.thx

JParc.

---

### Post by keys@sax on 2008-11-25
@jparc, 

There is no sound from the ews88mt in my place too.

From the liveCD and after installing 8.04 it works fine with the sound selection of "ice1712 multi" or "ALSA".

I upgraded to 8.10 and sound was lost. Did a complete fresh install, still no sound. The liveCD 8.10 is also not giving any noise

@community,
Are there solutions??

Thanks, Keys@sax

What's a music lover without music? More dead than alive

---

### Post by sr.aye on 2009-01-23
Hi try with this:

1.Go to Synaptic and unistall Pulseaudio

2.(as user)> asoundconf list
[list of your available sound cards]
EWS88MT
V8235

3.(as user)> asoundconf set-default-card EWS88MT

4.Go to Preferences>Sound  and select EWS88MT

[IMG]http://i44.tinypic.com/e7armh.jpg[/IMG]

5.reboot

6.to manage in/out , volume control and hardware configuration I use
Envy24 Control

You can install it form:

$ sudo apt-get install alsa-tools alsa-tools-gui

Hecho amigo!

I have my old EWS88MT working fine with Ubuntu 8.10. I hope that this helps you.

---

