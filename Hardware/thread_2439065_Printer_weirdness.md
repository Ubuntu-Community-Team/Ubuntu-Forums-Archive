---
title: "Printer weirdness"
date: 2020-03-22
forum: Hardware
---

### Post by 0+-. on 2020-03-22
Whenever I plug a USB stick into my computer, or whenever I boot my computer, my wireless printer (Epson WF-7515) starts noisily moving the print head for a few seconds, and then again a minute later. Is there any way to stop this? If not, what's the best way to disable access to printers so that it can conveniently be re-enable later when needed? In Kubuntu 19.10 I have removed the printer in the settings and it says "No printers have been configured or discovered" but the problem still occurs. This happens on various Ubuntu flavours/versions.

---

### Post by HermanAB on 2020-03-23
It sounds to me like a Wake-On-LAN setting in the printer is a bit bonkers.  Try to turn it off - or probably easier, turn the printer off when you are not using it... :)

---

### Post by slickymaster on 2020-03-23
*Thread moved to **Hardware**.*

---

### Post by 0+-. on 2020-03-29
I couldn't find any settings on my printer for wake-on-lan. I have now disabled cups with the following commands. This seems to stop the problem and I can just re-enable cups if I need to use the printer. :-\"
```
systemctl stop cups
systemctl stop cups-browsed
systemctl disable cups
systemctl disable cups-browsed
```

---

