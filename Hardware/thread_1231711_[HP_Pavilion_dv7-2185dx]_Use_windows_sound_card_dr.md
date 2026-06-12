---
title: "[HP Pavilion dv7-2185dx] Use windows sound card driver in Ubuntu?"
date: 2009-08-04
forum: Hardware
---

### Post by ramidavis on 2009-08-04
To make a long story short, i got a new HP pavilion dv7-2185dx (System Specifications [here]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01753029&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN")) and as far as i can tell, everything is going great... But i have no sound. While booting into ubuntu, i can hear the speakers 'pop' a little, my only guess is ubuntu is probing them, but then not finding a suitable driver? 

P.S. I am dual booting vista x64 and using 9.04 x64 ubuntu. Tried a 32 bit 9.04 live dvd, and again no sound. When i use the touch-sensitive volume control, it does show the volume changing. Just tried a sound file in the Examples folder, and the media control touch-sensitive play/puase, forward back, and stop all work. Just too bad i can not hear it. Headphones are a no go as well. Would also like to point out that gparted live cd version 0.4.5-2 managed to make a short 'blip' sound as i told it to reboot my machine. If gparted live can do it, then there has to be a way with ubuntu, right? Any way, any help getting sound to work would be great.

---

### Post by ramidavis on 2009-08-05
Bump

I'm sorry, if this is in the wrong place, please let me know, or have a mod move it.


OK, so i found my answer, from this [thread, first post.]("http://ubuntuforums.org/showthread.php?t=1073090&highlight=hp+pavilion"):
The latest alsa-driver snapshot provides a fix for this issue. You can get it here:

[ftp://ftp.kernel.org/pub/linux/kerne...napshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kerne...napshot.tar.gz)

After downloading and gzip/tarring the files, you'll need sudo privileges to:
#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo vim /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]
#> sudo reboot

If any one else has this laptop, these steps should work for you.

---

