---
title: "Samsung NC110 Touchpad issues"
date: 2011-05-31
forum: Hardware
---

### Post by tempmike on 2011-05-31
I just got the Samsung NC110 netbook and had to quickly replace 7 Starter with Natty.

Only real problem I'm having is with the touchpad. The "mouse" systems settings doesn't include a tab for trackpad (like I've seen on some guides) and I was hoping to disable the tap-to-click option (even better if I can adjust the sensitivity)

Additionally I have none of the multitouch options like two finger scrolling.

Thanks for any help.

amazon link:
[http://www.amazon.com/Samsung-NC110-A01-10-1-Inch-Netbook-Gloss/dp/B004HIN828/ref=sr_1_1?s=electronics&ie=UTF8&qid=1306888689&sr=1-1](http://www.amazon.com/Samsung-NC110-A01-10-1-Inch-Netbook-Gloss/dp/B004HIN828/ref=sr_1_1?s=electronics&ie=UTF8&qid=1306888689&sr=1-1)

---

### Post by Findecanor on 2011-07-20
I also got a NC110, have spent hours looking for info on how to do it, and I am still stumped.
I am afraid that there is no kernel driver for it (yet). Until someone writes one, it will only be recognized as a PS/2 device.

You can disable the touchpad completely in the BIOS if you don't need it or are using an external mouse. This is what I am going to do.

---

### Post by jonny_bowes on 2011-07-27
Hey guys

I have just got a Samsung NF110 and have installed 10.04 Remix and also have issues with the touchpad. It will track and register clicks but the side scrolls dont work.

This [site/thread]("http://www.voria.org/forum/viewtopic.php?f=4&t=694&p=5224#p5224") has good info but hasnt worked for me.

---

### Post by mjjw on 2011-11-05
Well I just got my Samsung NC110 and had the same urge to replace WIndows 7 with Ubuntu :) I chose Natty and had the same problem with the touchpad not being recognised. So I tried Oneiric, and the touchpad worked (hurrah!) however I could not get xrandr --scale to work properly, so I wanted to go back to Natty. After trawling the internet and not having much success in fixing the problem, I did learn enough to know that the cause was a buggy psmouse driver which was not recognising the elantech mousepad and was treating it as a logitech mouse.

So, to cut a long story short I (eventually) solved my problem by installing the Oneiric kernel into Natty. If you are trying to stick with Natty (Oneiric seems buggy to me at the moment) and want to get your touchpad working on a Samsung NC110 (mine is Samsung NC110-A03) then here's what to do:

Step 1: Install natty, note that touchpad settings are not available in System Settings.
Step 2: Create a Oneiric bootable cd / usb / partition. I still had Windows 7 on my PC at this point, so I installed it using Wubi
Step 3: Boot Oneiric and open a terminal.
Step 4: type the following into the terminal:
mkdir ~/Kernel-3.0.0-13
cd ~/Kernel-3.0.0-13
sudo apt-get download linux-headers-3.0.0-13 linux-headers-3.0.0-13-generic linux-image-3.0.0-13-generic
(I have no idea if sudo is necessary buy I am in the habit of always sudo for apt-get and that is what I did).
This will download 3 files onto your machine and should only take a few minutes assuming you have reasonably fast internet.
Step 5: Open your home folder and copy Kernel-3.0.0-13 to a USB stick (or directly to your Natty partition if you know how to use the mount command)
Step 6: Reboot into Natty
Step 7: Copy the folder off the USB stick and into your home folder
Step 8: Open a terminal and type the following:
cd ~/Kernel-3.0.0-13
sudo dpkg -i linux-headers-3.0.0-13_3.0.0-13.22_all.deb linux-headers-3.0.0-13-generic_3.0.0-13.22_i386.deb linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb
Step 9: Reboot, your boot menu should display kernel 3.0.0-13
Step 10: Enjoy a working touchpad :)

---

