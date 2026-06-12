---
title: "reverse procedure for audio device: internal mic"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by nicola76b on 2007-11-29
Hi all.
I already ask it in Italian forum but nobody can tell me how....
PLEASE HELP ME!!

I have a problem in audio device of dell d830 (I need internal mic and it doesn't work)
```
lspci -n | grep `lspci | grep -i audio | awk '{print $1}'` 
00:1b.0 0403: 8086:284b (rev 02)
```


A) times ago all audio system doesn't work; to get it work I made
```
cd /usr/src
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant auto-install alsa
sudo shutdown -r now
```

with these problem:
-output jack does not mute internal speakers
- found no way in kmix to mute internal speakers and output jack independently (as an alternative to item above)
- output jack in the docking station is not working/recognized. the one on the left of the laptop works
- internal microphone does not work at all
- internal speakers do not work after resume from suspend/hibernate - need reboot to get them working again

B) NOW I FIND NEW METHOD: 
([https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)) to get all features:
```
sudo aptitude install linux-backports-modules-generic
 sudo gedit /etc/modprobe.d/alsa-base
 options snd-hda-intel model=dell-m42

```
Save the file and reboot to get sound working correctly.


MY QUESTION IS:
how can I unistall installed parts with A) ???
I try to exec B) without uninstall A but microphone (that I really need) doesn't work...

Thanks a lot 

   -Nicola

---

