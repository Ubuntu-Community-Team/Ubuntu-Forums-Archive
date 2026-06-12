---
title: "Toshiba Satellite C655 - Lucid 10.04 no headphone output, speakers don't mute"
date: 2010-07-28
forum: Hardware
---

### Post by jfp550 on 2010-07-28
I recently bought a brand new Toshiba C655 laptop. The BIOS has ACPI issues that have been addressed in kernel 2.6.35rc3 which I have installed.

The built-in speakers keep playing when headphones are plugged in and the headphones are silent.

I've searched and tried a number of different 'options snd_hda_intel model=foobar' in /etc/modprobe.d/alsa-base.conf. I've also installed alsa 1.0.23. No joy.

I would really like headphones to play sound and mute the speakers. Help?

And thank you!

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant CX20585

---

### Post by lidex on 2010-07-28
You could try this one. Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=laptop position_fix=1 enable=yes

```
Save. Close. Reboot.

Or you can try the linuxant drivers:
[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

---

### Post by jfp550 on 2010-07-28
Thanks. I tried it:
 options snd-hda-intel model=laptop position_fix=1 enable=yes
No joy.

---

### Post by djbokka on 2010-12-12
Any luck on this issue? I'm having the same problem and the suggested solution didn't work for me either.

---

### Post by pimy on 2010-12-18
I am running 10.10.

After seeing this[ https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/637040]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/637040")
I tried the models that were listed, but they did not work. In fact, no hardware was even detected when I used those models.

I went back to using toshiba as my model, and got the latest linux alsa drivers according to the instructions here:

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

I rebooted and now the headphone is working as expected.

Best of luck to you.

---

### Post by TorinThe on 2011-02-22
Just wanted to confirm pimy's post.  I'm running 10.04 on a Satellite C655.  Updated the alsa-drivers, and headphones work as expected.  Thanks!

---

