---
title: "Sound plays through both headphones and main speakers"
date: 2009-07-07
forum: Hardware
---

### Post by go7Ul1ai on 2009-07-07
Hello,
I am wanting to record and edit music on my laptop, but when I plug in my headphones in the standard jack port and play a sound, it plays through both the laptop speakers and the headphones, I've tried fiddling about with the volume preferences but to no avail.

Any ideas?

I have a Fujitsu Siemens Amilo li1818 laptop.

Lee Jarratt

---

### Post by go7Ul1ai on 2009-07-08
help please

---

### Post by Axx83 on 2009-07-08
Ok straight to the point.

Do this:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
ONLY part A (I suppose you're using jaunty) it seems long but it's very short.

Then this in a terminal
```
cat /proc/asound/card0/codec#* | grep Codec
```
write down the name of the card
search it here
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)
add it to the conf file
```
sudo gedit /etc/modprobe.d/alsa-base
```
write at the end of the file this
```
options snd-hda-intel model=MODEL
```
of course instead of MODEL write the name you find in the list I pointed above
for example
```
options snd-hda-intel model=fujitsu
```

and now try the headphone/speaker combination, of course be sure that nothing is muted using alsamixer
```
alsamixer
``` in a terminal

---

### Post by go7Ul1ai on 2009-07-21
Thank you, this worked after a bit of experimentation.

Lee

---

