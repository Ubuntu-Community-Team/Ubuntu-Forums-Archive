---
title: "No sound on Compaq Armada m700 with XUbuntu"
date: 2010-05-14
forum: Hardware
---

### Post by pgcg99 on 2010-05-14
Hi.  I had orriginally installed Ubuntu on my Compaq Armada m700.  The  sound worked right away without any tinkering at all.  I found the OS a  little sluggish, so switched to XUbuntu.  Now the sound doesn't work at  all and I can't seem to get it working.

I have followed all the steps in the thread Comprehensive Sound Problem  Solutions Guide ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)), but  have not gotten anywhere.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: E2E [ESS ES1978 (Maestro 2E)], device 0: ESS Maestro [ESS  Maestro]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3

sudo modprobe snd-es1968
*No output, just the command prompt*

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
reboot
[I]All commands worked, but still no sound.
[/I]
alsamixer
Screenshot attached, but master volume is not muted and at 100%.

Also, my laptop's fn+F5 function for controlling the sound at the hardware level doesn't do anything.  I'm not sure if that is relevant or not.  I can't get any of the laptop fn functions to work.

Any ideas anyone has would be appreciated.

Thanks!

---

### Post by lidex on 2010-05-14
What happens with this command:
```
pulseaudio & pavucontrol
```

---

### Post by pgcg99 on 2010-05-15
pulseaudio & pavucontrol
[1] 1374
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
The program 'pavucontrol' is currently not installed.  You can install it by typing:
sudo apt-get install pavucontrol
[1]+  Exit 1                  pulseaudio

I'm not sure if pavucontrol is supposed to be installed or not.

---

### Post by lidex on 2010-05-16
> **pgcg99 said:**
> pulseaudio & pavucontrol
[1] 1374
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
The program 'pavucontrol' is currently not installed.  You can install it by typing:
sudo apt-get install pavucontrol
[1]+  Exit 1                  pulseaudio

I'm not sure if pavucontrol is supposed to be installed or not.

It may help - certainly won't hurt. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. *_Also helpful is the make/model of your PC/Laptop._*

---

### Post by pgcg99 on 2010-05-31
Thanks for you help.  I have this solved now.  It actually was the hardware speaker where pressing fn+F5 fixed it.  I booted to a Windows desktop to get access to the key.
 
Any idea why the fn keys do not work in XUbuntu?

---

