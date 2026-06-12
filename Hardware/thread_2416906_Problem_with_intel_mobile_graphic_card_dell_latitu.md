---
title: "Problem with intel mobile graphic card dell latitude"
date: 2019-04-17
forum: Hardware
---

### Post by zalle1 on 2019-04-17
Hi guys,

I installed Xubuntu on an old dell latitude d630, and it works fine, except the graphics card.

I start the pc, and it's all good, but after about a minute, the screen goes black. I checked the display, and it says the refresh rate is 76Hz, and resolution 1024X768.

The only way I can work with it is to start in recovery mode, and then it will boot without graphic card. It shows refresh rate 0Hz, resolution 1024X768. And all is fine, until I reboot it.

What can I do about it?

Thanks

---

### Post by mörgæs on 2019-04-17
Hi, welcome to the fora.

Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it to the command line, run it and post lshw.txt in CODE tags. It will tell us more about the hardware.

---

### Post by zalle1 on 2019-04-18
Thank you for your answer, but I'm going with Kubuntu, which is also giving me some headaches... :)

---

