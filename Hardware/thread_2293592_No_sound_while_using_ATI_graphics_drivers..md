---
title: "No sound while using ATI graphics drivers."
date: 2015-09-06
forum: Hardware
---

### Post by jaciminelli-0 on 2015-09-06
Hello, I have recently switched back to Ubuntu as my primary OS and have an issue related to sound I am having trouble solving. All of my hardware was recognized and worked fine in the live environment, shortly after installing and starting update/install software I noticed I had no sound. I have three audio devices on this system, an on board sound card which I have disabled, a PCI soundcard and a graphics card with HDMI audio. Since it worked in the live environment I assumed that it was possible and I just needed to tweak some settings. My troubleshooting so far has shown that the only times I can get it to work it is when I am not using the fglrx drivers. This makes sense as to why it was working in the live environment. There appears to be a conflict between the HDMI audio on this graphics card and my creative card. I would happily blacklist the HDMI audio completely as long as I can still use the card for video/games however they both use the snd-hda-intel module and almost everything I have been able to find assumes that the conflicting devices are using different modules. I have a hunch that it will work if the soundblaster is loaded first but since they are using the same module I'm not sure if that will work either.

Info - 
Ubuntu 14.04
Sound Card: Creative SOUND BLASTER AUDIGY SE
Graphics Card: Asus AMD Radeon HD 7770

aplay -l output
```
**** List of PLAYBACK Hardware Devices ****card 0: HDMI [HDA ATI HDMI], device 3: ID aa01 Digital [ID aa01 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Creative [HDA Creative], device 0: ALC898 Analog [ALC898 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Please let me know if there is anything else that would be helpful to see, thanks! :)

---

### Post by ipillinger on 2015-09-06
I had some luck installing PulseAudio Volume Control from Synaptic Package manager. When I had some audio playing I could see it in the levels bar in the Output tab. I can't remember exactly what I did but I played around with the options in the Output and Configuration tabs.

This was for an integrated soundcard on an AMD system so your mileage may vary.

---

### Post by jaciminelli-0 on 2015-09-07
Thanks for the suggestion, PulseAudio Volume Control was able to let me disable the HDMI audio and it stopped showing up in the System Settings however the driver is still being loaded even after restart. :( I'll keep working on it, worst case I can try another sound card or with enough research I might have to modify the module in some way though that sounds like a rabbit hole I don't want to go down.

---

### Post by Yellow Pasque on 2015-09-07
Try this:
```
echo "options snd-hda-intel enable=0,1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

Based off: [https://lists.fedoraproject.org/pipermail/users/2013-July/439139.html](https://lists.fedoraproject.org/pipermail/users/2013-July/439139.html)

---

### Post by jaciminelli-0 on 2015-09-10
Thanks, I added that line to my Alsa conf and it worked like a charm I don't see the HDMI audio at all. I switched graphics cards in order to get better compatibility with Wine and this method worked with that also. I do have sound now however its just static. When the system starts up for example it plays static for like 10 seconds. I play a video there is static for as long as the video is on so it's as if a signal is being sent but for whatever reason it is encoded wrong and comes out as static. I tried a friends Creative Card and it also tried to use snd-hda-intel prior to the disabling of the HDMI interface so I assumed it would not work either however strangely when I swapped my original card back in there it worked for a couple reboots and then died. I know there is a configuration that works I just wish I had been able to save it when it was briefly working. Thanks everyone for the help so far.

---

