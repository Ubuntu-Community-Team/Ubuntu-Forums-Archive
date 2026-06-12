---
title: "Hooking up USB mouse"
date: 2004-12-20
forum: Hardware &amp; Laptops
---

### Post by malmjako on 2004-12-20
On my laptop, I want to be able to use an external USB mouse sometimes. My touchpad works great, but sometimes I prefer to work with a mouse. But attaching the mouse doesn't seem to be enough... Nothing happens when I try to use it. What do I need to do to get this to work? I want to be able to attach and detach the mouse at any time.

---

### Post by wulf on 2004-12-20
My laptop (Packard Bell Easynote M5262) works fine with my USB mouse (MS Optical Wheel Mouse). Of course, it is plugged in all the time, including when I boot up. Have you tried booting up with the mouse attached?

Wulf

---

### Post by malmjako on 2004-12-20
Yep, I've started up with the mouse attached, but it still doesn't work. The computer is a HP Omnibook 6000.

Is there some way I can check to see that USB actually works correct? When I hook up my digital camera, the following is added in /var/log/messages:
```
Dec 20 15:58:37 localhost kernel: usb 1-1: new full speed USB device using address 8
Dec 20 15:58:37 localhost kernel: usb 1-1: new full speed USB device using address 9
```
However, I also get the following with dmesg:
```
usb 1-1: new full speed USB device using address 8
usb 1-1: device not accepting address 8, error -71
usb 1-1: new full speed USB device using address 9
usb 1-1: device not accepting address 9, error -71
```
In Ubuntu on my iMac, I get /dev/sda and a dialog which asks me if I want to import photos, but nothing on my laptop... Could there be something wrong with USB? I bought the computer second hand just a week ago and haven't tried USB until now.

---

### Post by malmjako on 2004-12-20
Ok. USB works. I hooked up a keyboard and it worked straight away. (Still strange with the digital camera...)

---

### Post by wulf on 2004-12-20
How about taking a look at the Device Manager (in the System Configuration section of the Computer menu)? I was playing around with my camera (Fuji-Finepix 1400) on Saturday and could see when it was plugged in but didn't figure out how to access the pictures. What I'd really like to do is figure out how to access the built in card-reader but that's probably another thread when I've got time to follow it up  :D 

Wulf

---

### Post by malmjako on 2004-12-20
Thanks for your help, Wulf! The problem was mechanical. The USB port is old and it's actually possible to attach the cable the wrong way! Both mouse and camera work now. (However, if I attach them to a hub and then attach the hub to the port, only one works... It works fine if I first attach the hub and then the devices.)

---

