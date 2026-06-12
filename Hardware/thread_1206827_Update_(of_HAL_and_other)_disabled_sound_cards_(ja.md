---
title: "Update (of HAL and other) disabled sound cards (jaunty)"
date: 2009-07-07
forum: Hardware
---

### Post by Antonio Tavares on 2009-07-07
Hi!
I have a media server with Ubuntu 9.04 jaunty (not remix) on my ACER ASPIRE ONE. I could never use the wifi card, but that's OK, as I don't need it now. The sound was working, sometimes with some noise overlayed, but since I've made the latest update this morning, **the sound stopped**. I've noticed that there was an HAL "update" and other things I don't remember.

-I've tryed everything in "Sound Problem Solutions Guide" - [http://ubuntuforums.org/showthread.php?t=205449&page=2](http://ubuntuforums.org/showthread.php?t=205449&page=2) but nothing worked;
-I've upgraded Alsa from 1.0.18rc3 to 1.0.20 with success but that also didn't solve the problem
-I've installed an USB "Sound Blaster Extigy" sound device, and it also doesn't work.

Doing the tests on "Sound Problem Solutions Guide" I get the following:
#sudo su
#aplay -l
aplay: device_list:221: no soundcard found...

#lsusb
Bus 001 Device 007: ID 041e:3000 Creative Technology, Ltd SoundBlaster Extigy

#lspci -v
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 015b
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 58540000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel modules: snd-hda-intel

#alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory

That's the point I couldn't follow the instructions (because of this error).

The driver for the Sound Blaster Extigy seems to be described in [http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio](http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio)
The driver for my Intel PCI internal card appears to be in:
[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0)

After 6 hours work, I'm about to reinstall Ubuntu, but I suspect that it will not work, as it is probably a bug on the latest HAL or something else related to today's update.
Can someone help?

---

### Post by shatterblast on 2009-07-07
As a temporary solution, you can try switching from ALSA to OSS.  This can be done from:

System -> Preferences -> Sounds -> Switching everything to OSS

I think the update process might have a recognized issue with Creative over all because of how ALSA integrates with it.  An alternate solution would be switching over to PulseAudio, which can get potentially deep into the technical side.  It has limited benefits for sound-editting.

In a few rare cases, the settings for ALSA require deletion at the folder level.  Reinstalling Ubuntu would do this.  If you choose this route, you might want to "lock version" on your ALSA things through Synaptic.

---

### Post by Antonio Tavares on 2009-07-07
Thank you for your help shatterblast!

I've tryed to switch to OSS but it's the same as with ALSA. After testing, instead of a sound it gave me this message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink:
"Não foi possível abrir o dispositivo áudio para reprodução."

Translation: "Couldn't open the audio device for playing."

If I try Pulse Audio, instead of a sound I just get a message box saying:
A testar - Prima Ok para terminar
Translation: "Testing - Press OK to end"
But the sound never appears! Frustrating...

---

### Post by shatterblast on 2009-07-07
I'll agree with the idea of software updates possibly causing the conflict.  An update may come down in a week or so that fixes the problem.  Setting your updates to weekly may also help avoid the issue in the future.  That can be done through:

System -> Administration -> Software Sources -> the Updates tab at the top.

The next suggestion involves installing the Karmic test versions of ALSA.  I think the following are the appropriate ones:

[http://packages.ubuntu.com/karmic/alsa-base](http://packages.ubuntu.com/karmic/alsa-base)
[http://packages.ubuntu.com/karmic/alsa-firmware-loaders](http://packages.ubuntu.com/karmic/alsa-firmware-loaders)
[http://packages.ubuntu.com/karmic/alsa-source](http://packages.ubuntu.com/karmic/alsa-source)

---

### Post by Antonio Tavares on 2009-07-07
I've installed all the debs and all the dependencies.
After a reboot sound was still not working, but this time I've noticed that a configuration file was wrong:
#cat /etc/modprobe.d/alsa-base.save
options snd-hda-intel model=ALC268options snd-hda-intel model=ALC268options snd-hda-intel model=ALC268

The same option was repeated 3 times, so it was invalid!
I corrected to:
options snd-hda-intel model=ALC268
and rebooted
This time, after puting up the volume running:
# alsamixer
... sound was working!!!
I've installed again the sound volume icon on the toolbar, and all was ready.
Conclusion:
This mess was caused by **/etc/modprobe.d/alsa-base.save** erroneously configured. This type of error is not directly human. It's common to appear in installation scripts. This must be an **error on the latest update of Ubuntu Jaunty**. I have little doubt of it.

Note: I've changed the update to weekly, instead of daily, as you advised

Thank you for your precious help shatterblast. We've discovered this bug thanks to your instructions.

---

### Post by shatterblast on 2009-07-08
Wow.  Good job.  Just remember I only provided advice.  I suggest keeping a back-up of that file and storing it somewhere safe in your profile since such things tend to be valuable on Ubuntu.

---

