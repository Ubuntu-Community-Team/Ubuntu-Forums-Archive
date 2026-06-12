---
title: "No Sound"
date: 2011-09-11
forum: Hardware
---

### Post by mark957 on 2011-09-11
Hello, I did something stupid and tried to install OSS4 on my Ubuntu v10.10 desktop computer.  The install was not successful and I can not remove the OSS4 from the system, also I can not get ALSA and PulseAudio to work again.

The next step I took was to upgrade to Ubuntu v11.04 and that did not help.

I started searching the forums and found this code:
"sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` linux-alsa-driver-modules-$(uname -r) libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` linux-alsa-driver-modules-$(uname -r)  libasound2; killall pulseaudio; rm -r ~/.pulse*"

After I reboot, ALSA and Pulse Audio works, until I shutdown or reboot the system.

After the second reboot, ALSA and Pulse Audio does not work and the only sound modules that are loaded when I do "lsmod" are the following: oss-USB, oss-sblive and osscore.

If I run the code above again I get the ALSA back until I reboot a second time.

Any help will be appreciated.

---

