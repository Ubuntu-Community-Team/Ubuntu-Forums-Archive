---
title: "HP Pavilion Webcam &amp; Microphone"
date: 2010-09-04
forum: Hardware
---

### Post by Santaji on 2010-09-04
I installed Ubuntu on my HP Pavilion dv1000 and everything is working fine except the Webcam and Microphone, The microphone is able to detect sounds properly, but when i try to record something and play it back in the Sound Recorder app i just get some weird noises. for the Webcam i downloaded Cheese but it says "No device found". i need to get drivers first right? i did bit of googling but i can't seem to find any useful/easy to understand info about where i can get Linux drives and how to install them.

---

### Post by Santaji on 2010-09-05
Anyone know what i should do?

---

### Post by Veloteuton63 on 2010-09-06
> **Santaji said:**
> Anyone know what i should do?

I do have problems of that kind with my HP Pavillon DV6 (AMD Turion Dual) unknown webcam and ATI SBxxx Azalia soundcard.

I had to fiddle around quite a bit with the Pulsaudio and ALSA installations, following valuable inputs found in these forums and elsewhere on the net. Two links that helped:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/324886]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/324886")

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

Basically after an upgrade of ALSA drivers and the rest plus a re-installation of pulsaudio I managed to find a configuration in which the internal speakers and micro work:
For that I had to start the Pulsaudio Volume control and

a) select analog input / output devices
b) I disabled the HDMI digital profile and soundcard
c) enable and set correctly the volume and microphone settings

After that using skype I manage to get voice input / output.

But then:o:o: Trying the video using the build-in webcam the input devices completely disappear (no microphone). When I try to open the Pulse audio Vol control I get an error message telling: [...] "Connection failed"

And this is where I stand. Additionally headphone and mic jacks do not work (I found treats somewhere but didn't persevere. 
Also: using an external Webcam with microphone after the dysfunction of the internal peripherals works perfectly well, i.e. webcam is correctly mounted an useable the webcam micro shows in the input device list and can be used in skype.

---

### Post by Santaji on 2010-09-07
Thanks for your reply but i'm not understanding anything in your links(i'm a total noob). 
Also tried following the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=280121](http://ubuntuforums.org/showthread.php?t=280121) but it didn't work.

The webcam and microphone are the only hardware that won't work, the speakers, bluetooth, wifi and everything else worked fine without having to do anything.

---

### Post by Veloteuton63 on 2010-09-07
> **Santaji said:**
> Thanks for your reply but i'm not understanding anything in your links(i'm a total noob). 
Also tried following the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=280121](http://ubuntuforums.org/showthread.php?t=280121) but it didn't work.

The webcam and microphone are the only hardware that won't work, the speakers, bluetooth, wifi and everything else worked fine without having to do anything.

The thread you refer to is rather old. I remember having followed it to get a webcam to work on an other computer with an older Ubuntu version. But for me on the HP and with Ubuntu 10.04 the camera worked just fine. 
You should try what is mentioned in the cheese Help (chapter 6.7):

1/ check whether an other program (e.g. SKYPE) recognises the webcam rightclick the skype icon; options/video devices; Select Webcam -> if you have an empty list, then your webcam hasn't been installed correctly.

In that case look here to see whether your device is support and if yes which driver needs installation: [https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

2/ If it works with skype, check your gstreamer installation (using synaptic)

---

### Post by Veloteuton63 on 2010-09-07
> **Santaji said:**
> Thanks for your reply but i'm not understanding anything in your links(i'm a total noob). 
Also tried following the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=280121](http://ubuntuforums.org/showthread.php?t=280121) but it didn't work.

The webcam and microphone are the only hardware that won't work, the speakers, bluetooth, wifi and everything else worked fine without having to do anything.

... And this might solve your mic pbs:

[http://ubuntuforums.org/showpost.php?p=9486962&postcount=62]("http://ubuntuforums.org/showpost.php?p=9486962&postcount=62")

if you like the comfort of a graphical UI, install "alsamixergui" to set you mic settings.

---

### Post by Santaji on 2010-09-07
> **Veloteuton63 said:**
> The thread you refer to is rather old. I remember having followed it to get a webcam to work on an other computer with an older Ubuntu version. But for me on the HP and with Ubuntu 10.04 the camera worked just fine. 
You should try what is mentioned in the cheese Help (chapter 6.7):

1/ check whether an other program (e.g. SKYPE) recognises the webcam rightclick the skype icon; options/video devices; Select Webcam -> if you have an empty list, then your webcam hasn't been installed correctly.

In that case look here to see whether your device is support and if yes which driver needs installation: [https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")

2/ If it works with skype, check your gstreamer installation (using synaptic)

It doesn't work in Skype. i found that it's a "Ricoh Co., Ltd Webcam 1000" by typing "lsusb" in the terminal, in the Ubuntu Wiki link in your post it says i need to download this [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/) so i did and followed the instructions from the Read Me file but it won't work. it says
```
 r5u87x firmware loader v0.2

Searching for device...

Error: Failed to find any supported webcams.

```

---

### Post by Santaji on 2010-09-08
Still haven't got the webcam to work :(

---

### Post by Veloteuton63 on 2010-09-08
> **Santaji said:**
> It doesn't work in Skype. i found that it's a "Ricoh Co., Ltd Webcam 1000" by typing "lsusb" in the terminal, in the Ubuntu Wiki link in your post it says i need to download this [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/) so i did and followed the instructions from the Read Me file but it won't work. it says
```
 r5u87x firmware loader v0.2

Searching for device...

Error: Failed to find any supported webcams.

```

can't be of much help with your issue there. But in the pursuit of my own happiness, I stumbled upon this post:

[https://bugs.launchpad.net/ubuntu/+bug/120434?comments=all]("https://bugs.launchpad.net/ubuntu/+bug/120434?comments=all")

Hope it brings you to a solution ...

---

### Post by Santaji on 2010-10-15
Still trying to get the webcam to work :(

---

### Post by Santaji on 2010-10-19
I tried this: [http://www.arakhne.org/ricoh/](http://www.arakhne.org/ricoh/) but it won't work.
It says to load it i have to type: "modprobe r5u870" in the terminal but when i do that it says "FATAL: Module r5u870 not found."

EDIT: I got it to work!

---

