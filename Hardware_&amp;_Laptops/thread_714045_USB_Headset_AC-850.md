---
title: "USB Headset AC-850"
date: 2008-03-03
forum: Hardware &amp; Laptops
---

### Post by KLineD on 2008-03-03
Hello!

I recently bought a AC-850 USB headset. I got it USB because my mic input is not working with Ubuntu (HDA Intel). When I plug it in, dmesg gives the following output:

> [ 2127.960000] input: HID 0d8c:000c as /class/input/input8
[ 2127.960000] input: USB HID v1.00 Device [HID 0d8c:000c] on usb-0000:00:1d.0-2


But then I don't know how to proceed. If i play some music after I plug the headset, sound is still played through the laptop speakers and I tried to record some sound with audacity but it didn't listed any "USB device" as recording or playback source.

I looked [here]("http://www.qbik.ch/usb/devices/showdev.php?id=3511") and they say the device gets autodetected and configured, at least in the referenced site (radioshack device with same chipset, [listed here]("http://www.qbik.ch/usb/devices/showdev.php?id=3973")).

Maybe I don't know how to configure the device. I looked in alsamixer but it only list the laptop soundcard. Kmix is the same, no USB nothing. The headset works, I tested it with windows, although I had to set the recording and playback source manually.

Anything I could try to make this work? Thanks in advance!

---

### Post by KLineD on 2008-03-03
Ok I found the following thread: [http://ubuntuforums.org/showthread.php?t=224797](http://ubuntuforums.org/showthread.php?t=224797)

The solution seems to be editing alsa-base, selecting the USB device under System | preferences | sound and reboot. This are instructions for Gnome.

Anyone knows the equivalent for KDE? and is there a way to eliminate the reboot? that would be awesome.

---

