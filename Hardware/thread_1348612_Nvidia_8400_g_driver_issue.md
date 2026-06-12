---
title: "Nvidia 8400 g driver issue"
date: 2009-12-07
forum: Hardware
---

### Post by sandy4linux on 2009-12-07
Hi,
 
  My laptop acer aspire has got ubuntu 9.10 with Nvidia. when it turns on LED 's for power, bluetooth, hardrive, DVD drive etc works, but the screen is blank. I have Nvidia driver 180 installed and it has mismatch with kernal version( found it when I checked in system logs)
  Its turns on normally sometime, when I cover my notebook with my blanket. It sounds funny..but it worked though. My Nvidia works on 100 mhz-129 mhz --- level 0, there are 3 performance level in Nvidia settings. How do I change this to level 1, where my system could be stable to boot up? 
 
how could I turn on my system now? Please give me a quick response..
 
Thank you

---

### Post by gradinaruvasile on 2009-12-07
Well if u have a mismatching kernel version its bad... You have to install the drivers again. Also the latest stable drivers are 190.42.

Do you have some light intensity detector on your laptop? If it is, can you turn it off from BIOS?

---

### Post by sandy4linux on 2009-12-07
My notebook is off right now. There is no light intensity detector. I couldnt find 190.42 driver update in hardware driver option. how do I upgrade it?
Thanks for the reply
Regards

---

### Post by gradinaruvasile on 2009-12-07
Dont play with the performance levels. Its a good thing for laptops. Lowering the speed the card cools more efficiently. If you force it to run with higher speed it may (yes, even if its not loaded) overheat and may be damaged.

And for the latest drivers:

Open a terminal (applications -> accessories -> terminal) and type:

sudo gedit /etc/apt/sources.list

Add to the end of the file the following line:

deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main

Save,quit. Then type:

sudo apt-get update && sudo apt-get install nvidia-glx-190 nvidia-190-libvdpau nvidia-190-modaliases 

You will get a GPG authentication error. Thats not a problem. Go to the PPA :

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

Click on "Technical details about this PPA" and click on "Whats this" - there is described how you can add the GPG key to your keyring in the "Telling Ubuntu how to authenticate the PPA" section - remember, the rest is done already.

Also that card of yours has the VDPAU feature, interesting if you want to watch HD (1080p) movies - it lowers the CPU usage to ~10% while decoding 1920x1080 resolution movies, MPEG-1, MPEG-2, VC-1/WMV9 and H.264 compressed.
 You have to install mplayer (also in this ppa - and only this version supports vdpau) if you want to take advantage of that.

---

### Post by gradinaruvasile on 2009-12-07
Ok, here it is a simpler GPG adding:
In a terminal type:

gpg --keyserver keyserver.ubuntu.com --recv cec06767
gpg --export --armor  cec06767 | sudo apt-key add -

Thats it.

---

### Post by sandy4linux on 2009-12-07
My notebook shows no bios at all. if I am lucky, it will turn on. Do u think its an issue with flashing bios? Sometime notebook starts up normally..

---

### Post by gradinaruvasile on 2009-12-07
Why, did you flash the bios?
Usually the bios keys are F2, Del (that is an older standard, but who knows), F1. Try pressing these keys (one at a time, hold it just when you are typing, not longer), you might get to your bios.

What model is exactly? Acer Aspire...? 

Also, if sometimes starts, sometimes not, it might be a problem with your RAM.
Select the memtest option from the boot menu. If its hard to get even to that one, boot from the live-cd and do a memory test - you h\ave option for that in the first menu - and let it do 1 full cycle (1 pass). If there are errors (shown in red, cant miss them) then you have a problem with your RAM.

---

### Post by sandy4linux on 2009-12-08
It turned on thrice when I flashed the bios, or may be it turned because the blanket was covered. Im confused now. 
It doesnt show bios, when I pressed F2 for a while, a long beep sound comes. I think there is no trouble with Ram, when I replaced with another 512 mb, doesnt work either.
 
But when I had vista, I tried the memory test, system turned off. I tried several times to run a memory test, didnt work though. Do u think its problem with my ram? But its turning on my bluetooth light itself, that means the booting process is working except detecting my display. Once I turn on I will update the Nvidia to 190.42.
 
acer aspire one 5520G
1 gb ram, 120 Hdd, 2.2 ghz 512 kb L2 cache
AMD turion 64 mobile technology

---

### Post by sandy4linux on 2009-12-11
Hey,

 I have updated the Nvidia to latest driver 190.42 and resolved the GPG authentication, as per the commands. In hardware driver  I have nvidia 190 and 173, still Im not able to turn my system off. 
Help me pls

---

