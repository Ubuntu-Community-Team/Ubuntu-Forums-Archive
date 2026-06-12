---
title: "Ubunto Mini PC suggestion"
date: 2017-07-25
forum: Hardware
---

### Post by hijoshua on 2017-07-25
Hello Guys,

Would like to get some feedback regarding what low power mini PC/Board (looking for under $150 usd, lower, better)I can install Ubuntu 16.04 LTS as 24/7 Server?
May run some python scripts for user interaction.
Your suggestion will be really appreciated.

Thanks

---

### Post by vocx on 2017-07-25
> **hijoshua said:**
> Hello Guys,

Would like to get some feedback regarding what low power mini PC/Board (looking for under $150 usd, lower, better)I can install Ubuntu 16.04 LTS as 24/7 Server?
May run some python scripts for user interaction.
Your suggestion will be really appreciated.

Thanks
I don't know what you would consider a mini PC. I read about the Meerkat computer from System76, which has a very small footprint but it seems it can be configured to be quite powerful. It's probably more than what you need, starting around USD 500. [https://system76.com/desktops/meerkat](https://system76.com/desktops/meerkat)

On the other hand there's the Raspberry Pi. The board itself costs USD 35. If you additionally buy power supply, case, SD card, keyboard, mouse, touchscreen, etc., it may be around USD 120. The only hard drive it has is the SD card, so you should use a 32 GB or 64 GB SD card for better results. The operating system itself should take less than 5 GB. Its official distribution is Raspbian, which is based on Debian. I'd say it behaves pretty similar to Ubuntu, and you should be able to install the actual Ubuntu, if you really need to.

The Raspberry runs with an ARMv7 CPU, so it is a low power CPU similar to the ones in mobile phones. It is not an x86_64 CPU as with most desktop and laptop computers, so it would not be possible to install the regularly available Ubuntu images. You would need to use a specific ARM version of Ubuntu, which I don't think would be an LTS. The CPU is not extremely powerful but it is enough for simple tasks, and certainly running scripts periodically should be no problem. You can install most Linux programs as well, precompiled for ARM, including Mathematica, Python, LibreOffice, etc. What do you intend to do with your server? You can connect it to a USB hard drive so you never run out of space for storing your personal files, and sharing them should be simple. I use my Raspberry Pi as a security video camera. It takes pictures, it creates videos, and after a while I manually move the pictures and videos to another drive with more storage.
[https://www.raspberrypi.org/products/raspberry-pi-3-model-b/](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/)

---

### Post by QIII on 2017-07-25
Hello!

"Server" is a bit vague.  What sort of server?  What is your intended purpose for it?

---

