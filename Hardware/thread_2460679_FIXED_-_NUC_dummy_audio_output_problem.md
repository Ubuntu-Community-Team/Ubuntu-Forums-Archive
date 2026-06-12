---
title: "FIXED - NUC dummy audio output problem"
date: 2021-04-15
forum: Hardware
---

### Post by doug23 on 2021-04-15
I installed 20.04 - April14, 2021 on a NUC and had no headphone output sound. I was driving a set of speakers. I confirmed this with actual headphones plugged in. I researched the web for a fix and there are plenty of suggestions out there for many different versions. Here is what fixed it for me as given in one suggestion. 

Edit-   /etc/modprobe.d/alsa-base.conf    -and add this line -

options snd-hda-intel model=dell-headset-multi

Reboot and you should see the analog headphone audio show up rather than the dummy sound and you should have sound.

You can test this in preview but of course it will have to be put back in after the final install.

This also worked when I reinstalled and went to 20.04 Ubuntu Mate

I have no idea if HDMI audio works as I have no need for it but I suspect it would also need an options line to be able to be selected.

I hope this is of help to NUC users.

---

