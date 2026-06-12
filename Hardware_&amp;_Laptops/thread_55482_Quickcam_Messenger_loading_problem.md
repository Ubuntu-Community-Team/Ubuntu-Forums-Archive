---
title: "Quickcam Messenger loading problem"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by Altmenorg on 2005-08-09
Hi all.

I compiled yesterday the driver found there: [http://home.mag.cx/messenger/](http://home.mag.cx/messenger/)

I first had a problem because alsa was loading snd_usb before snd_pci, then my webcam microphone was detected as the first sound card and I got no sound.

This was resolved by loading my chipset driver whithin the /etc/modules file in the first place, then the snd_usb is loaded in the second place and that works (in case someone has the issue that might help :-P ).

I have another apparently know problem for which I haven't been able to find the solution...
The driver is working fine but isn't loaded correctly.
I have to perform a "sudo rmmod quickcam && sudo modprobe quickcam" after each boot to get it working fine.

The developper is aware of the problem and doesn't have the solution at the moment (but says it might be corrected with the next version).

My question is, how to perform this manipulation automatically at the end of the booting process ?
I can use a kde bootscript, but typing the password at each boot in a bit annoying ;)
I'd appreciate to perform that whithin a root script or something like that that would run just before kdm launching (to be sure it is performed after the initial bad loading).

Thanks in advance for your help ;)

---

### Post by mo_x on 2005-08-09
You can create a script in /etc/init.d, for example /etc/init.d/quickcam.sh, and create a symbolic link to this script in the /etc/rcS.d directory:
sudo ln -s /etc/init.d/quickcam.sh /etc/rcS.d/S99quickcam.

---

### Post by Altmenorg on 2005-08-10
[QUOTE=mo_x]You can create a script in /etc/init.d, for example /etc/init.d/quickcam.sh, and create a symbolic link to this script in the /etc/rcS.d directory:
sudo ln -s /etc/init.d/quickcam.sh /etc/rcS.d/S99quickcam.[/QUOTE]
 I'll try this.
Thanks ;)

---

### Post by hardw1re on 2005-08-22
hi, im having so much difficulty getting this to install on my x86_64 system (system details below)
```
(Kernel):[Linux 2.6.10-5-amd64-generic x86_64] (Uptime):[53 min] (Load):[0.14] (CPUCount):[1] (Model):[AMD Athlon(tm) 64 Processor 3000+] (Clock):[1872.192MHz] (Cache):[512 KB] (Bogomips):[3710.97] (Mem):[413/1023M] (Total Space):[506.4G] (Processes):[99]
```

What sort of system did you install this on? im really annoyed that i cannot get it working, it means i have to boot to windows all the time when i webcam.

1)the install script cannot detect the camera, it is listed in lsusb
```
Bus 001 Device 006: ID 046d:08f0 Logitech, Inc.
```
but it cant seem to install / load / compile the driver
any help would be appreciated :)

cheers,
hardw1re / Pete

---

