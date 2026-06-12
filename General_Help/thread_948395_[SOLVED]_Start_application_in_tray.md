---
title: "[SOLVED] Start application in tray"
date: 2008-10-15
forum: General Help
---

### Post by Tryfon on 2008-10-15
I was wondering if there is a way to configure any application to start in tray when I start it.
For example I have JDownloader and I'd like it to start in tray and go back there when I minimize its window.

---

### Post by Aero-Z on 2008-10-15
> **Tryfon said:**
> I was wondering if there is a way to configure any application to start in tray when I start it.
For example I have JDownloader and I'd like it to start in tray and go back there when I minimize its window.
Try:
```
sudo apt-get install alltray
```
I'm not sure cause I haven't used it myself, but to start application in tray try:
```
alltray APPCOMMAND
```
APPCOMMAND should be for example firefox or deluge or what ever.

---

### Post by Tryfon on 2008-10-15
Thanks a million!

---

