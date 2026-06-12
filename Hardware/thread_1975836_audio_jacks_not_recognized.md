---
title: "audio jacks not recognized"
date: 2012-05-07
forum: Hardware
---

### Post by majicklaughfter on 2012-05-07
Is there any way to get Ubuntu 12.04 to recognize my laptop audio jacks? 
I tried all the settings in the System>Sound panels 
But I can not get it to recognize my microphone jack or my headphone jack? 
Is there a way to update drivers if that might help?
Thanks in Advance!

---

### Post by Yellow Pasque on 2012-05-08
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by majicklaughfter on 2012-05-09
This is the info I got back....
[http://www.alsa-project.org/db/?f=35a8dd6bcb15f2042d41c0ec5282ef9c6f213f15](http://www.alsa-project.org/db/?f=35a8dd6bcb15f2042d41c0ec5282ef9c6f213f15)
what next?

---

### Post by Yellow Pasque on 2012-05-09
You could try adding this line to /etc/modprobe.d/alsa-base.conf :
```
options snd-hda-intel model=hp-dv5
```
Change won't take effect until you restart.

---

### Post by majicklaughfter on 2012-05-10
I don't understand where to add the code?

---

### Post by Yellow Pasque on 2012-05-10
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Add it to the end of the file.

---

