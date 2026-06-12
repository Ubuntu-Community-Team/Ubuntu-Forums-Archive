---
title: "Cannot boot Karmic livecd in laptop"
date: 2009-10-31
forum: Hardware
---

### Post by gamewolf on 2009-10-31
I am trying to install Karmic on my gateway T-1628 Laptop. I burned a disc with the 64-bit version, but it gave me errors during the verify stage. It said that the size of the disc was smaller than the size of the image. Well I tried it and it didn't work. It would freeze at the boot menu.

But then I tried it in a different computer, and it worked fine. The second computer I tried is a desktop. I don't know why but the only way I can install Karmic is by running the netboot installer on my usb flashdrive. It works, but its slow and has to download everything.

What can I do to get it working? Thanks.

---

### Post by lrcaballero on 2009-10-31
Hi gamewolf,

It seems like a whole bunch of people are going through difficulties, just follow the threads and comments and see for your self, at this time I am just going to wait before I do the up-grade and/or clean install!!! I been having lots of problems to, I can't up-grade and when booting from live-cd it boots in normal mode and sends me directly to my desktop. Best thing to do is just hang in there and stay with 9.04 version wich for me it work very very fine!!!!

Good Luck

Luis

---

### Post by gamewolf on 2009-10-31
Man i'm not sure. I haven't tried 9.04 on this particular laptop. but I am pretty sure it won't work either. It seems like it has something to do with my hardware possibly. Even the alternative cd doesn't work. I may have to try the dvd instead.

---

### Post by unsungboxer on 2009-10-31
I had the same problem on my hp mini 311 using the 9.10 beta images.  Once the 9.10 official release came out, there was no more troubles.  Are you using the official release from just 2 days ago?

---

### Post by gamewolf on 2009-10-31
Yes I am using the official 9.10 cd. I don't understand how the livecd can run in one computer and not another...

---

### Post by Efros on 2009-10-31
Tried to boot 32 bit Karmic desktop on this Lenovo Y550 Ideapad, despite using just about every combination of command line entries I can think of it will not successfully boot the Ubuntu Desktop from CD, I can hear the drumbeat and I'm sure the system is making it to the desktop but the LCD screen displays nothing. Looks as if I'll have to bite the bullet and install the alternate disk, before I see if everything has drivers.

---

### Post by gamewolf on 2009-10-31
> **Efros said:**
> Tried to boot 32 bit Karmic desktop on this Lenovo Y550 Ideapad, despite using just about every combination of command line entries I can think of it will not successfully boot the Ubuntu Desktop from CD, I can hear the drumbeat and I'm sure the system is making it to the desktop but the LCD screen displays nothing. Looks as if I'll have to bite the bullet and install the alternate disk, before I see if everything has drivers.

I know how that goes too :/ Ubuntu is just a good Linux Distro but its just so buggy at times. At least your somewhat getting the the desktop. I can't get back the boot menu...

---

### Post by gamewolf on 2009-10-31
any other ideas?

---

### Post by Efros on 2009-11-05
I have a spare 2.5" HD and I'm going to install this in my Y550, I have a USB version of karmic LiveCD and I'm going to try that, failing the live route I'll make an alternate USB installer and try that failing that... who knows!


Update: after various attempts with 9.10 images and Unetbootin, managed to get to a Live desktop using a flash drive Unetbootined with a copy of Ubuntu 32 bit 9.04 Desktop, following the procedure on this website.

[http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/) 

Everything (wireless/USB/Webcam etc) appears to work although the touchpad appears to be jumpy as hell.

Anyway plan to install the spare 2.5" drive tomorrow and install ubuntu 9.04 to it, and follow this with a distribution upgrade. Will update on the efficacy of this route.

---

### Post by Efros on 2009-11-06
Update:

Y550 Ideapad with intel series 4 graphics.

Booted and installed 9.04 32 bit desktop from USB flash, installation was smooth and fast. Once at the desktop I started a distribution upgrade to 9.10 32 bit. Installation took a while, eventually rebooted to a dark screen, rebooted and entered Grub menu. Two 9.10 kernels displayed, booted the older of the two and successfully got to a working Ubuntu installation, with a catch, slower than a very slow thing. Hardwarewise everything appeared to be working apart from the general sluggishness. I think I'm going to let this release mature a bit longer before I try again.

---

### Post by treesurf on 2009-11-13
I had this same problem on my Y550.  For the solution see this thread:

[http://ubuntuforums.org/showthread.php?p=8284770#post8284770](http://ubuntuforums.org/showthread.php?p=8284770#post8284770)

---

### Post by Efros on 2010-03-19
Just installed the 10.04 Beta faultlessly, well ok I had to add the wireless drivers from the hardware list, but everything else is just working, including compiz-fusion, bluetooth, audio, camera etc. Gurrreat!

:p:popcorn:

---

