---
title: "Can't enable audio recording"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by lamadredelsapo on 2007-12-15
When I click on Volume Control applet to select the microphone as audio recording device to use it with Skype there are no recording options available. My motherboard is an ASUS M2N which has nForce 430 chipset, and thus ADI 6-channel high definition audio codec. Playback works like a charm though.

---

### Post by lamadredelsapo on 2007-12-15
I solved it by following [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by staticvoid on 2007-12-15
thanks for posting the link

---

### Post by crazyfish666 on 2007-12-15
> **lamadredelsapo said:**
> I solved it by following [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

This seems to all be going well for me until I get to the "Manually Specify Module Parameters" section and input
> cat /proc/asound/card0/codec#* | grep Codec
it then gives me
> cat: /proc/asound/card0/codec#*: No such file or directory

I am on a Dell Inspiron 6400 with integrated audio (is this the problem?) I am new to Ubuntu and rather confused. The original problem was that it was not recognizing my microphone. I tried skipping to the next step, figuring I would figure out my sound card model later on, and inputted 
> /usr/src/KERNEL_VERSION/Documentation/sound/alsa/ALSA-Configuration.txt
but it came back with
> bash: /usr/src/2.6.22/Documentation/sound/alsa/ALSA-Configuration.txt: No such file or directory

I am sure I am just being blind and there is some easy way to fix this, but I simply don't know enough about Ubuntu to see it.

---

### Post by lamadredelsapo on 2007-12-16
You can find ALSA-Configuration.txt in the directory where you extracted de ALSA driver.

Have you checked if any errors or warnings appear during make or make install?

This might sound stupid but, have you rebooted after installing the driver, alsa utils and alsa-lib?

---

