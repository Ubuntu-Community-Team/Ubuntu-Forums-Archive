---
title: "Finger Print reader not detected Ubuntu 20.04 Asus X409FJ"
date: 2020-07-28
forum: Hardware
---

### Post by zuenda25 on 2020-07-28
I have instaled ubuntu 20.04  with my device Asus X409 but my fingerprint reader not detected

---

### Post by collisiondomain on 2020-07-29
You might need to install the appropriate fprint drivers, if your device is supported.

As noted [https://unix.stackexchange.com/questions/396499/fingerprint-reader-on-asus-zenbook]([URL="http://[URL")]here[/url], try running this command in a command line:

```
lsusb
```

Then check to see if the code for your fingerprint reader is [https://fprint.freedesktop.org/supported-devices.html]([URL="http://[URL")]on the list of supported devices[/url].

---

