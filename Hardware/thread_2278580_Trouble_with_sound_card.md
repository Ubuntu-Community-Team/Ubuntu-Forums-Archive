---
title: "Trouble with sound card"
date: 2015-05-17
forum: Hardware
---

### Post by usuarionte on 2015-05-17
Hi, I have recently bought a new laptop ( Acer aspire E5-571G) and I am having some trouble with the sound card, after been researching for a few days I havent been able to find a solution.
The speakers work fine, but the microphone doesnt work at all, it seems like I have the Realtek [COLOR=#333333][FONT=Ubuntu]ALC283, but I cant find any drivers that solve my problem, maybe is just a problem of configuration?
I also tried modifying the volume (everything is at max) with alsamixer but didnt get anything, it seems like I have more than one sound card (??) because there i have default, hdmi and hda.
I dont know what else to try, can someone tell me what to do?
Thank you
EDIT: I tried with some more tutorials, and now finally in pulseaudio I can see the bars on the microphone moving up and down when I speak ( So the driver is properly working and my micro is working) however, when I try to use any app to record, or to use the device to capture to a file, it doesnt work.
If I run it from terminal I get the next error: Error opening PCM device plughw:0 (No existe el archivo o el directorio)
Could not open PCM for capture.
ALSA capture failed!

I read somewhere that my alsa thinks I have two sound cards, how can I tell the recording app to use a different place to look for the micro?
Thank you
[/FONT][/COLOR]

---

### Post by usuarionte on 2015-05-18
Hey, I have been trying, and it has to be a problem of configuration definitely, because I am able to record using the terminal, with the command arecord, but I am unable to do it from any other aplication, I tested it and they keep sending me the same error, how can I change the apps to use the same mic device used by alsa?
I also tried removing pulseadio with no results (because alsa apparently knows wich one is the right one but the others are taking the configuration from a different source??)
Thanks

---

