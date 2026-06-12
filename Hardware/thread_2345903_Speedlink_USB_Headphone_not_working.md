---
title: "Speedlink USB Headphone not working"
date: 2016-12-09
forum: Hardware
---

### Post by Macamba on 2016-12-09
I had to install Ubuntu 16.04 over my old installation because my MBR was wiped. The first time I installed my USB Speedlink (SL-4475-BK Xanthos) headphones worked. I had to install a second time, and they stopped working.

If I plug the headphones in the appear in the (System Settings ->) Sound window.
[IMG]https://s13.postimg.org/xm1zzbrjr/Sound_system.png[/IMG]
But no noise is emitted, even when I test it. 

On the [manufacturers site]("http://www.speedlink.com/?p=2&cat=41A3&pid=25428&paus=2") they say:
> **My headset doesn’t work when connected to a USB 3.0 port. What could be causing the problem?**
This problem is usually due to poor sound-chip support provided by older USB 3.0 drivers. Update your USB 3.0 port drivers.

Is this the solution for my problem, and where can I find these drivers?

---

### Post by Macamba on 2016-12-09
And now no sound from my speakers too :confused: :cry:
[IMG]https://s30.postimg.org/pcbaebf0h/Required_plugin_not_found.png[/IMG]

Yesterday at least I had sound from my speakers.

---

### Post by Macamba on 2016-12-10
FWIW, to install the required > ubuntu plugin mpeg-1 layer 3, see [How do I install the ubuntu-restricted extras package?]("http://askubuntu.com/questions/56446/how-do-i-install-the-ubuntu-restricted-extras-package").

The USB headphones from Speedlink are still not working.

---

### Post by Macamba on 2016-12-11
I posted a thread "[Speedlink USB Headphone not working]("https://ubuntuforums.org/showthread.php?t=2345903")" in the Hardware forum, but had no luck getting an answer on this thread. 

I installed 16.04 twice. And if I remember correct, the headphones where working the first time. Two options:
[LIST=1]
[*]Hope someone has the solution, and posts it here
[*]Install 16.04 again
[/LIST]

Should I choose the second one?

---

### Post by coffeecat on 2016-12-11
I've merged your two threads. Your second was posted in the Installation & Upgrades forum, the tagline for which states:

> For questions about upgrading and installation of your new Ubuntu OS.

The Hardware sub-forum is correct. If you don't get a reply to your thread it's ok to "bump" it every so often to bring it up to the top and bring it to the attention of members in different time zones. Please don't post duplicates in different forums - this dilutes community effort and causes confusion.

A few thoughts and suggestions:

You say it worked first time but not on a re-install, which tells us that the driver is in the kernel in a default installation of Ubuntu 16.04, and there's no point in re-installing just for the sake of it. So long as the ISO you used to make your install medium was OK, there's going to be no difference from one install to the next. (Did you check the hashsum of the downloaded ISO?) Which suggests that something has gone wrong between the first install and the second. Have you checked the headphones in another system in another computer? If you want to check Ubuntu 16.04 on your machine without going to the trouble of another re-installation, try a live session from your USB drive or DVD, whichever you used, or you could try live sessions of other distros not related to Ubuntu. I'm not sure what that would achieve, but it might give useful data.

---

### Post by Macamba on 2016-12-18
As suggested I tried the headphones with a Live Session. The headphones worked. I also noticed the 'Headphones audio controller' had a digital and analog entry. So the 'Headphones audio controller' abd the 'Digital output (S/PDIF)' and 'Line out' do not work either.

So, what can I do? Install what and how plugin?

---

### Post by Macamba on 2016-12-21
Still struggling with my sound. As I said earlier, I have no sound in my headphones, and my external speakers. Only the HDMI of the screen have sound. 

I'm working with [SoundTroubleShooting]("https://help.ubuntu.com/community/SoundTroubleshooting").

```
me@system:~$ clear;sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Set [USB Headphone Set], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

This shows the same sound systems available as I shown in the screenshot of the **Sound** window. 

Anyway, my system recognizes the external speakers and headphones are attached to their respective sprockets. But still no sound. And to reiterate, the headphones worked during the Live Session.

The sound card I have is:
```
me@system:~$ lspci -v | grep -A7 -i "audio"
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
	Subsystem: Gigabyte Technology Co., Ltd SBx00 Azalia (Intel HDA)
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

--
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
	Subsystem: XFX Pine Group Inc. Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at fdefc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
```

In a last ditch effort I tried to reinstall my drivers with
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

But my system replied with 
```
sudo: aptitude: command not found

```

So, what options do I have?

---

