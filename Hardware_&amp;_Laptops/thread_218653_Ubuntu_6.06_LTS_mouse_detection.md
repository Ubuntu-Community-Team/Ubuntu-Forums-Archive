---
title: "Ubuntu 6.06 LTS mouse detection"
date: 2006-07-18
forum: Hardware &amp; Laptops
---

### Post by Toad1771 on 2006-07-18
Ubuntu 6.06 LTS is always detecting my PS/2 wheel mouse as a PS/2 IBM Trackpoint rather than a Generic PS/2 Wheel Mouse as Ubuntu 5 did (cat /proc/bus/input/devices).

When running xev, there are no events at all for wheel up or down, so the xorg.conf settings for ZAxisMapping seems does not matter.

So, needless to say, my mouse wheel does not work and I just assume it is because the device is being detected improperly as an IBM trackpoint (whatever that is).

Any ideas?

Thanks,
Toad

---

### Post by zxee on 2006-07-19
You could try to reconfigure your xorg. From a shell type 
'sudo dpkg-reconfigure xserver-xorg' That will give you a chance to choose the correct pointing device. Or you could edit your /etc/X11/xorg.conf file manually.

---

### Post by Toad1771 on 2006-07-20
I have tried both and neither matter because it is the physical device that is not being detected correctly by psmouse.

What I have determined is that after booting up, I can manually run rmmod psmouse and modprobe psmouse proto=exps (the proto is required for it to work) and then the mouse is detected correctly as a PS/2 wheel mouse and suddently buttons 4 (scroll up) and 5 (scroll down) work in xev and xorg works then too (the ZAxisMapping is already correct in xorg.conf).

So, the problem seems to be in the psmouse driver module. 

Note that if I add proto=exps to the psmouse line in the kernel modules file (/etc/modules) and reboot it still detects the mouse incorrectly. So, I am not sure why psmouse incorrectly detects the mouse at boot time versus when reloading it manually later. I have also noticed that /etc/modules does not have an entry for mousedev as does Ubuntu 5 - is this important? (I am not sure what mousedev actually is).

Thanks,
Toad

---

