---
title: "auto-detection of samsung ml-1740 printer"
date: 2006-02-07
forum: Hardware &amp; Laptops
---

### Post by dhalgren on 2006-02-07
Hi. I hope this is the correct forum (my first post).

Recently, due to a catastropic power failure, I had to reinstall 5.10. Before this, the printer was auto-detected and ran perfectley. After reinstall and update, the printer fails to be detected, and none of the drivers chosen manually seem to work. The usb port is ok, and I have tested the printer on my wife's windows machine, so it's ok also.

I did try samsung's own drivers and installing their ppd file (I may nto have done this correctly, but I think I did) and this gave no joy.

Does anyone have any suggestions about this? Is it, e.g., a matter of re-installing some software, or something else?

Ok, I don't know what happened, but I sorted it out. something had interfered with ~/.ICEauthority. For some reason (I am not a hacker, so I don't know) this prevented it from being detected in device manager and in the add printer dialogue. It also prevented my logging in again.

Fix: console login (^MF1), delete ~/.ICEauthority, and reboot into home directory, and everything works fine. I don't understand, as I said, but that's the beauty of learning a few things, and keeping on learning where one can.

Cheers

---

