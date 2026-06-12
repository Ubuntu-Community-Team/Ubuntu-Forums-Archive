---
title: "ASUS eepc 1015PX microhone not working"
date: 2011-12-29
forum: Hardware
---

### Post by Tim Legg on 2011-12-29
Hello,

I have a ASUS 1015PC-MU17 BU netbook.  I have Ubuntu 10.04 LTS installed

I found that the microphone isn't working.  All I get is a hissing noise when the volume is raised.

Here is what lspci says about my audiocontroller.

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

I saw elsewhere that I should install pavucontrol, but all that did is basically duplicate the functionality of the sound control applet on the Gnome Panel

Tim Legg

---

### Post by wolfen69 on 2011-12-29
Double check your mic settings first, if nothing still, do:

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
```
then
```
 sudo apt-get update && sudo apt-get dist-upgrade
```
then
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
reboot.

---

### Post by Moozillaaa on 2011-12-29
Some machines with 5.1, 7.1 SurroundSound-capable hardware have settings that change the mic port INput, to a center-channel OUTput. 

I don't know how to check if that's your problem however...

---

