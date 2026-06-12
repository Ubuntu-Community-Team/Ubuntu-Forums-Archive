---
title: "MP3 Player Inaccessible"
date: 2005-12-25
forum: Hardware &amp; Laptops
---

### Post by Unit #134679 on 2005-12-25
I receive a "No jukeboxes found on USB bus" when I connect my Nomad MP3 player and kick start Gnomad. When I try with Neutrino and scan for jukeboxes nothing happens. I didnt have this problem in the post. I tried following a HOWTO on the forum, but I ran into even more problems (no GNU C++ Complier, no GCC, and unable to read USB headerfiles, etc.) I *need* to have this running before tomorrow. Thanks

---

### Post by kaamos on 2005-12-25
[QUOTE=Unit #134679](no GNU C++ Complier, no GCC, and unable to read USB headerfiles, etc.) I *need* to have this running before tomorrow. Thanks[/QUOTE]

Just a quick guess, have you done```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

---

### Post by Unit #134679 on 2005-12-25
Apparently not. I never had this problem before...missing GCC and what not. After I install what is needed to be installed, what would be next?

---

### Post by Unit #134679 on 2005-12-25
Oh yea, when I follow the HOWTO on the forum, I get this error now:

configure: error: I can't find the libusb header file on your system. You may
        need to set the CPPFLAGS environment variable to include the
        search path where you have libusb installed before running
        configure (e.g. setenv CPPFLAGS=-I/usr/local/include)

---

### Post by kaamos on 2005-12-25
Try
```
sudo apt-get install libusb-dev libusb++-dev
```

---

### Post by Unit #134679 on 2005-12-25
I did that and followed the rest of the HOWTO. It worked correctly, but when I rescaned for jukeboxes, it still did not find any

---

### Post by wushumofo on 2005-12-28
[QUOTE=kaamos]Try
```
sudo apt-get install libusb-dev libusb++-dev
```[/QUOTE]


ooo! this worked for me, thank you!

---

