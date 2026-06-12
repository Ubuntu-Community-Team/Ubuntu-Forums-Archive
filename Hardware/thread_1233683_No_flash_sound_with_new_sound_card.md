---
title: "No flash sound with new sound card"
date: 2009-08-06
forum: Hardware
---

### Post by linux_paul on 2009-08-06
I bought a new sound card to get SPIDF conectivity to my amp since I use the pc as a media center. I can play all local files fine however, I get no sound on flash sites. I set gstreamer-properties as follows and get the test tone:```
Default Output: Alsa 
Device: IEC1724 IEC958
pipeline: alsasink device ="hw:1,1"
```

And here is the output of sudo lspci -v:```
02:05.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
	Subsystem: VIA Technologies Inc. Device 2403
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at e800 [size=32]
	I/O ports at e400 [size=128]
	Capabilities: [80] Power Management version 1
	Kernel driver in use: ICE1724
	Kernel modules: snd-ice1724
```

Lastly I'm running the 64-bit version of Jaunty. Can anyone help or is this a 64-bit issue I have to live with?

Thanks,
paul

---

### Post by Yellow Pasque on 2009-08-07
Are you using the native 64-bit Flash player or the 32-bit one from the repos? If you're using the 32-bit Flash, you'll need probably need the lib32asound2 package.

---

### Post by linux_paul on 2009-08-08
Thanks for the reply. I'm using the repo version and I do have lib32asound2 installed. How would I get the 64-bit version to try?

---

### Post by linux_paul on 2009-08-09
Alright I installed the 64-bit version of flashplayer but still no luck. I suspect its a driver/hardware issue associated with linux.

Can anyone else offer a suggestion to fix this issue or suggest a good relatively inexpensive sound card with full spidf support.

---

### Post by MediocreBadGuy on 2009-08-10
I had this exact same problem and it took forever to figure it out but theres a quick and painless way to solve it.  You can't choose what soundcard you want flash to play through, so you have to get PulseAudio and choose through there.

Synaptic Package
type pulse in search
check paddevchooser
click apply

once installed
applications
sound
pulse audio device chooser
click icon in top right
volume control
change the playback to your new soundcard
hope it works, this seems to be a pretty common problem

---

