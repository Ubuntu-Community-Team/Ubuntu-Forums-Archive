---
title: "Fujitsu-Siemens V3515 - After installing, Ubuntu will not start for the first time"
date: 2009-02-23
forum: Hardware
---

### Post by metalix on 2009-02-23
I managed to instal Ubuntu 8.10 fine eventually, after restarting the installer in low graphics mode.

However, after rebooting the computer and starting Ubuntu for the first time it reported an error, about the video driver not being found, and prompting me to configure it myself. Every option seems to revert back to this error, except if I modify the xorg.conf file.

Looking at the following page...

> [http://ohioloco.ubuntuforums.org/showthread.php?t=967198](http://ohioloco.ubuntuforums.org/showthread.php?t=967198)

...I tried changing the driver from "vesa" to "openchrome". Now, the Ubuntu will display a "spinning mouse" pointer, but crash there. The screen is a dark brown but is completely locked up. There is no way to change the file back. I have read somewhere that I can change it from the command prompt, but as far as I can see there is no way whatsoever of doing this.

Is there anyway to get this working. I have a driver for my display device that is supposed to work, but I can't even get into the operating system to do this.

My graphics hardware is: Via Chrome9. My laptop is: Fujitsu-Siemens AMILO Pro V3515.

I gave Ubuntu a go back when it was 7.04. I thought that it would be better now but it's actually worse. I like Ubuntu but it seems to suffer from the same problems as all other opensource stuff.

Thanks,

---

