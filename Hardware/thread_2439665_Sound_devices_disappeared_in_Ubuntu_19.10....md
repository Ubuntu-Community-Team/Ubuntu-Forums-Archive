---
title: "Sound devices disappeared in Ubuntu 19.10..."
date: 2020-03-30
forum: Hardware
---

### Post by joelgraff on 2020-03-30
So I was trying to test some cross-platform code under a Win10 VM using VirtualBox.  I had to install VirtualBox since I last upgraded Ubuntu.  I then built the VM and did my testing.  Audio was working fine and the audio played in the VM as well.

Unfortunately, after that, the audio just quit.  A little digging reveals that all of my audio devices, save one, have just disappeared.  Those devices are built in speakers, microphone, line-in, and headphones  The only remaining audio device is my HDMI / DisplayPort device.

To this point, I've force-reloaded pulseaudio, purged and reinstalled it, and played with several configuration files, all with no success.

I'm guessing VirtualBox modded the kernel in some way which has left me without most of my laptop's sound devices.  At a loss, though, as to how to go about bringing them back without reinstalling ubuntu...

---

### Post by CelticWarrior on 2020-03-31
No, it isn't related to Virtualbox. It can be related with your experiments though but we can't/shouldn't speculate about it without knowing exactly what you did right before noticing the problem.

---

### Post by joelgraff on 2020-03-31
> **CelticWarrior said:**
> No, it isn't related to Virtualbox. It can be related with your experiments though but we can't/shouldn't speculate about it without knowing exactly what you did right before noticing the problem.

It is undoubtedly related to what I was doing with VirtualBox, as the sound worked fine once I set up my VM in VirtualBox, and then quit functioning on my laptop afterwards - I had not made any changes to my system apart from trying like crazy to get GuestAdditions to work with the Win10 VM properly, which included uninstalling / purging the Ubuntu repo version and installing the latest VB from Oracle...  Right now, I suspect the issue was created during those efforts.

Since I won't be able to retrace my steps exactly, I'm really just looking for a starting point to troubleshoot this.  Given that the system simply doesn't see *any* other sound devices than my HDMI / DisplayPort, I'm guessing it's a kernel module issue...  but again, I'm out of my depth to really feel certain about that or to know where to begin with searching.

---

### Post by CelticWarrior on 2020-03-31
You can try booting with an older kernel to see if it makes a difference or not.

---

### Post by joelgraff on 2020-03-31
Thought of that as I replied on my last post...  duh, lol.

Anyway, I tried an older kernel - no change.  So, that's a start.

For reference, I have two kernels to choose from: 5.3.0-40 and 5.3.0-42.

---

### Post by CelticWarrior on 2020-03-31
Any of the things you did had to do with BIOS/UEFI settings? Typically in a a new UEFI system we would need to disable Secure Boot to allow loading of the Virtualbox drivers for virtual hardware (or sign them with mokutil). Maybe you also disabled the internal audio device (the HDMI audio is part of the graphics subsystem so it wouldn't be affected)?

---

### Post by joelgraff on 2020-03-31
Unless in purging / reinstalling VirtualBox, it somehow affected BIOS / UEFI, then no.  I've done nothing with it - I don't think I've actually accessed that stuff in a couple years. I did poke around in the BIOS / UEFI setup after the problem occurred ust to see if there was  anything that controlled it and I found nothing that directly related to  sound.

The idea that the internal audio device is disabled seems to be the best characterization of the problem, however.

---

