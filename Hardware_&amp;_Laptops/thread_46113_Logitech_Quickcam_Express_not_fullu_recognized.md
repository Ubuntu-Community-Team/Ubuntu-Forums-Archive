---
title: "Logitech Quickcam Express not fullu recognized"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by jeanjan on 2005-07-03
Hi all,

. firstly, this is my lsusb :
```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c03e Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:08f0 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
```
*note: i also have an logitech optical usb mouse*
here, something disturbs me because i have seen other people's lsusb and it was like this :
```
Bus 003 Device 003: ID 046d:0870 Logitech, Inc. QuickCam Express
```
```
$ lsmod | grep usb
usbhid                 29376  0
snd_usb_audio          60224  2
snd_pcm                84872  4 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_usb_lib            11776  1 snd_usb_audio
snd_rawmidi            22944  1 snd_usb_lib
snd                    50276  9 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device
usbcore               107384  6 usbhid,ehci_hcd,snd_usb_audio,snd_usb_lib,uhci_hcd
``` 
```
lsmod | grep uhci
uhci_hcd               30224  0
usbcore               107384  6 usbhid,ehci_hcd,snd_usb_audio,snd_usb_lib,uhci_hcd
``` 

. secondly, I installed gqcam qcam qc-usb-source qc-usb-utils and it didn't help.
qcam give me that :
```
Qcam not found
Cannot open QuickCam; exiting.
``` 
qcset -a :
```
qcset: can not open /dev/video0 (No such device)
``` 

. thirdly, i tried to install from the tar on the official site, "make all" was ok. I made : 
```
# mknod /dev/video0 c 81 0
# mknod /dev/video1 c 81 1
# chmod a+rw /dev/video0
# ln -s /dev/video0 /dev/video
``` 
But when i launch ./quickcam.sh :
```
gcc version: version gcc 3.3.5 (Debian 1:3.3.5-8ubuntu2)
Make version: GNU Make 3.80
Linker version: GNU ld version 2.15
Kernel compiler: gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)
[!] Kernel compiler and gcc seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
        export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels (kgcc is often used in Red Hat systems).
``` 
```
I can find the following probably compatible devices:
[!] Didn't find compatible cameras.
```

If someone can help me, please  :-?

---

### Post by jeanjan on 2005-07-04
When I plug off the webcam I lost my keyboard(inactive) but keep the mouse.

---

### Post by dosadi on 2005-07-16
> **jeanjan]Hi all,

. firstly, this is my lsusb :
```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c03e Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:08f0 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
```
*note: i also have an logitech optical usb mouse*
here, something disturbs me because i have seen other people's lsusb and it was like this :
```
Bus 003 Device 003: ID 046d:0870 Logitech, Inc. QuickCam Express
```
```
$ lsmod | grep usb
usbhid                 29376  0
snd_usb_audio          60224  2
snd_pcm                84872  4 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_usb_lib            11776  1 snd_usb_audio
snd_rawmidi            22944  1 snd_usb_lib
snd                    50276  9 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device
usbcore               107384  6 usbhid,ehci_hcd,snd_usb_audio,snd_usb_lib,uhci_hcd
``` 
```
lsmod | grep uhci
uhci_hcd               30224  0
usbcore               107384  6 usbhid,ehci_hcd,snd_usb_audio,snd_usb_lib,uhci_hcd
``` 

. secondly, I installed gqcam qcam qc-usb-source qc-usb-utils and it didn't help.
qcam give me that :
```
Qcam not found
Cannot open QuickCam said:**
>  Kernel compiler and gcc seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
        export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels (kgcc is often used in Red Hat systems).
``` 
```
I can find the following probably compatible devices:
[!] Didn't find compatible cameras.
```

If someone can help me, please  :-?
 I'm in a similar state thus far, but then i can't get flashplayer working in firefox either . . . so what do I expect ;)  still learning.

root@[host]:/home/[username] # lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:08f0 Logitech, Inc.
Bus 001 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000
root@[host]:/home/[username] # lsmod | grep usb
snd_usb_audio          60224  0
snd_usb_lib            11776  1 snd_usb_audio
snd_rawmidi            22944  1 snd_usb_lib
snd_pcm                84872  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    50276  9 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
usbhid                 29376  0
usbcore               107384  5 snd_usb_audio,snd_usb_lib,usbhid,uhci_hcd
root@[host]:/home/[username] # lsmod | grep uhci
uhci_hcd               30224  0
usbcore               107384  5 snd_usb_audio,snd_usb_lib,usbhid,uhci_hcd
root@[host]:/home/[username] # apt-get install gqcam qcam qc-usb-source qc-usb-utils
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libglib1.2 libgtk1.2 libgtk1.2-common libsvga1

--snip messages of success--
.
Unpacking qcam (from .../qcam_0.91-11.1_i386.deb) ...
Setting up libgtk1.2-common (1.2.10-17) ...

Setting up libglib1.2 (1.2.10-9) ...

Setting up libgtk1.2 (1.2.10-17) ...

Setting up gqcam (0.9-2) ...

Setting up libsvga1 (1.4.3-20ubuntu2) ...

Setting up qc-usb-source (0.6.2-2) ...
Setting up qc-usb-utils (0.6.2-2) ...
Setting up qcam (0.91-11.1) ...

root@[host]:/home/[username] # qcam
Qcam not found
Cannot open QuickCam; exiting.
root@[host]:/home/[username] # qcset -a
qcset: can not open /dev/video0 (No such file or directory)
root@[host]:/home/[username] #

---

