---
title: "Trouble installing from anything"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by RYjet911 on 2009-05-25
I'm trying to install the 9.04 version of Ubuntu Studio. I have downloaded the ISO from the proper website, yet every method I've tried simply does not work. I've wasted two DVDs and tried a USB install.

With the DVDs, I get an error of something like "Unable to mount disc image" (Will give more specific error when I next attempt it) then tells me (As the only possible reason) that I haven't put the CD in. Well no ****, I wouldn't have got to that stage without it!

Then with USB, it kept trying to use the DVD drive. Upon satisfying it by putting one in, I obtained the same error as above. I followed a guide online to get the USB installer working, and it did until it got past selecting my keyboard layout.

I've got really two questions
1) Can anyone help on getting the installer to recognise the own disc it is on?
2) How come the only download on the Ubuntu Studio site is for an "Alternative" installer?

---

### Post by merlinus on 2009-05-25
Have you done a checksum for your .iso to ensure the download is not corrupted?  Did you burn it as a disc image (not as a data disc), at a slow speed?

---

### Post by RYjet911 on 2009-05-25
I did burn it as a disc image, and I did it at a slow speed. Although I burnt standard ubuntu at max speed and everything on there works fine (And don't suggest upgrading to Studio through Ubuntu because it didn't work properly last time I tried, the very reason I'm installing through DVD)

I also have no idea what a checksum is or how to perform one.

---

### Post by merlinus on 2009-05-25
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by RYjet911 on 2009-05-25
The checksum is fine according to winMd5Sum

---

### Post by merlinus on 2009-05-25
Have you tried burning the .iso to a CD rather than a DVD?

---

### Post by RYjet911 on 2009-05-25
The ISO is 1.3 gigs, it won't fit on a CD

---

### Post by merlinus on 2009-05-25
OK.  Another suggestion is to install Ubuntu 9.04, and then add the other software that comes with Studio via Synaptic.  That .iso will fit on a CD.

---

### Post by albinootje on 2009-05-25
> **merlinus said:**
> OK.  Another suggestion is to install Ubuntu 9.04, and then add the other software that comes with Studio via Synaptic.  That .iso will fit on a CD.

Good plan, you can use this command for that after the Ubuntu installation :
```

sudo apt-get install ubuntustudio-desktop

```

---

### Post by RYjet911 on 2009-05-25
I'll give it a shot. Thanks for your help :)

---

