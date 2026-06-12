---
title: "The Dreaded Webcam Drivers...."
date: 2009-04-04
forum: Hardware
---

### Post by Jackofwack on 2009-04-04
right, well you guys probably get this asked of you a lot but what driver would I have to use for a Microsoft web cam. It's model is the VX-1000 and Id 045e:00f7.

Whole Iusb for webcam: Bus 001 Device 002: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000.

I'm a noob to Linux and Ubuntu so help would be accepted gratefully!

(running Ubuntu 8.10) 

Thanks. Jack.

---

### Post by Jackofwack on 2009-04-04
Not that i'm being fussy or demmanding but this is my second post out of two in this forum and iv'e had no replies to any of them... why don't you like me?

---

### Post by Jackofwack on 2009-04-04
Jesus christ sure someone can help me?

---

### Post by bcschmerker on 2009-04-04
> **Jackofwack said:**
> right, well you guys probably get this asked of you a lot but what driver would I have to use for a Microsoft web cam. It's model is the VX-1000 and Id 045e:00f7.

Whole Iusb for webcam: Bus 001 Device 002: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000.

I'm a noob to Linux and Ubuntu so help would be accepted gratefully!

(running Ubuntu 8.10) 

Thanks. Jack.Ye picked a difficult one indeed!  Unfortunately, Microsoft Corporation hasn't provided the open-source community with the information necessary to determine what driver would be appropriate, a problem that I myself stumbled upon with an Emprex G40 webcam for USB 1.1 (iPassion iP2936 CCD, still unsupported to my knowledge despite manufacturer claims).  Creative Labs and Logitech are both reasonably well-supported between five drivers by CCD: gSPCA, OV511, OV51x-JPEG, SPCA5xx, and qce-ga (in addition to Modules for Kernels 2.6.28-up as planned for Ubuntu 9.04); both have webpages on their respective sites about the extent of support by hardware product.

(I'm currently awaiting help on a fix for the gSPCA-Source package, which is not compiling for me due to deprecated variables in at least one C sourcefile in addition to a deprecated Makefile in need of update to dovetail into the 2.6.24 Headers in Ubuntu 8.04-LTS; not all maintainers in the Universe category stay up to speed with Kernel changes.)

---

### Post by TyrantWave on 2009-04-04
This is what I did, worked for me, although no sound:
(No one has gotten sound working with the VX- series)

> **jesterthejedi said:**
> Working after 6 months of waiting and searching forums. My cam is the dreaded Microsoft VX-1000.

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file (top of page little text link called bz2)
extract archive (you can extract with nautilus)
in terminal "cd /Desktop/gspca" + <TAB> or exact name <ENTER>
in terminal type "make" no quotes takes about 5 mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue Hardy mess.
not working in Camorama, Camstream, errors in gqcam

installed xawtv, luvcview, and removed camserv.

I am so happy that I should pinch myself. I bought this webcam in June for my birthday and it was always a pain in the butt to solve. Success at last!

One thing they didn't say which I've noticed: When the computer is turned on, you need the webcam plugged in. If you plug it in after, it doesn't work all the time. Having it plugged in before turning the laptop/computer on seems to fix this. (Cam will get detected as /dev/video0, which is what you want)

---

### Post by stanca on 2009-10-07
Or:
```
sudo apt-get install subversion build-essential linux-headers-$(uname -r) && wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 && tar xf tip.tar.bz2 && cd gspca-* && make && sudo make install && sudo depmod -ae $(uname -r)
```

---

### Post by imblack on 2009-10-14
Than info was very helpful but on latest karmic the gspca module is not build able. :( 

I have also heard that after Ubuntu 8.10 the gspca was merged in the kernel is that true? if so then why are we even trying to compile it?

Please shed some light.

Thanks

---

