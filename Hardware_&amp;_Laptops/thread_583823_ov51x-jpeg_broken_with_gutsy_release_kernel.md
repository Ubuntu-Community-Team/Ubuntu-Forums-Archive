---
title: "ov51x-jpeg broken with gutsy release kernel"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by feld on 2007-10-20
I used to use ov51x-jpeg to use my eyetoy with Gutsy during the alpha/beta/RC/whatever. It worked fine until the very last kernel update before Gutsy was released. Now when I try to use my camera all I get is a very distorted image and I cannot figure out why.... doesn't make any sense at all.

Does anyone out there have any tips? Can anyone else test?

I'm on the amd64 release.

Thanks

---

### Post by Offoffoff on 2008-02-03
I have made like this:
1. I compiled driver
2. sudo apt-get install ov51x-jpeg-source
3. module-assistant a-i ov51x-jpeg (many mistakes, but who cares)
4. sudo mknod /dev/video2 c 81 2 (because I already have two video devices, I do not know why - Ubuntu don't want to make it automatically)
5.sudo chmod a+rw /dev/video2
6. plug camera to usb
7. sudo modprobe -f ov51x-jpeg
Camera works. But audio channel of camera catches audio hw1.0 where already tv-tuner sends sound, camera shifts hw1.0 to hw2.0. And sometimes, I did not get - when and why, system loose video2. And every time I need to use camera - I have to use:
sudo modprobe -f ov51x-jpeg

---

