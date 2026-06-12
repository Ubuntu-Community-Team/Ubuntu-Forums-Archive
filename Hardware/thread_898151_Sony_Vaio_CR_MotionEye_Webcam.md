---
title: "Sony Vaio CR MotionEye Webcam"
date: 2008-08-22
forum: Hardware
---

### Post by subaruwrc01 on 2008-08-22
I currently have Ubuntu 8.04 installed on my new Sony Vaio CR (vgn-cr520).  How do I go about using my webcam in say programs like Pidgin.  Using it in general would also be helpful.

Thanks!
Ryan

---

### Post by Crafty Kisses on 2008-08-25
You can see if it works by doing the following:

Open Ekiga and see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly. If that doesn't work post results of > lsusb

---

### Post by subaruwrc01 on 2008-08-25
```
Bus 007 Device 002: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 05ca:1839 Ricoh Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 044e:3012 Alps Electric Co., Ltd 
Bus 001 Device 005: ID 044e:3013 Alps Electric Co., Ltd 
Bus 001 Device 004: ID 044e:3010 Alps Electric Co., Ltd 
Bus 001 Device 003: ID 044e:3011 Alps Electric Co., Ltd 
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by IntuitiveNipple on 2008-08-25
The camera is a VGP_VCC6 and is supported by the r5u870 driver (it may also be partially supported by the uvcvideo driver).
```

0x05CA, 0x1839, R5U870_DI_VGP_VCC6

```
I help maintain the r5u870 driver and it is [available from my PPA as r5u870-dkms](https://launchpad.net/~intuitivenipple/+archive?field.name_filter=r5u870&field.status_filter=published).

The package uses DKMS (Dynamic Kernel Module Support) - what this means is that the driver is automatically rebuilt by the DKMS system on the PC if the kernel is upgraded. Without DKMS a new binary driver would need to be built and installed each time the kernel was updated.

Fetch and install the r5u870 driver (for Hardy):
```

wget http://launchpadlibrarian.net/16745481/r5u870-dkms_0.11.1-0ubuntu1%7Eppa1h_all.deb
sudo dpkg -i r5u870-dkms_0.11.1-0ubuntu1~ppa1h_all.deb

```

You might have problems at boot-time with the uvcvideo and r5u870 drivers *arguing* over which should manage the camera. In that case, to manually sort it out, unload both drivers then load r5u870 first:
```

sudo modprobe -r r5u870
sudo modprobe -r uvcvideo

sudo modprobe r5u870
sudo modprobe uvcvideo

```

---

### Post by subaruwrc01 on 2008-08-25
Ok, I did all the above.  I can't test it on Ekiga because I don't feel like  going through all the setup.  It doesn't work on cheese or camorama, but from what I read, Sony webcams rarely do.  How would I go about using this on AIM?

---

### Post by IntuitiveNipple on 2008-08-25
Try it with VLC player:
```

$ vlc v4l2:// :v4l2-dev=/dev/video0 :v4l2-adev= :v4l2-standard=0

```

To install it:
```

sudo apt-get install vlc

```

---

### Post by subaruwrc01 on 2008-08-26
I get the following error:
```
Unable to open 'v4l2://'
```

---

### Post by IntuitiveNipple on 2008-08-26
Ahh yes... I should have remembered. I have installed a much newer version of VLC that supports V4L2!

You can install it from my PPA (linked in my signature-line).

---

### Post by subaruwrc01 on 2008-08-26
I see it on your site, but what exactly do I download and how do I install?

---

### Post by IntuitiveNipple on 2008-08-27
The usual process is to add my PPA repository to apt's sources list, update:
```

sudo sh -c "echo 'deb http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
sudo sh -c "echo 'deb-src http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >>/etc/apt/sources.list.d/intuitivenipple.list"
sudo apt-get update

```

and then install (the plugins are optional but generally desirable):
```

sudo apt-get install vlc-nox vlc mozilla-plugin-vlc vlc-plugin-alsa vlc-plugin-arts vlc-plugin-esd vlc-plugin-jack vlc-plugin-pulse vlc-plugin-sdl vlc-plugin-svgalib

```
Once installed it is best to remove my PPA from apt's sources list since I carry a lot of backported and upgraded packages that Update Manager might offer you - and it doesn't differentiate or flag PPA packages from *offical* packages:
```

sudo rm /etc/apt/sources.list.d/intuitivenipple.list
sudo apt-get update

```

---

### Post by subaruwrc01 on 2008-08-27
Still doesn't work:
```
 v4l2 demux error: cannot open video device (No such file or directory)
```

---

### Post by PokeParadox on 2009-06-29
Does anyone have a surefire way to make sure that the r5u870 is loaded properly at startup.
It works when I do the commands below. But I have to remember to manually do this each time I boot the PC. I've made a script so that it's easier to do this.. but I would still prefer automation here...
```
sudo modprobe -r r5u870
sudo modprobe -r uvcvideo

sudo modprobe r5u870
sudo modprobe uvcvideo
```

---

