---
title: "Ubuntu 16.04 LTS - sound stopped working, no cards detected"
date: 2018-06-14
forum: Hardware
---

### Post by artemisworks on 2018-06-14
Hi everyone,
I've been using Ubuntu 16.04 LTS on my laptop for over a year now. Everything was working as normal until yesterday when I noticed that sound wasn't working at all. When I checked Settings->Sound, it suggested under outputs: several HDMI outputs but no internal soundcard. Until now I've been using the internal speakers for sound. I just installed some standard system updates when prompted, a day or two ago so I am unsure if that broke the sound?? After rebooting my system, I can only see Dummy Output when I check the Sound setting. 

I managed to stop pulseaudio from autospawning, deleted everything in ~.config/pulse and restarted, and at some point I had a loud hissing noise from my speakers and nothing else. I also added a line to /etc/modprobe.d/alsa-base.conf: options snd-hda-intel model=auto (I tried 'generic' too, to no avail).

I tried several solutions suggested in blogposts and forum posts. Finally uninstalled and reinstalled Alsa, uninstalled and reinstalled Pulseaudio and I still have the same problem.

pacmd -list-cards
0 card(s) available

lspci -v | grep Audio
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)

alsamixer
cannot open mixer: No such file or directory

It seems even worse after uninstalling and reinstalling Pulseaudio as the volume control icon has now disappeared from my Ubuntu window menu on the upper right corner.

Does anyone have any ideas about what has happened and how I can fix it?
Many thanks. 

Artie

---

### Post by Autodave on 2018-06-14
This may or may not help, but it is the very first thing that I do when I get a weird thing happening on a laptop:

1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

### Post by artemisworks on 2018-06-14
Thanks for your response, but I don't have any peripherals connected to the laptop.

I was considering getting a Linux-only desktop but considering these troubles I'm having with my laptop, I'm seriously reconsidering that idea.

I tried a few more things, but for some reason it isn't detecting my sound card. 

aplay -l
aplay: device_list:268: no soundcards found...

---

### Post by Yellow Pasque on 2018-06-14
Have you tried a LiveUSB? (preferably Ubuntu 18.04)
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

If you have the option to disable the audio codec in the BIOS/EFI, do that, reboot into the OS, then shut down, boot back into the BIOS and enable the audio codec again. I've seen that work, often on dual-boot (Linux/Win) systems.

---

### Post by artemisworks on 2018-06-16
Hi there, yes I've tried that Alsainfo script - should I post the output file here?

Unfortunately my BIOS does not allow me to disable the codec :( 

Bizarrely enough when I booted my laptop today it recognises *4* sound outputs, but of course none of them work! One of them appears to be headphones, but when I plug my headphones in I don't get any sound.

lspci shows - among others:
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)

aplay -l shows:
***List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH] , device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH] , device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH] , device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1

I haven't a clue what this all means. I do not have ANY peripherals plugged into my laptop whatsoever.... I tried my headphones and they didn't work.

alsamixer now works (!) but tweaking it does not seem to make any difference whatsoever.

I've run out of ideas. :(

---

