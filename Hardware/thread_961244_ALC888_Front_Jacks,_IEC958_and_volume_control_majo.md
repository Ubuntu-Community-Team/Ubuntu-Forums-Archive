---
title: "ALC888 Front Jacks, IEC958 and volume control major issues"
date: 2008-10-28
forum: Hardware
---

### Post by SergeiFranco on 2008-10-28
The system is: 8.04, Kubuntu, 64Bit, P965 chipset, with ALC888 (ICH8) sound chip.
The problems are:
No volume control for digital audio via kmix keyboard buttons feature (alsa mixer works - PCM device that controls output), even if I specify master device to be PCM the buttons on the keyboard still move the "Master".
I have made up a softvol to counter the problem in alsa, which did not achieve good result (buttons would ether have only 0 or 10%, the sliders in kmix would get confused, while alsamix would get stuck at ~25%).
I since removed that softvol configuration, even deleted the whole .asoundrc and other associated files, I purged alsa-utils and kmix, reinstall and the bloody softvol slider is still appears in alsamix and kmix. I am confused why it still remembers it even after purging resetting and deletion.
The front jacks randomly work, today it was working but yesterday there were no sound. Hate intermittent problems :(.

Originally I had 32bit 8.04, but I decided that it is a waste to loose 40% of RAM, hence installed 64 bit. I had a working (at least the volume control was working) in 32 bit.

I prefer to use alsa - as it is at least configurable.
I have read that pulseaudio does not detect digital out, digital out is a must, I don't care much if I can't plug in headphones, I always could plug them in the pre-amp.

It really sux to have these features fully supported in windows, while nothing works in linux, while the ALC888 is claimed to be fully supported :(.

So here are the questions:
How it is possible that alsa remebers a softvol plug device even after I purged the alsa, deleted all config files,etc.? I will try purging it and deleting the whole /etc/alsa directory (if it is left behind).
Is there anything better than kmix? (no install GNOME solutions - too dumbed down, mix between vista and mac in my opinion)
Is there a binary blob for this chipset that I can install that works like in windows? (like nvidia driver for example) Although I preffer open source solution (no need to recompile drivers after kernel update)...

---

### Post by SergeiFranco on 2009-08-14
After almost a year, and 2 releases this problem still there.

I am getting sound out of Digital out, but volume control does nothing (master/front/etc).
Also mixing is lacking.

---

### Post by SergeiFranco on 2009-08-14
Here is in depth info of the situation:
A while ago I managed to hack a .asoundrc file that worked well with dmix and volume control:
```

 pcm.!default {
     type            plug
     slave.pcm       "softvol"   #make use of softvol
 }
 
 pcm.softvol {
     type            softvol
     slave {
         pcm         "duplex"
     }
     control {
         name        "Master"
         card        0
     }
 }

pcm.dmixer  {
   type dmix
   ipc_key 1024
   slave {
      pcm "hw:0,1"
      period_time 0
      period_size 1024
      buffer_size 8192
	rate 48000
   }
   bindings {
      0 0
      1 1
   }
}

ctl.dmixer {
   type hw
   card 0
   device 1
}
pcm.dsp {
    type plug
    slave.pcm "dmixer"     # use our new PCM here
}
ctl.mixer {
    type hw
    card 0
}

pcm.dsnooped {
    type dsnoop
    ipc_key 2048
    slave {
      pcm "hw:0,0"
      period_time 0
      period_size 1024
      buffer_size 8192
	rate 48000
    }
	bindings {
	0 0
	1 1
	}

```

So that config worked until I upgraded to jaunty.
It looks like alsa is ignoring my config or something drastically changed.
As if I play sound via amarok, and then I go and see youtube or watch a video, amarok would mute.

And now my master volume control does not work.

EDIT: I have figured that amarok is at fault, it looks like it is using the sound card directly bypassing the Alsa.

---

### Post by mobron on 2009-08-15
I think my problem is simular. Though I don know for sure. 

This is the result of my aplay -l
kaart 0: NVidia [HDA NVidia], apparaat 0: ALC888 Analog [ALC888 Analog]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: NVidia [HDA NVidia], apparaat 1: ALC888 Digital [ALC888 Digital]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: NVidia [HDA NVidia], apparaat 3: NVIDIA HDMI [NVIDIA HDMI]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0

I have a laptop with two sets of speakers and a subwoofer. In Ubuntu, Kubuntu and Mint only the front speaker work in ALC888 analog, but there is no sound on my ALC888 Digital. Installing realtek drivers didn´t seem to do anything. 

with regards 
Robin

---

