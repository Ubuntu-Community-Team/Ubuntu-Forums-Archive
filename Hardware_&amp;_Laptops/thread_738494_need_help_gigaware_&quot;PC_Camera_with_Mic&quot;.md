---
title: "need help: gigaware &quot;PC Camera with Mic&quot;"
date: 2008-03-28
forum: Hardware &amp; Laptops
---

### Post by thebinaryblob on 2008-03-28
I got a Gigaware "1.3 Megapixel PC Camera with Mic" today, and when i plugged it in, even the microphone was not recognized :( . I have not been able to find any drivers (i tried gspca)  that will make it work and create the /dev/video0 device file all of the webcam applications look for. Everything that I find either points to offline websites ([http://www.kaiser-linux.li/]("http://www.kaiser-linux.li/")) or information that is out of date ([http://ubuntuforums.org/showthread.php?t=320290]("http://ubuntuforums.org/showthread.php?t=320290"), the drivers recommended dont work, and the last post was in May 2007 :( ) . The gspca drivers dont work. I've also tried searching for help using what appears to be the model number of the webcam, which is 25-234. That didnt work either.

lsusb gives:
```
Bus 005 Device 004: ID 0c45:628f Microdia 
```
I've tried searching for microdia drivers, but none of them work.

dmesg tells me:
```
[ 1767.843433] usb 5-6: new high speed USB device using ehci_hcd and address 5
[ 1767.978440] usb 5-6: configuration #1 chosen from 1 choice
[ 1767.981177] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1296: 5:2:1: cannot get freq at ep 0x84
[ 1769.367335] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1296: 5:2:1: cannot get freq at ep 0x84

```

Any help at all would be enourmously appreciated, but I fear that I may have to just wait for drivers that work with it, or try to make them myself (i don't even know where to start :confused: ).

---

### Post by linuxwizard on 2008-03-28
Microdia webcams drivers > [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

---

### Post by intel on 2008-05-02
Your webcam should be already supported by the following driver
[https://groups.google.com/group/microdia](https://groups.google.com/group/microdia)

---

