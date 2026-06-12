---
title: "Mic not working in Ubuntu 12.04 - Lenovo G470"
date: 2012-06-26
forum: Hardware
---

### Post by caveman7 on 2012-06-26
Hi all. I used a Lenovo G470 laptop (Core i5 2410M processor, AMD Radeon 6370M and 2GB DDR3 RAM) and I installed Ubuntu 12.04.
I can't get the microphone to work. I encountered this type of issue before in my old Acer Aspire One with Ubuntu 10.04/10.10, and installing PulseAudio Volume Control and tweaking a little solves the problem. I tried the same solution to no avail.

cat /proc/asound/card0/codec* | grep Codec gives the following result:
Codec: Conexant CX20590
Codec: Intel CougarPoint HDMI

Does anybody encountered a similar problem? Any help will be greatly appreciated.

---

### Post by nipunshakya on 2012-06-27
see the following link... maybe something can come up..
[http://askubuntu.com/questions/135778/no-sound-on-ubuntu-12-04](http://askubuntu.com/questions/135778/no-sound-on-ubuntu-12-04)

---

### Post by www.rzr.online.fr on 2012-07-06
I own a g470 too ... 

now on debian but I had to tweek a bit hda audio :

[http://rzr.online.fr/q/hda](http://rzr.online.fr/q/hda)

---

### Post by Rambo Tribble on 2012-07-06
I had a similar problem that was resolved by using alsamixer from the command line and increasing the gain on the "Mic" setting.

---

### Post by caveman7 on 2012-07-12
> **www.rzr.online.fr said:**
> I own a g470 too ... 

now on debian but I had to tweek a bit hda audio :

[http://rzr.online.fr/q/hda](http://rzr.online.fr/q/hda)

I'm very sorry but I'm confused when reading your link. Is there any manual/guide that I can follow?

> **Rambo Tribble said:**
> I had a similar problem that was resolved by using alsamixer from the command line and increasing the gain on the "Mic" setting.

Do you mean the Analog Mic? I tried that to no avail :(

[IMG]http://i790.photobucket.com/albums/yy183/caveman712/Screenshotfrom2012-07-13091949.png[/IMG]

---

### Post by caveman7 on 2012-07-12
Never mind. Found the solution: [http://u0x.blog138.fc2.com/blog-entry-98.html](http://u0x.blog138.fc2.com/blog-entry-98.html)

Thanks RzR!!

---

### Post by jmfal on 2012-07-12
Try changing the sound card and see if the mic can be  increased

---

### Post by americanman28 on 2012-07-12
Maybe you need to change the default device

---

### Post by caveman7 on 2012-09-16
> **caveman7 said:**
> Never mind. Found the solution: [http://u0x.blog138.fc2.com/blog-entry-98.html](http://u0x.blog138.fc2.com/blog-entry-98.html)

Thanks RzR!!

Copied the solution just in case the website goes down:


> Solution : 

1.gksu gedit /etc/modprobe.d/alsa-base.conf
2.add this line "options snd-hda-intel model=asus"

now microphone gonna work but very low volume 

3.make sure you already installed packages PluseAudio Device Chooser,PulseAudio Vulume Control, PulseAudio Manager, PulseAudio Preferences, PulseAudio Volume Meter (Playback),PulseAudio Volume Meter (Capture) 
4.runs "PulseAudio Device Chooser". the icon appears on indicator bar, click it go to "Manager...", go to tabs "Devices"
5.select which your current audio device and click "Properties"
6.try to changes "Volunme:" bar as you need (carefully about noisy sound)


---

### Post by caveman7 on 2013-03-07
In Ubuntu 12.04, PulseAudio Device Chooser is not available, as an alternative, refer to: [http://askubuntu.com/questions/122226/microphone-not-working-on-lenovo-g470](http://askubuntu.com/questions/122226/microphone-not-working-on-lenovo-g470)

---

