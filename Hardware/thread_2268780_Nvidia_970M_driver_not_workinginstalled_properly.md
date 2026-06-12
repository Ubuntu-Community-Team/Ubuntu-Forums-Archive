---
title: "Nvidia 970M driver not working/installed properly?"
date: 2015-03-11
forum: Hardware
---

### Post by rohan8 on 2015-03-11
Hi

I've been having a little trouble for a while trying to get my nvidia drivers working. 
I have a Geforce 970m running on Kubuntu 14.10, and the current nvidia version driver that I have managed to install is version 346.

Any application that requires 3d acceleration runs quite slow, so I'm under the impression that the drivers are not working as intended.

When checking on the video driver using :  lspci | grep VGA , I get the following output:

[B]00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 13d8 (rev a1)[/B]

When I use glxgears to check the framerate to test it I get:

[B]306 frames in 5.0 seconds = 61.128 FPS                                                                          
301 frames in 5.0 seconds = 60.015 FPS                                                                          
301 frames in 5.0 seconds = 60.020 FPS                                                                          
301 frames in 5.0 seconds = 60.019 FPS                                                                          
301 frames in 5.0 seconds = 60.021 FPS [/B]

Although I've read it should be much higher (200+) if the graphics card is actually working.

If someone could give me a few tips on getting the drivers working it would be greatly appreciated.

---

### Post by dino99 on 2015-03-11
so try to reinstall , but after purging the installed driver

- sudo apt-get purge nvidia*
then follow that howto  [http://ubuntuhandbook.org/index.php/2014/11/install-nvidia-driver-346-16-beta/](http://ubuntuhandbook.org/index.php/2014/11/install-nvidia-driver-346-16-beta/)

---

### Post by rohan8 on 2015-03-11
Reinstalled using that ppa, didn't work at first, but after I added "quiet splash nomodeset&#8221; to the grub and added :

*blacklist vga16fb*
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
blacklist lbm-nouveua
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off 

to the blacklist from this thread as well [http://ubuntuforums.org/showthread.php?t=2263316](http://ubuntuforums.org/showthread.php?t=2263316)

Now the install from the ppa seems to be working now as I have from glxgears this output now:

[B]4012 frames in 5.0 seconds = 802.351 FPS
4422 frames in 5.0 seconds = 884.372 FPS
5004 frames in 5.0 seconds = 1000.775 FPS
4543 frames in 5.0 seconds = 907.409 FPS
3571 frames in 5.0 seconds = 714.155 FPS

[/B]thanks for the help

---

