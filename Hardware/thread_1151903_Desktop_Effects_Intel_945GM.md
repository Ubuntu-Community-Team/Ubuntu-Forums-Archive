---
title: "Desktop Effects Intel 945GM"
date: 2009-05-07
forum: Hardware
---

### Post by Ben Leedham on 2009-05-07
Hi,

 When I first installed Ubuntu 8.10 on my Dell Latitude D820 the desktop effects worked. 

At some point, after an update I am assuming, they stopped working. I updated to Jaunty when it came out and have had to do some driver rollback and configuration ( specifying XAA in my xorg.conf ) to get the scrolling of text files and firefox to be smooth again. Still unable to enable the effects.

The odd thing is, I have also installed Jaunty as a Live instance with persistence on a USB drive, if I insert that into my Dell Latitude D820 and boot from it into a Live session I can enable desktop effects and have nice wobbly windows again.

Can anyone suggest what the difference would be?

Cheers.

---

### Post by mikewhatever on 2009-05-07
Could be a clean install versus an upgrade.

---

### Post by Ben Leedham on 2009-05-07
thanks mikewhatever, what is the difference there though? Is it that my drivers wouldn't automatically get upgraded with an upgrade or my xorg.conf won't be touched?

The fresh install everything works fine?

---

### Post by gooligan on 2009-05-07
I have a Dell E1705 with the Intel 945GM chipset and compiz works well for me.
My settings are in the following thread. Hope that helps
[http://ubuntuforums.org/showthread.php?t=1147488](http://ubuntuforums.org/showthread.php?t=1147488)

---

### Post by gooligan on 2009-05-07
Oops... sorry, here is the right thread:
[http://ubuntuforums.org/showthread.php?t=1146466](http://ubuntuforums.org/showthread.php?t=1146466)

---

### Post by mikewhatever on 2009-05-07
> **Ben Leedham said:**
> thanks mikewhatever, what is the difference there though? Is it that my drivers wouldn't automatically get upgraded with an upgrade or my xorg.conf won't be touched?

The fresh install everything works fine?

I am not sure really. It would be interesting to compare the xorg.conf files from both.

---

### Post by Ben Leedham on 2009-05-08
Thanks guys.

I tried your settings, but it didn't work for me unfortunately.

Eventually I followed a guide I found in the general sticky:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Although I used the rc4 kernel and libdrm2_2.4.9-2_i386.deb libdrm-intel1_2.4.9-2_i386.deb with the same intel driver as specified in the guide.

Finally I have wobbly windows again.

Thanks for the help.

---

