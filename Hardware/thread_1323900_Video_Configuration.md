---
title: "Video Configuration"
date: 2009-11-12
forum: Hardware
---

### Post by tcosson on 2009-11-12
I'm currently running xubuntu 9.04 on a really old laptop (Gateway Solo 9100) and I can't seem to get the video to go to 1024x768. I've tried several distributions and Knoppix boots right up into 1024x768 but none of the ubuntu versions will go there after the install. I was wondering if there was some way to copy the knoppix settings to xubuntu and make it work at the higher resolution.

or alternatively can someone walk me through a manual config.
I've tried sudo dpkg-reconfigure xserver-xorg and that did nothing for me.

---

### Post by tcosson on 2009-11-13
Nevermind - 
Turns out the solo9100 I have has different video than all the example configurations I found. Adding trident in the xorg.conf file and some modelines corrected the issue.

---

