---
title: "Tenx Sound card - Missing volume control"
date: 2010-02-05
forum: Hardware
---

### Post by Max-P on 2010-02-05
Hi all,

I have an USB sound card that on which the volume control doesn't work. Alsamixer only reports a "PCM" volume control and it's the same for PulseAudio. The card itself works nicely with no problems except that I can't control its volume. Since I use it for my headphones, I can't just keep it at 100% volume, it's way too loud.

PulseAudio calls it "USB Audio" and "audio headset Analog Stereo" (depending on where I get the name).

lsusb
```
Bus 004 Device 003: ID 1130:f211 Tenx Technology, Inc. audio headset

```

I read many posts saying that this card should be avoided, but I got one. :-| 

Moving the volume slider doesn't do anything except at 8% which turns it on/off.

It there a way to get it working? I read that it is possible to do something called softvol using Alsa but since it is automatically detected and loaded, I can't write it in config files.

Thanks

---

### Post by Max-P on 2010-02-08
Nobody?

---

### Post by Pifilatakanemu on 2010-04-13
any news?
i bought the soundcard, too but I'm not sure how to use it...

---

### Post by Max-P on 2010-04-14
Still not fixed. I sad but I never got any answer that fixed my problem on these forums.

The latest version of PulseAudio just broke my last workaround: now the hardware volumes is linked with the software volume, which blocks me even further because hardware volume has to stay to 100%.

I'm still searching for a solution, if you find one let me know

---

### Post by Max-P on 2010-07-16
Hi again everyone,

I just found out how to do it. I stopped using this card for a while, that's why I took so long to find out how, but now it's almost fixed.

Here's how, for others who might fall on this thread for help:

Step #1: We have to define the card as "softvol" in alsa, si lets edit our .asoundrc:

```

gksudo gedit ~/.asoundrc

```

Now copy this at the end (the file is probably empty, even not existing yet):

```

pcm.usbsoft {
	type softvol
	slave {
		pcm "hw:1,0"
	}
	control {
		name "Master"
		card 0
	}
}

```

Be sure to change hw:1,0 to the correct soundcard. Any ALSA mixer will give it.

In short, I define a new ALSA output, which will be used later by pulseaudio. Since its type is softvol, ALSA will decrease the volume of the audio before sending it on the card, which will always be at 100%.

Step #2

This time, we will edit /etc/pulse/default.pa . We also can edit the user's configuration in ~/.pulse, but I don't really know how it works, si I take the easy way.

```

gksudo gedit /etc/pulse/default.pa 

```

and add at the end:

```

# Tenx USB Soundcard fix
.fail
load-module module-alsa-sink device=usbsoft sink_name=usbsoft sink_properties=device.description=Tenx_USB_Card
.nofail

```

This just add a basic ALSA sink to pulseaudio. I works fine without any problems with the usual autodectection that Ubuntu uses since pulseaudio comes shipped with it. Other devices will continue to work properly.

Note: I putted the .fail tag before, so if the card is not plugged in, pulseaudio will still start (otherwise, it just won't start).

Step #3: Restart pulseaudio:

```

pulseaudio -k
pulseaudio -D

```

If there's no message after that, then everything should work fine. Juste redirect your streams to Tenx_USB_Card and enjoy your cheap card, now with a working volume control!


Removing the card doesn't cause any problem, but the USB card won't get loaded automatically anymore. it will be loaded on the pulseaudio's startup or when done manually with this command:

```

pactl load-module module-alsa-sink device=usbsoft sink_name=usbsoft sink_properties=device.description=Tenx_USB_Card

```


If someone knows how to make it load automatically, please let me know!

---

