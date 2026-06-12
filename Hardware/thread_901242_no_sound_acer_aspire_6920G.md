---
title: "no sound acer aspire 6920G"
date: 2008-08-26
forum: Hardware
---

### Post by Manoau2002 on 2008-08-26
I am running ubuntu 8.04 according to the sound properties i have a alc883 hda intel sound card. thanks.

---

### Post by Manoau2002 on 2008-08-26
I should have said realtek alc889.

This is what I have tried so far.

cat /proc/asound/card0/codec#* | grep Codec

then

sudo gedit /etc/modprobe.d/alsa-base

then I changed the last line to:

options snd-hda-intel model=acer-aspire


I also tried maxing the sound using alsamixer

I restarted my computer and still have no sound. Any help would be appreciated. Thanks.

---

### Post by lud3e on 2008-09-18
My sound is running fine with the new oss version.

At least stereo + microphone.

You need to get special versions of some programs though (Skype, flash,...).

See [https://bugs.launchpad.net/ubuntu/+bug/218165](https://bugs.launchpad.net/ubuntu/+bug/218165) for details

Anyone got alsa working yet??

---

