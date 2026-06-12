---
title: "Audify fx card - getting just noise"
date: 2014-03-03
forum: Hardware
---

### Post by PeterTaps on 2014-03-03
Folks,

Environment: Ubuntu 13.10 core + openbox + alsa (No pulse-audio at all)

I just installed a Creative Labs' Audigy FX card in my computer.

When I connect the 3 line-out pins from my motherboard to speakers, the following command works just fine:

$ speaker-test -c6 -twav -Dsurround51:CARD=PCH,DEV=0
I can hear the sound from each individual speaker.

However, when I connect the line-out pins from my Audigy card to speaker, it doesn't really work:

$ speaker-test -c6 -twav -Dsurround51:CARD=Creative,DEV=0

speaker-test 1.0.27.1


Playback device is hw:CARD=Creative,DEV=0
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 5440
Period size range from 32 to 2720
Using max buffer size 5440
Periods = 4
was set period_size = 1088
was set buffer_size = 5440
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 8.523790


All I hear is some noise from the speakers.

Here are some other relevant outputs:

$ aplay -l 

...
card 2: Creative [HDA Creative], device 0: ALC898 Analog [ALC898 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ aplay -L

...
surround51:CARD=Creative,DEV=0
    HDA Creative, ALC898 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers


Note that the card is enabled via gnome-alsamixer. Otherwise, I wouldn't even hear the noise.

I am wondering if anyone knows what could be going on.

Looking at some other posts, it appears others see "Audigy" in the output from aplay instead of the generic "Creative ALC898" output that I am seeing. Wondering if it is perhaps a missing driver issue.

Thank you in advance for your help.

Regards,
Peter

---

### Post by jank2 on 2014-08-25
Hej guys,

I know this thread is old but I recently ran into this problem and since I didn't find any solution online I am gonna say how I fixed it ;)

The problem is quite simple, you use the same driver for two different cards. In my case it was the nvidia HDMI and the Creative Audigy. Both use the snd_intel_hda. You have to make sure the one driver you use is loaded the latter, that means for my case adding into /etc/initramfs-tools/modules the name of the nvidia driver, simply nvidia (+nvidia_uvm but that does nothing with the sound) because I want the Creative to blast. This is now included into initramfs and loaded just before the kernel jumps to hdd reading. Please do not forget the command update-initramfs -u after changing /etc/initramfs-tools/modules. If you have n sound cards, just add the n-1 ones you don not want to use as primary output to that file. The only possible way I can see problems with that when you have two cards of the same type installed. Otherwise you should be fine.

I am running linux-3.16.1 now with awesome sound, nvidia GTX750 driver from thier webite and all GPU computing enabled. (Yes, while listening to music)

janK

---

