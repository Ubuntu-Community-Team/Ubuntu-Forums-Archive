---
title: "Acer v3-572pg, headset microphone not working"
date: 2018-12-30
forum: Hardware
---

### Post by mikasu on 2018-12-30
Hello,
I have discovered a problem with my system recently. I searched quite a lot but my system isn't used very widely in general. The mother board is a Acer v3-572pg. It's branded as a Aspire V15 Touch laptop (I believe, it could be V5). My model has a combo jack with a 3.5mm jack for both microphone and headphone. My headset's microphone is not recognized in the system. It seems like the general fix that is using the dell-headset-multi option doesn't work. I know that my Realtek codec is the ALC283. Except that... I am in the blind. If you need any other specific information, I'll do my best to provide them. Also, I use Ubuntu 18.04.1.

---

### Post by clementc on 2019-01-02
Hi [**[COLOR=#000000]mikasu[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115175"),

Can you please try overriding pin 0x19 from "not connected" to "microphone" using hdajackretask and advise if you see any improvements?

---

### Post by mikasu on 2019-01-02
I got the error: tee: /sys/class/sound/hwC1D0/reconfig: Peripheral or resource busy. Shall I do a boot override and reboot? Or is there something else?
In pavucontrol, it's still the internal mic that is detected and used.

---

### Post by clementc on 2019-01-02
Hi [**[COLOR=#000000]mikasu[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115175"),

Before you go any further with hdajackretask, can you please try the following:

1. In Terminal, run: sudo nano /etc/pulse/default.pa
2. Above the line: .ifexists module-udev-detect.so, add the line: load-module module-alsa-source device=hw:0,0
3. Save the changes, then still in Terminal, run: pulseaudio -k; pulseaudio -D
4. Run pavucontrol and check if you can see your mic input under the Input Devices tab
5. Make sure you have commented any "options snd-hda-intel model=" lines you might have added in: /etc/modprobe.d/alsa-base.conf

Please let me know if that helped at all.

---

### Post by mikasu on 2019-01-02
I found this in my file in the section of interest:
```

### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=inp$
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else

```
considering that my ALC283 is recognized as the card 1(I discovered that through my research), should I just uncomment the line above?

Proof of the card number:
> 
mikasu@Aspire-V3-572PG:~$ grep -r Realtek /proc/asound/card*
/proc/asound/card1/codec#0:Codec: Realtek ALC283
mikasu@Aspire-V3-572PG:~$ 


---

### Post by clementc on 2019-01-02
Hi  				 				 					 						 	[**[COLOR=#000000]mikasu[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115175"),

Do you mean un-commenting line: #load-module module-alsa-source device=hw:1,0 ?

If yes, please go ahead and carry on from step 3 of my previous post then report back here if it has worked.

---

### Post by mikasu on 2019-01-02
I rebooted to make sure the changes in the alsa-base.conf were applied. We have a progress, in pavucontrol, the microphone input from the ALC283 card is now recognized. Only thing is that it behaves like there is no mic plugged in. So no sound level bars like the integrated mic which now has it's own device. And it was a yes about the line.

---

### Post by clementc on 2019-01-02
Hi [**[COLOR=#000000]mikasu[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115175"),

Can you please provide me with the output of the following command: aplay -l

---

### Post by mikasu on 2019-01-02
here it is:
```

mikasu@Aspire-V3-572PG:~$ aplay -l
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: HDMI [HDA Intel HDMI], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: HDMI [HDA Intel HDMI], périphérique 7: HDMI 1 [HDMI 1]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: HDMI [HDA Intel HDMI], périphérique 8: HDMI 2 [HDMI 2]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: HDMI [HDA Intel HDMI], périphérique 9: HDMI 3 [HDMI 3]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: HDMI [HDA Intel HDMI], périphérique 10: HDMI 4 [HDMI 4]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: PCH [HDA Intel PCH], périphérique 0: ALC283 Analog [ALC283 Analog]
  Sous-périphériques: 0/1
  Sous-périphérique #0: subdevice #0
mikasu@Aspire-V3-572PG:~$ 

```

I'm sorry if you struggle to understand, my operating system is setup in french because I am a native french speaker and I prefer using my system in french. So far, I translated the error codes the best I could.

---

### Post by clementc on 2019-01-02
Hi [**[COLOR=#000000]mikasu[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115175"),

Don't worry about the French language in your output, I am French myself so that's not really a problem (or at least to me) ;-)

Just for the sake of completion, can you please try adding the line: load-module module-alsa-source device=hw:0,0 (and commenting the one which ends in 1,0) as previously stated in my post #4 then follow it from step 3 onward?

I just want to make sure we cover our basis here.

---

### Post by mikasu on 2019-01-02
So this is the new section of the file:
```

### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
load-module module-alsa-source device=hw:0,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=inp$
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else

```

and... that happened the first time, sorry for not pointing out, but I have this error:
```

mikasu@Aspire-V3-572PG:~$ pulseaudio -D
E: [pulseaudio] main.c: Échec lors du démarrage du démon.

```

Edit: and no sound, which I think didn't happen in the first test... pavucontrol says the pulseaudio server is crashed (probably)

---

### Post by clementc on 2019-01-02
Hi  				 				 					 						 	[**[COLOR=#000000]mikasu[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115175"),

Can you please comment again the line: load-module module-alsa-source device=hw:0,0 (and keep the one ending with hw:1,0 commented as well) and modify /etc/modprobe.d/alsa-base.conf by adding the following line: options snd-hda-intel model=alc283-sense-combo

Finally, if this also fails, I can only think of a kernel update to a newer version (there is a tool called Ukuu that is really good for this) hoping that this would resolve your issue.

Hopefully someone else on this forum will also be able to help you out with this issue.

Nonetheless, thank you for trying all the commands I provided you. I hope that you do get your issue resolved soon.

---

### Post by mikasu on 2019-01-02
Sadly, still on integrated microphone. The device split is now gone. I still don't have the prompt that some forums talked about that was supposedly present in "Precise" which would ask if what I connected are Headphones, Headsets or Microphone. About upgrading the kernel, I don't know to which kernel version I should go with. This has been my only "major" issue with Ubuntu. If there are no software solutions, I might go for a usb sound card which apparently work on Linux if they don't require a driver. That would get my microphone recognized and actually be used. Though, if anyone would have a fix for this issue, well, I will be very happy to test it. Specially since the sound card will cost 16$CAD on amazon...

---

### Post by clementc on 2019-01-02
Hi [**[COLOR=#000000]mikasu[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115175"),

You could try installing the latest Linux kernel (4.20 at the time of this writing) by following the steps mentioned on [this page]("http://ubuntuhandbook.org/index.php/2017/02/ukuu-install-latest-kernels-ubuntu-linux-mint/").

Worst case scenario, a backup entry would have been created automatically in GRUB at the time of the update, so if anything goes wrong, you should just be able to boot right back into your current version.

---

### Post by mikasu on 2019-01-02
Hi

The Kernel 4.20 didn't work. Except breaking my gpu driver, it did nothing to my sound issue. I'm going back to the 4.15 for now.

---

### Post by clementc on 2019-01-02
Hi [**[COLOR=#000000]mikasu[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115175"),

Sorry about that, at least you tried.

Hopefully someone here will be able to help you out more than I did.

Good luck.

---

### Post by mikasu on 2019-01-02
Thank you. No need to be sorry. You got me a possible path of progress, at least we got the devices split in two separate ones! Perhaps something can be done on this path if someone knows something to do with that. Right now I only have the "options snd-hda-intel model=alc283-combo-sense" set, nothing else.

---

