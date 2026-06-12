---
title: "eee pc mic recognition"
date: 2009-08-15
forum: Hardware
---

### Post by maggiemonic on 2009-08-15
hello!

im sorry to sort of double post, but i think i placed a previous thread in the wrong category. does anyone know how to get the eee pc's built in microphone to function, particularly with skype. i can not get it to function whatsoever, and have tweaked all the settings in the control panel and volume control. 

thanks a lot!

---

### Post by DavidFromCanada on 2009-08-15
Please specify your Eee PC model
Here is your solution for the Eee PC 701:
```
sudo gedit /etc/modprobe.d/alsa-base
```
Add this:
```
options snd-hda-intel model=3stack-dig
```
Run this command:
```
sudo alsactl store

```

This sets the sound levels:
```
amixer set "Input Source" "Front Mic"
amixer set "Capture" 80% cap unmute
amixer set "Front Mic" 100% mute
```


In Skype's Options, go to the Sound Devices category
```
Sound in: HDA Intel (hw:Intel,0)
Sound out: pulse
Ringing: pulse
```

---

### Post by maggiemonic on 2009-08-15
oops! its the eee pc 1000. should i run the same commands tho?


actually, it worked... your brilliant! thanks so much!

---

