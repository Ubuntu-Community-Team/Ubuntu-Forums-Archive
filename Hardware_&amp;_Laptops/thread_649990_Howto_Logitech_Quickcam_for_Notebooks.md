---
title: "Howto: Logitech Quickcam for Notebooks"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by ma-tai on 2007-12-25
This is not about Pro, Deluxe, etc. 
This was on Edgy.

Install packages: build-essentials spca5xx-source gspca-source and the appropriate  linux-headers

untar the sources (they lie in /usr/bin)

make

sudo make install

for both of them

in modules/spca5xx/drivers/usb/spca5xx.c
edit 
#include <linux/config.h>
to
#include <linux/autoconf.h>

(maybe needed) rmmod the loaded modules
watch the kernel log while unplugging and plugging it in again

it should look like: 
```

Dec 26 00:35:21 user kernel: [13604.276000] usb 3-1: new full speed USB device using uhci_hcd and address 6
Dec 26 00:35:21 user kernel: [13604.480000] usb 3-1: configuration #1 chosen from 1 choice
Dec 26 00:35:22 user kernel: [13604.808000] Linux video capture interface: v2.00
Dec 26 00:35:22 user kernel: [13604.816000] /home/user/driver/modules/spca5xx/drivers/usb/spca5xx.c: USB SPCA5XX camera found. Logitech QC for Notebooks 
Dec 26 00:35:22 user kernel: [13604.816000] /home/user/driver/modules/spca5xx/drivers/usb/spca5xx.c: [spca5xx_probe:5548] Camera type JPEG 
Dec 26 00:35:22 user kernel: [13605.196000] /home/user/driver/modules/spca5xx/drivers/usb/zc3xx.h: [zc3xx_config:543] Find Sensor PAS202BCB
Dec 26 00:35:22 user kernel: [13605.196000] /home/user/driver/modules/spca5xx/drivers/usb/spca5xx.c: [spca5xx_getcapability:1833] maxw 640 maxh 480 minw 176 minh 144
Dec 26 00:35:22 user kernel: [13605.200000] usbcore: registered new interface driver spca5xx
Dec 26 00:35:22 user kernel: [13605.200000] /home/user/driver/modules/spca5xx/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered
Dec 26 00:35:22 user kernel: [13605.204000] zc0301: V4L2 driver for ZC0301[P] Image Processor and Control Chip v1:1.05

```

Now again for noobs:

```

sudo apt-get install build-essentials spca5xx-source gspca-source linux-headers-`uname -r`
cd /usr/bin/

sudo tar -xjvf gspca-source.tar.bz2
cd modules/gspca/
sudo make
sudo make install

cd /usr/bin/
sudo tar -xjvf spca5xx-source.tar.bz2
cd modules/spca5xx/
# in the next step, edit 
##include <linux/config.h>
#to
##include <linux/autoconf.h>
sudo nano drivers/usb/spca5xx.c
sudo make
sudo make install
sudo tail -f -n0 /var/log/messages
# plug in and out; if you're done, cancel with Ctrl-C

```

---

### Post by K.Mandla on 2007-12-25
Moved to Hardware and Laptops.

---

### Post by wurzia on 2008-01-03
I am really a noob... after installing the packages (copying your command line) I do not have those files in /usr/bin. What can I do?

---

### Post by wurzia on 2008-01-05
Update: I did it, the packages were in /usr/src. Also, I used a different gspca package as suggested in [http://mmejiav.wordpress.com/2007/06/07/modulo-gspca/](http://mmejiav.wordpress.com/2007/06/07/modulo-gspca/)
So now the webcam works with camorama. But not with Skype! Any suggestions ?

---

### Post by wurzia on 2008-01-06
One more update: I restarted the laptop and it does not work anymore even with camorama... HELP!

---

### Post by wurzia on 2008-01-15
Well, I reinstalled Skype and everything works

---

### Post by maitrei on 2008-01-22
Hi,
I have a Logitech Quickcam for Notebooks which I want to get it run
on  Debian.My kernel version is 2.6.18-5-686.
I followed exactly the steps you said, plus:
 modprobe  spca5xx gspca .
I connect and disconnect the camera and dmesg shows:

usb 5-1: new full speed USB device using uhci_hcd and address 12
usb 5-1: configuration #1 chosen from 1 choice
usbcore: registered new driver snd-usb-audio
usb 5-1: USB disconnect, address 12
usb 5-1: new full speed USB device using uhci_hcd and address 13
usb 5-1: configuration #1 chosen from 1 choice


So, it sees only the microphone integrated in the camera.
Also there is no directory /dev/video.

Any idea what is going on?

---

### Post by Comrade42 on 2008-01-28
I'm having an almost identical problem, maitrei.

Logitech Quickcam for Notebooks (no Pro, Deluxe, or anything)
on Ubuntu 7.04

My computer is detecting and using the microphone (I can talk over Skype with it) but it has failed to detect the camera.

When I use "EasyCam2", I get the error message: "No camera, or no compatible camera found"

When I use "Camorama webcam viewer" I get: "Could not connect to video device (/dev/video0). Please check connection."

When I use Terminal and type "lsusb" I get:
```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:08dd Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```

In Ekiga, when I am configuring my setup, the "Video Manager" says "No devices found" when I specify either "V4L" or "V4L2" as my video plugin. Ekiga detects the webcam's built-in microphone easily but can't find my camera.

I've looked through many similar topics on these forums about the Quickcam for Notebooks and not much of anything has helped me. I would be very grateful for some help!

---

### Post by maitrei on 2008-01-30
Hi Comrade,

Finally I got my camera running in linux but not with skype.
(it works e.g. with camorama)
The way I did is to download gspca from

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)
(for me was: gspcav1-20071224.tar.gz)

untar and read the READ_AND_INSTALL file which says I should do:
./gspca_build

(before I think I uninstalled the previous gspca, but I don't know if it was really necessary)
And after this it was working with camorama.
 
But my problems now are:

1.it doesn't see the microphone anymore, 
2.it doesn't work with skype though, when I look in the skype-options-video
it recognizes it. (when I press 'test the camera' it only shows a black screen)

Anybody can bring me a step further?

---

### Post by ztyx on 2008-03-03
> **maitrei said:**
> Hi Comrade,

Finally I got my camera running in linux but not with skype.
(it works e.g. with camorama)
The way I did is to download gspca from

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)
(for me was: gspcav1-20071224.tar.gz)

untar and read the READ_AND_INSTALL file which says I should do:
./gspca_build

(before I think I uninstalled the previous gspca, but I don't know if it was really necessary)
And after this it was working with camorama.
 
But my problems now are:

1.it doesn't see the microphone anymore, 
2.it doesn't work with skype though, when I look in the skype-options-video
it recognizes it. (when I press 'test the camera' it only shows a black screen)

Anybody can bring me a step further?

Hi maitrei,

I found your this thread through Google.I just wanted to tell you that I experience the exact same problem as you and am watching this thread from now on.

Regards,

Jens

---

### Post by lucaa on 2008-03-18
> **maitrei said:**
> 
2.it doesn't work with skype though, when I look in the skype-options-video
it recognizes it. (when I press 'test the camera' it only shows a black screen)

Anybody can bring me a step further?

Wait a while after hitting the 'Test' button in skype and try to point it to a source of light:
if we have the same camera (the QuickCam for Notebooks (not pro, not deluxe)) and the same gspca (for me too it was 20071224) then the image quality is really bad (very dark).

If I found out something about improving image quality I'll let you know...

Good luck!

---

### Post by ztyx on 2008-03-21
Hi again,

This issue is currently being solved and is discussed at:
[http://forums.quickcamteam.net/showthread.php?tid=22]("http://forums.quickcamteam.net/showthread.php?tid=22")

Jens

---

