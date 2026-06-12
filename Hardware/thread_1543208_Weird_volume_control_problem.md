---
title: "Weird volume control problem"
date: 2010-07-31
forum: Hardware
---

### Post by Hellhound4 on 2010-07-31
Ok so I was streaming some videos and the audio started to cut out for several seconds at a time. Now all my audio will play for a little while then stop for several seconds then resume. To make the volume play correctly I have to constantly move the volume slider.

---

### Post by lidex on 2010-07-31
Try removing pulse config:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

