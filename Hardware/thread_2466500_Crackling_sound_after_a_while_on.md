---
title: "Crackling sound after a while on"
date: 2021-08-29
forum: Hardware
---

### Post by joerack2 on 2021-08-29
As topic, I'm getting a crackling sound from my recon sounblaster  

I've tried: 


[LIST=1]
[*]Nothing (didn't work)
[/LIST]
Replacing  /usr/share/pulseaudio/alsa-mixer/paths/analog-output-speaker.conf  lines   

2.
[Element Headphone]
switch = off
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

and 

[Element Speaker]
required-any = any
switch = mute
volume = off

Worked for a few minutes

3. output of inxi -Fxz

  Device-1: Creative Labs Sound Core3D [Sound Blaster Recon3D / Z-Series] 
  driver: snd_hda_intel v: kernel bus ID: 06:00.0 
  Device-2: NVIDIA GP104 High Definition Audio driver: snd_hda_intel 
  v: kernel bus ID: 07:00.1 
  Device-3: AMD Family 17h HD Audio vendor: ASUSTeK driver: snd_hda_intel 
  v: kernel bus ID: 09:00.3 
  Device-4: C-Media TONOR TC30 Audio Device type: USB 
  driver: hid-generic,snd-usb-audio,usbhid bus ID: 3-1:2 
  Device-5: Logitech Webcam C270 type: USB driver: snd-usb-audio,uvcvideo 
  bus ID: 1-6:4 
  Sound Server: ALSA v: k5.11.0-31-generic 
Network:


4. switching to hdmi/internal sound card no problems at all



I think my card is bad.... any other solution before chucking it?

---

