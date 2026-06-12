---
title: "audio output via HDMI"
date: 2020-03-24
forum: Hardware
---

### Post by engine on 2020-03-24
I've inherited a Lenovo laptop and installed Linux, so now I'm able to watch YouTube on a TV through the HDMI connection: but I can't get any audio. Do I need to enable this somewhere ? thanks in advance!

---

### Post by webaake on 2020-03-24
You should be able to click on the sound icon in your panel (or the equivalent of a panel - you don't indicate which, of the many flavors of linux you use) In that panel click on "Mixer". There you can configure outputs. You can also start the mixer from a terminal with the command "pavucontrol". Start the Mixer with a Youtube clip running and it will be easier to see what's going on.

---

### Post by SeijiSensei on 2020-03-24
Probably the audio system is defaulting to the analog jack.  You should be able to switch to HDMI audio using the methods Webaake describes.

---

### Post by luks911 on 2020-03-24
I sometimes have to restart pulseaudio in order to can use de HDMI audio. In a terminal execute ```
pulseaudio -k
``` and then check if you have the HDMI sound output as an option.

---

