---
title: "Spontaneous speaker crackle on laptop in Karmic Koala"
date: 2009-11-04
forum: Hardware
---

### Post by p1977p on 2009-11-04
I recently upgraded to Karmic Koala . The upgrade went flawlessly, but since then I have have noticed that the speakers give off an intermittent cracke every 10 -15 seconds , even if no audio file is being played. This happens even if if tap on the laptop Vol UP/down keys, but strangely does not occur everytime if i do it in quick succession. Seems as if some time is required for charge - like thing to build up ????. Pl. help

I'm running Ubuntu 9.10 32 bit on a Compaq AMD-Turion 64-bit  laptop with NVIDIA graphics card.

---

### Post by Talon1205 on 2009-11-04
I am having the same issue on my HP Pavilion dv 6000. I get one crackle then one second later i get two crackles then ten seconds later it starts over again.

I hear it on both the laptop speakers and external speakers at the same time. But when I disconnect the external speakers it stops after one more single crackle.

I thought at first it may be a system sound that was supposed to be a click or tic sound, but it is not effected by the volume setting or mute.

---

### Post by Aerodynamic on 2009-11-04
I suspect you're using a high definition sound card? check that with lspci in the terminal.


I found the solution to this problem in this thread [http://ubuntuforums.org/showthread.php?t=1306963](http://ubuntuforums.org/showthread.php?t=1306963)

It seems that the power saving feature with high definition sound card doesn't work so good.

			 		   		 		 		Audio device: Intel Corporation 82801G (ICH7 Family) High Definition AudioController (rev 01)

Problem solved after commenting the line #options snd-hda-intel power_save=10 power_save_controller=N in the file /etc/modprobe.d/alsa-base.conf

---

### Post by Talon1205 on 2009-11-06
Thanks, that did it!

---

### Post by p1977p on 2009-11-10
Worked well... thanks!!

---

### Post by snakeman21 on 2009-11-27
THANK YOU!!!  That was my only problem with Karmic on my HP dv6000!

---

