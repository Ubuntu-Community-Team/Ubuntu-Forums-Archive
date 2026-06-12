---
title: "reinstalling alsa?"
date: 2008-10-06
forum: General Help
---

### Post by Sylvertwyst on 2008-10-06
hello all

i tried following [this]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=868227") tutuorial to set up my usb maya44 audio interface.

i'll just quickly summarize what i did. 
download, extract and patch alsa
remove old alsa configs 

while at first it seemed that the install was going smoothly (i did have to install kernel heaers first), after install i am unable to produce any sound.

this is the end of my console output at trying to configure and making new alsa driver.
```
 ...
  LD [M]  /home/chaitanya/maya44/alsa-driver-1.0.17/acore/snd-timer.o
  LD [M]  /home/chaitanya/maya44/alsa-driver-1.0.17/acore/snd-pcm.o
  LD [M]  /home/chaitanya/maya44/alsa-driver-1.0.17/acore/snd-page-alloc.o
  LD [M]  /home/chaitanya/maya44/alsa-driver-1.0.17/acore/snd-rawmidi.o
  CC [M]  /home/chaitanya/maya44/alsa-driver-1.0.17/i2c/other/wm8776.o
gcc: /home/chaitanya/maya44/alsa-driver-1.0.17/i2c/other/wm8776.c: No such file or directory
gcc: no input files
make[4]: *** [/home/chaitanya/maya44/alsa-driver-1.0.17/i2c/other/wm8776.o] Error 1
make[3]: *** [/home/chaitanya/maya44/alsa-driver-1.0.17/i2c/other] Error 2
make[2]: *** [/home/chaitanya/maya44/alsa-driver-1.0.17/i2c] Error 2
make[1]: *** [_module_/home/chaitanya/maya44/alsa-driver-1.0.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-rt'
make: *** [compile] Error 2
chaitanya@VoUBU-chaitanya:~/maya44/alsa-driver-1.0.17$ 

```

paying not much attention i skiped one step ahead, and completed the howto. however now, if i go to system>preferences>sound, none of the tests work, getting the error that gstreamer has either wrong plugins installed, or there is no audio card to test on.

my question is twofold.

how can i have seperate settings for my usb audio device and my onboard one. so i can switch easily when i need to go on the road.

and secondly, if i cant get the maya44 to work, i'd obviously rather have the onboard card handle stuff, as it was just right out of the box with the hardy upgrade

in case it matters, i shifted to ubuntu studio with the included repositories. (on a side note, would simply uninstalling them via synaptics cause my system harm?) and i run on a dell Vostro 1500

thank you much in advance, 
Sylvertwyst

---

### Post by Sylvertwyst on 2008-10-06
bump ><

---

### Post by Sylvertwyst on 2008-10-06
._. anyone?  life is dull without my rhythmbox

---

