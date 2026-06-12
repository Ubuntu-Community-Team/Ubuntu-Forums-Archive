---
title: "HP Compaq tc4400"
date: 2012-05-15
forum: Hardware
---

### Post by joshbrice on 2012-05-15
Ok I just bought this HP Compaq tc4400.  It has a fingerprint scanner on it but I cant find any way to use it.  Any ideas?

---

### Post by Enigmapond on 2012-05-15
You may need these:

```
sudo add-apt-repository ppa:fingerprint/fingerprint-gui && sudo apt-get update
```

Then:

```
sudo apt-get install libbsapi policykit-1-fingerprint-gui fingerprint-gui
```

When install (I assume you are running 12.04) The gui will be listed under system settings.

---

### Post by joshbrice on 2012-05-15
Ok thanks I will try that after updates. And yes im running 12.04

---

### Post by linuchsan on 2012-05-15
Maybe [https://launchpad.net/~fingerprint/+archive/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/fingerprint-gui)

---

### Post by Enigmapond on 2012-05-15
> **linuchsan said:**
> Maybe [https://launchpad.net/~fingerprint/+archive/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/fingerprint-gui)

That's what I just gave him... :)

---

### Post by joshbrice on 2012-05-15
Ok.  I installed it but I cant find  anywhere in the settings on where to configure it.

---

### Post by Enigmapond on 2012-05-15
Icon far right top panel/right click/system settings.Should be in that menu.

Go here and see what they say about it...
[https://launchpad.net/~fingerprint/+archive/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/fingerprint-gui)

---

### Post by joshbrice on 2012-05-15
Nope.  Dont see it.

---

### Post by Enigmapond on 2012-05-15
Then like I said, go to the PPA page and there are instructions on how to set it up without the use if the GUI...

---

### Post by joshbrice on 2012-05-15
Ok.  I found the gui.  It was with the applications.  It keeps crashing.  Any ideas?

---

### Post by linuchsan on 2012-05-15
Enigmapond: :-)

---

