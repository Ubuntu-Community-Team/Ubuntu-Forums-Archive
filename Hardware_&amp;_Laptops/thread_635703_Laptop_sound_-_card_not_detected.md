---
title: "Laptop sound - card not detected"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by ryantmer on 2007-12-09
I've read around a fair amount, and this does not seem to be a common problem. My laptop (an old twinhead slimnote VX) does not have any sound. In fact, the sound card is not even detected with
```
lspci -v
```
I used to have Ubuntu 7.10 running on this, and it worked fine. However, I gave on using the laptop for anything but as a jukebox (as it is fairly slow, but has a 40GB HDD). So, I decided to switch to Kubuntu to get amaroK (comes with LiveCD, so I don't have to muck about at all). However, as I said, no sound. Card is not listed anywhere. If I run
```
alsamixer
```
I end up with
```
alsamixer: function snd_ctrl_open failed for default: No such device
```
The sound is enabled in the BIOS, the system beep works, and the sound worked 100% on Ubuntu.

Any help is greatly appreciated :)

---

