---
title: "Toshiba sattelite L665 headphone sense issue"
date: 2010-09-22
forum: Hardware
---

### Post by chhhhris on 2010-09-22
Hi, im having an issue many of you are probably already familiar with. When i have my headphones plugged in my computer my pc speaker don't disable. Also ive searched many different fixes none seem to work and alsa does not have a "headphone jack sense" option. Please help!

Edit: This is a Toshiba  Satellite L655

---

### Post by gareththered on 2010-10-17
Hi,

You've probably fixed it by now, but just in case...

I fixed my L655 by installing the latest alsa drivers from the ppa.

Just follow [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

After this both the headphones and microphone sockets work correctly.

---

### Post by canucked on 2010-12-09
If gareththered's suggestion of installing the latest alsa modules from the PPA don't work for you (it didn't for me on a Toshiba Satellite L655-S5115), you can try this:

Running this in Terminal:
```
cat /proc/asound/card0/codec#* | grep Codec
```

...revealed that the audio is Conexant CX20585.

To fix the audio, I did this:
Edit /etc/modprobe.d/alsa-base.conf and add:
```
options snd-hda-intel model=thinkpad
```

I provide more detail in a thread I started about that laptop:
[http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

Hope this works for you!

---

