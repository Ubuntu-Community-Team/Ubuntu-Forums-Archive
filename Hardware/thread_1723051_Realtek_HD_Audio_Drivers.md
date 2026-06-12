---
title: "Realtek HD Audio Drivers"
date: 2011-04-06
forum: Hardware
---

### Post by apric0t on 2011-04-06
I am running Ubuntu 10.10 on an Acer 5739G, I am very new to linux, started using it in college for some basic networking and thought I might as well set it up on this old thing to see if I can learn the ropes.

Having a lot of difficulty understanding ALSA, I have uninstalled it, reinstalled it, and installed official linux Realtek HD audio drivers, but whilst before it said I had Intel HD Audio, now it does not detect any devices, so I have absolutely no idea where to start and would appreciate any help offered!

---

### Post by lidex on 2011-04-06
Sounds like a botched driver install. Re-install alsa via this method.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

Now use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by apric0t on 2011-04-07
Thanks for the quick reply, sorry I didn't respond sooner I gave up out of frustration and didn't expect such a quick reply.

The output is; [here.]("http://www.alsa-project.org/db/?f=1777774601d4b50aa62e314eca1d2a7e392f6a54")

Cheers.


EDIT: Alsamixer now working, but still not getting any sound, devices detected are Intel and Nvidia HD Audio, i think i might have done what you instructed in the wrong order so i compiled another report thing, [here]("http://www.alsa-project.org/db/?f=5c76086e81fe2eedf8c47b4494da0786608cf211").

---

### Post by apric0t on 2011-04-07
Everything is ok now. Thanks for your help everything is working fine now!

---

### Post by mahenkpatel on 2011-04-07
I Am also facing similar issue with my Asus laptop, only difference is that my mic is working fine but not getting any sound from speaker or headphone.

Tried nearly everything i could find in this forum still no luck, if any body can help please have a look at this thread

[http://ubuntuforums.org/showthread.php?t=1722623](http://ubuntuforums.org/showthread.php?t=1722623)

---

### Post by Clawbsy on 2012-09-27
I'm having the same issue. No matter what I do, the system doesn't see my devices. ALSA and Pulse can see it just fine, but the menu in the system doesn't show anything and there is no sound. I had ALSA dump a report.
[http://www.alsa-project.org/db/?f=fb21976f4355a7703f0a7a7bcc880cc21226b60f](http://www.alsa-project.org/db/?f=fb21976f4355a7703f0a7a7bcc880cc21226b60f)

---

### Post by android4682 on 2013-06-24
> **lidex said:**
> Sounds like a botched driver install. Re-install alsa via this method.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

Now use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

@lidex Thanks! That worked for me too :D

---

### Post by a_isse on 2013-12-06
> **lidex said:**
> Sounds like a botched driver install. Re-install alsa via this method.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

Now use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.



i tried all of that but for some reason my laptop still doesnt respond to m headphones, the sound only comes from the laptop speakers.

i have an meenee MNW737 ubuntu 12.04

here is the link to the alsa report please have a look and see what i could do,, im so frustrated and really need some help.

thank you

 [http://www.alsa-project.org/db/?f=8d89fc7af0ed6b1ed7d16e9833e33b1326fad1df](http://www.alsa-project.org/db/?f=8d89fc7af0ed6b1ed7d16e9833e33b1326fad1df)

---

### Post by Bucky Ball on 2013-12-06
Please mark thread as solved and a note: 10.10 is no longer supported and hasn't been for a year and a half. It gets no security updates and is therefore vulnerable. I would upgrade to a supported release.

All other posters looking for support: post new threads rather than hijicking this one. OP has SOLVED their problem and yours aren't exactly the same or they would be fixed too. Thanks.

---

### Post by periclesc on 2013-12-09
I was having trouble using 5.1 channels
this solved for me
[http://www.youtube.com/watch?v=eeOuseUqe9Y](http://www.youtube.com/watch?v=eeOuseUqe9Y)

---

