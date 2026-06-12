---
title: "Drivers for Creative Sound Blaster 5.1 VX"
date: 2009-12-19
forum: Hardware
---

### Post by bhadresh_dahanuwala on 2009-12-19
Hi,

I have got Creative Sound Blaster 5.1 VX card on my PCI slot.

When I login to Ubuntu, I get some irritating sound (similar to old TV sound when you do not find any channel). When I play any music or movie, there is no sound.

The same works in Windows.

Please help me in searching drivers for my hardware OR to fix it.

Thanks & Regards,
Bhadresh

---

### Post by IcarusR on 2009-12-20
I had similar yesterday. Turned out the volume was muted.

---

### Post by bhadresh_dahanuwala on 2009-12-21
Hi,
 
That is not the case. I said I get annoying sound when I play any movie / music.
 
Regards,
 
Bhadresh

---

### Post by vynnie on 2010-02-25
I got the same problem too, when i play anything [ which use sound ] 
i got a { noizy,stratchy,anoying} sound like an old TV seeking for channels
Plz help here

Same Sound card [Creative] worked fine before on Win*

ubuntu 9.10 (x64)

---

### Post by bhadresh_dahanuwala on 2010-07-05
I have upgraded to Ubuntu 10.04 still crackling sound. Please help.

---

### Post by lidex on 2010-07-06
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by schnelle on 2010-12-15
Look at this link: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

" Not all features on all models supported. On the VX, white noise on playback unless initialized in Windows first."

---

