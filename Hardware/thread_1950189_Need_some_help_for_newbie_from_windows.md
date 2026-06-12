---
title: "Need some help for newbie from windows"
date: 2012-03-31
forum: Hardware
---

### Post by chemical349 on 2012-03-31
hi all, 
i am a win users for over 10 years. 
i have decide to start to use ubuntu with one of my old motherboard.
intel d915gav
4g ram
2T Disk

as i try both 12.04 & 11.1 of ubuntu. when i was trying with 12.04 , i had sound while i was doing the installation. i have access to a web radio via the sound button. however, after i complete the installation the same online radio became silence. i try all of the "Hardware" in "Sound" but with no luck. 

later on, the system keep crashing, so i have decide to change back to 11.1.

but i get no sound during the installation like 12.04 and no sound after complete installation.

also, i only get resolution 1024x768. 

As i am very new to ubuntu ( and i sware , i spend 4 horus online already but with no luck in google to have any workable solutions.

can someone point me a right direction or shred me some light? i don't want to give up this easy and i hope i can get some assist here.

million thanks. and wish you all have a good weekend. 

V.

---

### Post by theknightlinux on 2012-03-31
Nice old motherboard... Ubuntu 12.04 LTS has not been released yet, you might have installed the beta version. I believe the stable version will be release by April 26. If you went back to Ubuntu 11.10, try this and lets see if it works. Open a terminal Ctrl-Alt-T at the same time. And type in the following order:

 **sudo add-apt-repository ppa:ubuntu-audio-dev**
**sudo apt-get update** [B] 
sudo apt-get dist-upgrade

[/B]
This might also work on Ubuntu 12.04 LTS.

---

### Post by chemical349 on 2012-03-31
thanks for the quick reply on fixing the audio. i have decide to use the 11.1 for now. 

i will try to fix the audio  right away. 

any suggestion for me on the display resolution??


regards< V

---

### Post by theknightlinux on 2012-03-31
Go to the top right corner, click on system settings, then go to additional drivers and see if the drivers for  your video card are active. If so please let me know if you got more options of drivers for the video card.

---

### Post by chemical349 on 2012-03-31
it's blank under "Additional Drivers"

:(

---

### Post by theknightlinux on 2012-03-31
Do you have a video card attached like a PCI, PCI-E, AGP or is it integrated to the motherboard?

---

### Post by chemical349 on 2012-03-31
i m using the onboard motherboard vga display port right now.

---

### Post by theknightlinux on 2012-03-31
If you say everything was working smoothly with Ubuntu 11.10, I find it might be a problem with the drivers or updates made by 12.04 to the kernel, or you might not have all updates installed. Have you installed all updates for Ubuntu 11.10, to do this go to the left panel and open dash home and type update and open Update Manager. It will list all updates available for your system, make sure your install them.

---

### Post by theknightlinux on 2012-03-31
If you had all updates please let me know, to see if we can try another solution.

---

### Post by chemical349 on 2012-03-31
once again, million thanks for your reply.

i am 100% sure that i had done all the update,  "There are no update to install" is shown in the udpate manager GUI.

:(

anyway, i need to go to bed for now. once again, thanks for your help. i shall keep trying tomorrow. :)

---

### Post by theknightlinux on 2012-03-31
I'm afraid I haven't been of any good help here. I'm sure someone has a solution for your problem.

---

