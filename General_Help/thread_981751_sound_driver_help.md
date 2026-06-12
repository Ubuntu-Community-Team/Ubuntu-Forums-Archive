---
title: "sound driver help"
date: 2008-11-14
forum: General Help
---

### Post by moparfan90 on 2008-11-14
cant seem to get my sound to work.
fresh 8.10 32bit install on my hp tx2000 laptop. 

```
moparfan90@moparfan90-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

 i have tried a couple different things. nothing has worked yet. any ideas?

---

### Post by cyclobs on 2008-11-14
what have you actually done?

---

### Post by moparfan90 on 2008-11-14
i tried a script that installs the new alsa. i tried some other how to on installing alsa. didnt change anything. i searched the forums. but all the similar laptops i find are intel chips. and mine ati. so im not sure what to do.

---

### Post by gali98 on 2008-11-14
You tried the one from realtek, didn't you? It doesn't work as you know.. it just messes stuff up.
If you have ati sound, then you actually have the tx2500 (check the bottom label to make sure.)
Basically, what I suggest you do (only if you have a tx2500!)
is run these commands:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall linux-image-2.6.27-7-generic

then follow the advice in this post...
[http://ubuntuforums.org/showpost.php?p=6128598&postcount=4](http://ubuntuforums.org/showpost.php?p=6128598&postcount=4)

if you have the tx2000 then sound works by default, but you may need to change a few sound sliders..
Kory

---

