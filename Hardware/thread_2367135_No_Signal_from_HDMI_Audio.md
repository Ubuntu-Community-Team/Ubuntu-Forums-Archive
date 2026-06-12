---
title: "No Signal from HDMI Audio"
date: 2017-07-26
forum: Hardware
---

### Post by topgunman on 2017-07-26
Hi,

My problem is i can't make the HDMI Port deliver signal (Under Windows 7 works just fine [IMG]https://forums.linuxmint.com/images/smilies/icon_sad.gif[/IMG] ). I have GTX970
Already installed NVidia driver successfully.
I  have selected HDMI as default output. Linux detects it as  "GM204 High Definition Audio Controller Digital Stereo (HDMI)", ao far  so good, but no signal

What do I need to do, install maybe missing packages or i do something incorrect?

---

### Post by Autodave on 2017-07-26
Hmmm.....what driver did you install and where did you get it from?

---

### Post by BenginM on 2017-07-26
Did you reboot while the HDMI cable plugged in both the TV and the laptop !

---

### Post by papibe on 2017-07-26
Hi topgunman.

Could you open a terminal, run these commands, and post back the results (you can copy/paste the text using the mouse)?
```
lspci -nnk | grep -iA2 vga

aplay -l

pactl info | grep -i default
```
Regards.

---

### Post by vocx on 2017-07-26
> **topgunman said:**
> Hi,

My problem is i can't make the HDMI Port deliver signal (Under Windows 7 works just fine [IMG]https://forums.linuxmint.com/images/smilies/icon_sad.gif[/IMG] ). I have GTX970
Already installed NVidia driver successfully.
I  have selected HDMI as default output. Linux detects it as  "GM204 High Definition Audio Controller Digital Stereo (HDMI)", ao far  so good, but no signal

What do I need to do, install maybe missing packages or i do something incorrect?
This seems to be a bug with Nvidia cards, and their proprietary drivers. Maybe when paired with integrated Intel video cards, as is common in some laptops.

I have the same problem, and I have resigned myself to not have audio through HDMI any time soon. It is not very important to me, as I normally use headphones, but I think it's a problem if you want to watch a movie on TV or so.

There are several reports online about this issue.
[https://bugzilla.redhat.com/show_bug.cgi?id=1440797](https://bugzilla.redhat.com/show_bug.cgi?id=1440797)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1377653?comments=all](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1377653?comments=all)
[https://askubuntu.com/questions/641172/does-not-detect-my-sound-card-hdmi](https://askubuntu.com/questions/641172/does-not-detect-my-sound-card-hdmi)

Another symptom or a related problem is that when you select HDMI audio as output in your sound options, you do get audio but it is very slowed down, as if you were listening in slow-motion.
[https://askubuntu.com/questions/805355/sound-over-hdmi-is-2x-as-slow-after-resuming-from-standby](https://askubuntu.com/questions/805355/sound-over-hdmi-is-2x-as-slow-after-resuming-from-standby)

Some threads report that the problem is with the "nvidia" proprietary drivers, so there is no way to solve it but to wait for better drivers. Others think the issue is with "alsa", the audio drivers of Linux. I didn't try all the possible solutions, so I didn't dig deeper.

Maybe it's also the fault of the monitor or TV? Who knows. My personal experience is that when I tried HDMI audio with my cheap monitor, the sound didn't come out well. Then I tried HDMI audio with a Samsung TV at work, and the sound came out perfectly, as it should. So, I just assumed my monitor was at fault. I thought I should have bought a good monitor, instead of this cheap, no-brand one. Several weeks passed. I installed the regular updates of my system, so I assume I installed new kernel, video drivers, etc. Now, my monitor still doesn't output good sound, and the TV at work no longer works as it did that one time. So, I guess the problem was fixed in one kernel update, but then another kernel update happened, introducing a regression. Unfortunately, I didn't write down the version of the kernel in which the audio worked fine. If I had made a note about it, I could have helped pinpoint more specifically the problem.

I'm using 16.04, with a 4.4.0-87 kernel, with nvidia-375, so your experience may be different with other kernels and drivers. If you want to troubleshoot this, you should probably install a newer kernel, with newer nvidia drivers, but remember this is all at your own risk. I think I read somewhere that the issue could be solved in a 4.10 kernel, but I cannot find the thread now, so test at your own risk.

---

### Post by Autodave on 2017-07-27
I believe that the GTX970 is a desktop only card. (Could be wrong on that though.....) With the desktop cards, I have never had a problem with the HDMI other than having to turn it on in *pavucontrol*.

---

### Post by topgunman on 2017-07-27
Thank you @papibe

Here's Response from the Konsole:

 ~ $ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM204 [GeForce GTX 970] [10de:13c2] (rev a1)
        Subsystem: CardExpert Technology GM204 [GeForce GTX 970] [10b0:13c2]
        Kernel driver in use: nvidia
me@PC ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC1150 Analog [ALC1150 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC1150 Digital [ALC1150 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
me@PC ~ $ pactl info | grep -i default
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_01_00.1.hdmi-stereo
Default Source: alsa_input.pci-0000_00_1b.0.analog-stereo

---

### Post by Autodave on 2017-07-27
Where did you get the driver from? And what one are you using?

---

### Post by efflandt on 2017-07-28
In the Sound Settings gui I am use to seeing HDMI audio listed as simply "HDMI / DisplayPort HDA NVidia". And that works even using a DVI to HDMI cable (which has worked since GTX 200 series). I stumbled on that by accident when using wireless headphones in digital mode when batteries ran down, I unplugged USB dongle for the headset, and it automatically switched to my HDTV speakers. I normally use analog stereo (Line Out Built-in Audio) for 2.1 PC speaker system with subwoofer.

Although, I just noticed that if I do the speaker test (Front Left / Front Right) in Sound Settings, on HDMI there seems to be some static that I do not hear on analog stereo. I am currently running Ubuntu 16.10 (which I need to change soon) with nvidia-381 driver package from graphics-drivers ppa for GTX 1060 to 32" 1080p HDTV as monitor.

---

