---
title: "Dell Latitude D380 sound experiance"
date: 2007-11-22
forum: Hardware &amp; Laptops
---

### Post by prock on 2007-11-22
[SIZE="5"]Dell Latitude D380
My Installation experience.  
OS gutsy/ubuntu-7.10-desktop-amd64.iso
Duo Core 2  T7300, 2.0, 4MB
RAM 2 GB
Audio: SIGMATEL STAC 9205 C-Major HD Audio
Video: nVidia Corporation Quadro NVS 135M 128 MB
Wireless: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
Had some trouble booting from CD, Choosing the safe graphics option at the Ubuntu boot screen fixed this.
On boot the Restricted Driver Manager immediately found the proper  nVidia driver.  It worked fine.  In addition my wireless setup went flawlessly.   There was no sound.  I then installed.   I do not recall if I had to reset my video driver on reboot or not.  The sound problem was difficult but I found the answer [here]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller").  [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
“Method G” did the trick. :guitar:
What threw me was the Intel_HD thing because I don't have a Intel sound card but now both INTEL and SIGMATEL STAC 9205 show up in Gstreamer  volume applet and other sound related areas.  I had done a few things  prior to this that didn't work including reload the same ALSA packages.  This  didn't fix it.  I had to reload some other things in the process that disappeared.  I wish I knew more about command line stuff.    This setup is now a keeper and serving my needs well.[/SIZE]

---

