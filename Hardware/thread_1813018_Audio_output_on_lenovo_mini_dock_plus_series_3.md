---
title: "Audio output on lenovo mini dock plus series 3"
date: 2011-07-27
forum: Hardware
---

### Post by ocin on 2011-07-27
I have a lenovo thinkpad T520 docked to a mini dock plus series 3. I can't seem to get audio output to work on the 3.5mm jack on the dock. The jack on the laptop itself works fine. I only have one output device available in Sound preferences/Output and that is "Internal Audio Analog Stereo".

Am I missing something obvious here or is it a bug?

---

### Post by amdemas on 2011-09-20
I am having the same trouble but mine is a 420s 


Any have a solution?

---

### Post by amdemas on 2011-09-21
I did some hunting and found that when i added this line 


options snd-hda-intel model=thinkpad
to the /etc/modprobe.d/alsa-base file and even the /etc/modprobe.conf file.

Then reboot and dock it worked for me but your mileage may vary...hope this helps.

---

### Post by tatrabanka on 2012-05-09
thanks a lot mate!
that resolved this issue for me too!
btw:
1) modification of only "alsa-base.conf" file was enough
2) i couldn't find that "modprobe.conf"

---

### Post by oconnor663 on 2012-09-11
This worked for me too! Thanks! I also only needed to add the line to /etc/modprobe.d/alsa-base.conf. I'm on a Lenovo ThinkPad T420s.

---

