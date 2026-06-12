---
title: "Ubuntu 8.04 Toshiba Satellite Built In Mic Not Working"
date: 2008-09-28
forum: Hardware
---

### Post by Jarrkemaar on 2008-09-28
Hey everyone. I have recently acquired a Toshiba Satellite L300 laptop, and have almost everything working. However, my sister is wanting to use this laptop for voice chat and I am having trouble making the built in microphone work. I have already tried turning up the volume settings for the microphone, but to no avail. Are there drivers for microphones that I don't know about? If you could help that would be fantastic.

---

### Post by daka on 2008-10-21
I also have Mic problems and mixer problems with alsa.  Please let me know if you have had any luck with this BIG problem with this laptop?

daka

---

### Post by rapachooie on 2009-02-23
+1 on the request for help fixing. 

On 8.10 and same problem.

---

### Post by kill_u on 2009-02-27
One from me if you find a solution of this problem. I have tried many times without successes.

---

### Post by rapachooie on 2009-02-27
not useful, but I somehow have a working microphone input on the front port (though I had to adjust the levels to get it working) but its perfect now, just requires a plug in microphone.

Not ideal, but something.

---

### Post by kill_u on 2009-02-28
Unfortunately I have tried to plug this kind of device in front port and also didn't worked.

---

### Post by fumphco on 2009-03-18
I managed to get both the internal and external microphone working on my Toshiba U405 under Ubuntu 8.10 by disabling the alsa drivers and installing OSS4.1 instead. I used the Linux 2.6 (x86) (TAR) drivers at [http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi) and followed their build and installation instructions. After installing OSS, and configuring the sound with the provided mixer, ossxmix, I was subsequently able to reconfigure most of the applications to use the OSS drivers. To make Skype work, I had to uninstall the skype package and instead installed the skype-oss-static package. Even though I now have a working configuration, I am hoping that this problem will eventually be fixed in the ubuntu distribution.

---

### Post by rapachooie on 2009-03-20
Excellent info! Thanks for that.

I have actually now put on Linux Mint 6 which I am sure you know is Ubuntu 8.10 based...

This has solved my problem 100%.

I am not sure if I changed the exact same settings on Ubuntu 8.10 but all I had to do with Linux Mint is double click on the sound icon in the tray, up the Front Mic settings and possibly change the source and up those as well (I will have to investigate exactly what I did and cant right now but will on request).

In any case, I now have skype working 100% just as on Windows, which is now used purely for gaming.

I will be trying out 9.04 on its release because as nice as Linux Mint is, I like having something that feels a bit better supported, even if it is practically the same.

Loving Linux though!

---

