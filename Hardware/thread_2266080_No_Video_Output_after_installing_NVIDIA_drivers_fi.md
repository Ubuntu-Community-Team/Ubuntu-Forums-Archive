---
title: "No Video Output after installing NVIDIA drivers fix"
date: 2015-02-19
forum: Hardware
---

### Post by john_doe7 on 2015-02-19
I installed the latest version of Ubuntu in the harmony of a dual boot with Windows 7. I wanted to get access to my NVIDIA GPU and get the drivers. I watched a video on how to get the correct drivers and I did so and after restarting my system I have no video output, presumably. My computer makes boot sounds after getting past certain boot phases and those sounds are still being played but there is no video output. What am I to do? The best thing I can think of is taking out my GPU then connecting via VGA and going from there but I don't know if that would work. Can someone point me in the right direction because now my computer is just a brick.

*EDIT* Just uninstalled my GPU and using the VGA port on my motherboard and now I have video output. Currently I am deleting the partition for Ubuntu.

*EDIT* After deleting the partition I entered a command line which gave me an error saying "no such partition" and that I am currently in the "grub rescue" command line. I have been in this before and now I must put in my boot disk and reinstall Windows then the drivers for my GPU, Motherboard, and such. I have solved my problem and I am going to keep this here just in case anyone has a problem like this or similar and needs help.

The drivers were obtained from ppa:xorg-edgers/ppa repository. I proceeded and installed #346 after updating the repository which was the driver number NVIDIA told me through their website.

For people looking to reinstall Windows you press your boot from key when at the BIOS then boot from the CD you put in the try and press the button any button quickly when prompted else grub rescue will get ya.

Computer specifications are:
AMD FX 4300
NVIDIA GTX 750 ti
8 GB RAM
Toshiba 1tb HD

---

