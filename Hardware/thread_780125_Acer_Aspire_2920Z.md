---
title: "Acer Aspire 2920Z"
date: 2008-05-03
forum: Hardware
---

### Post by r4k11n on 2008-05-03
I couldn't get my speaker and mic jack, and the webcam to work. How do I enable them?

---

### Post by subzero316 on 2008-05-03
> **r4k11n said:**
> I couldn't get my speaker and mic jack, and the webcam to work. How do I enable them?




Webcam works with an app call 'CHEESE'..install that..also ur spk n mic jack anit workin????the one in the fromt?

---

### Post by Eirikizer on 2008-05-03
I had some problems with the sound on one of my machines a while ago, but I found a thread on the forums that helped me. Search for the name of your hardware on the forum, and you might find the solution. I know this isn't much help, but it's the best I can do.

---

### Post by r4k11n on 2008-05-03
@subzero: yerr, the two jacks in front. My speaker jack is plugged, but sounds still come out from the built-in ones.

@eirik: suggestion noted. :D

---

### Post by Zorael on 2008-05-03
As for sound not working, I had to edit **/etc/modprobe.d/alsa-base** and add the following line to the bottom.
```
options snd-hda-intel model=acer
```
This only applies to those with Intel HDA sound chipsets. Running 'lshw -C multimedia' in a terminal will list what you have.

Then do the following to apply changes. Alternatively, reboot.
```
$ sudo /etc/init.d/alsa-utils restart
```

---

### Post by r4k11n on 2008-05-03
Sound is working fine, but only through the built-in speakers. I just couldn't get the jacks to work.

---

### Post by r4k11n on 2008-05-04
Bump.

---

### Post by Zorael on 2008-05-04
Well, I only had sound through my left speaker, and it didn't autodetect whether there was a headphone connected, so at least it sounds fairly similar.

---

