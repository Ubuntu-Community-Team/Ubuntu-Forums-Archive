---
title: "Blue Snowball Ice isn't recognized in Pulse Audio"
date: 2015-10-16
forum: Hardware
---

### Post by ernestThornhill on 2015-10-16
Can someone help me with this as well? I just bought this Microphone under the assumption that it worked fine under Linux.

dmesg:
> 
[719184.006489] usb 2-1.7: new full-speed USB device number 6 using ehci-pci
[719194.111325] usb 2-1.7: New USB device found, idVendor=0d8c, idProduct=0005
[719194.111328] usb 2-1.7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[719194.111329] usb 2-1.7: Product: Blue Snowball 
[719194.111954] usb 2-1.7: can't set config #1, error -32


I am running Ubuntu 14.04 with Kernel 3.16.0-38-generic. Any help would be appreciated as I feel like I just wasted 40 dollars.

---

### Post by Bucky Ball on 2015-10-16
Welcome. This may or may not help, but have you done a full update/upgrade lately?

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

This will not upgrade your current release to a newer one. 

As you give no details whatsoever as to how it doesn't work, it is hard to give much support. Perhaps describe exactly what you are doing to try and use it. Does it show up in Pulseaudio Volume Control under the 'Input' tab? Does anything happen on the level meter when you test the mic? Is there a hardware switch on the mic anywhere or does it need 48volt phantom power from somewhere?

As far as your output goes the Snowball is present and accounted for. The 'can't set config #1, error -32' error not sure about. Just a thought: Have you tried it in another USB port? 

More specific details will help us help you. Thanks. :)

---

### Post by ernestThornhill on 2015-10-16
Sorry I didn't put as much information as I should have, it was late at night and I was frustrated.

I am currently up to date according to my system.

When I plug in the Microphone, it lights up Red to indicate that it has power. But when going to PulseAudio and Inputs, the Microphone doesn't show up at all. No program is able to see the Microphone either. I have tried different USB Cables, and everywhere available USB slot on the case, nothing seems to make it work. It isn't the Microphone, because running it on a Mac and Windows computer works perfectly fine. 

As far as the computer seems to be concerned, it's connected but unusable. Not visible at all to PulseAudio, Alsamixer, Pauvaudio (I think that's how you spell it), Audacity, ect.

The microphone is powered over USB, and on the website it says that it needs no drivers, and this appears to be true on the Windows and Mac machines I have tried it on.

Please let me know if you need any more information.

---

