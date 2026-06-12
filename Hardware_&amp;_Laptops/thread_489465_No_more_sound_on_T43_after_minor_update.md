---
title: "No more sound on T43 after minor update"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by Meister_Eder on 2007-07-01
Hey, about a month ago I updated some packages of Feisty. Today I recognized that there is no more sound. I tried different kernels (2.6.20-16, 2.6.2-15) with the same results. I had to mute headphone jack sense on Feisty to get sound before the update but now there is only the "regular" headphone switch. I believe the jackish one is gone.
All modules are loaded and the software pretends to play a song but there is no sound at all. 
I'd appreciate any suggestions.

---

### Post by Meister_Eder on 2007-07-02
Sound is back. Not sure what brought it back. I purged and installed alsa and the current kernel:

```

sudo apt-get --purge autoremove linux-sound-base alsa-base alsa-util
sudo apt-get install linux-sound-base alsa-base alsa-util

```


```

sudo apt-get --purge remove linux-image-generic
sudo apt-get install linux-image-generic

```

---

### Post by Meister_Eder on 2007-07-04
reboot - sound is gone, again! That's really annoying.

---

### Post by Meister_Eder on 2007-07-04
hmm, did the same thing as before (reinstalling alsa and kernel packages) but still no sound...

---

### Post by Zafrusteria on 2007-07-04
Hi 

I had :-) the same problem, I got it solved after reading the post " Comprehensive Sound Problem 7.04 "

I ran the alsamixer in a terminal and then while playing an mp3,  I played around with the volume and turned OFF the mute with the "m" key on the settings. I now have sound.

Hope that helps.

---

### Post by Meister_Eder on 2007-07-06
No, alsamixer is not the problem. It seems that I sometimes have sound after a reboot and sometimes I don't.

---

### Post by shizow on 2007-07-09
i have also a T43 and the kernel update broke my sound too
but the sound is still working with 2.6.20-15

---

