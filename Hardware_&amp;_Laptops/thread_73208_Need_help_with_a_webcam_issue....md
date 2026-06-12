---
title: "Need help with a webcam issue..."
date: 2005-10-08
forum: Hardware &amp; Laptops
---

### Post by skelooth on 2005-10-08
I have a very old usb logitech quickcam cs330.... logitech does not provide drivers for this webcam... i am screwed out of using it in linux right?

Also, is there a list of SUPPORTED webcams or recommeneded webcams?

I need a webcam that I can use with the GIMP that has a delay/timer function.

---

### Post by skelooth on 2005-10-08
Okay, i just tried downloading the spca5xx driver, and it won't compile.

```

 make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/skel1/Desktop/spca5xx-20051001.tar.gz_FILES/spca5xx-20051001 CC=cc modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

```

---

### Post by skelooth on 2005-10-09
slow board eh?

What I'd REALLY be interested in, is a list of supported webcams "out of the box"... does such a list exist??? I REALLY need to be able to take pics from the gimp with a 6 so second delay, so ANY help would be appreciated.

---

### Post by skelooth on 2005-10-09
it's kind of frustrating to buy hardware for a linux box.

NO VENDORS put down if their hardware/drivers are supported by any flavors of linux, and it's damn near impossible to find a list of supported hardware.

???????????????????????

---

### Post by skelooth on 2005-10-09
i almost feel bad for bumping for this???

---

### Post by newOldUser on 2005-10-09
Don't feel bad.

I have the Intel version of your webcam. It's got the Intel logo on it but the model is the cs330.  It's an old usb webcam.  I've got a little experience with Linux but not much with ubuntu (had 5.04 on my box for a week). If I get it working I'll post here. If you get it working you do the same.

You're not alone.  

ps: I've also seen other threads about the spca50xx driver working under ubuntu 5.04 you might want to search the forums.

---

### Post by skelooth on 2005-10-09
ooh yeah, i got spca installed, i didn't realize there was a .deb package available. The problem is that the webcam doesn't show up in the GIMP. I'm starting to think getting a cheap digital camera is my only option.

---

### Post by Joey French on 2005-10-09
I have yet to get my webcam working. It seems you may not be getting many responses because of the fact that webcams are *not* one of Ubuntu's strong points (mine is a cheap Creative Webcam NX).

Sad really. I would absolutely love to have mine work, it would mean the world to me, but buying a new one that functions under Linux seems so lame, you know? Especially since I got like two days of use out of it before moving to the world of Linux.

---

### Post by skelooth on 2005-10-09
okay, i went out and BOUGHT a digital camera for 150 bucks...........

it seems to be the only camera under the sun NOT supported by gphoto??? Their support goes from a300, a310, a400, a500 .......... mine is the a410...........


I CAN'T WIN!!!!!!!!!!!!!!!!! I'm compiling/installing gphoto anyway.... crossing my fingers

---

### Post by newOldUser on 2005-10-10
This is my second try at posting this... if it's a duplicate, I apologize.... don't know where the first one went...

I did some looking around and experimenting today. I'm spending way too much time on something that should be a plug-n-go thing.

I found this thread about some problems in Breezy: [http://www.ubuntuforums.org/showthread.php?t=70657&highlight=cs330](http://www.ubuntuforums.org/showthread.php?t=70657&highlight=cs330)  Look at message #6 from APIS.  I've sent a message asking APIS if he had the cs330 working under Hoary. Let you know what I hear.

I tried another webcam. A Logitech usb "eye-ball" type. Model number V-UB2. It's an oldie. It didn't work.

I then tried a D-Link DSB-C100 USB webcam. Once again its several years old but it must have a different chipset. After plugging it in I did a "dmesg" in a terminal windows and got this:

```

usb 3-1: new full speed USB device using uhci_hcd and address 9
usb 3-1: device descriptor read/64, error -71
drivers/usb/media/ov511.c: USB OV511+ video device found
drivers/usb/media/ov511.c: model: Generic Camera (no ID)
drivers/usb/media/ov511.c: i2c write retries exhausted
drivers/usb/media/ov511.c: Sensor is an OV6620
drivers/usb/media/ov511.c: Device at usb-0000:00:1d.2-1 registered to minor 0

```

When I went into System......Preferences....Multimedia System Selector.  I was able to get video when I selected v4l but not v4l2.   I was not able to use the D-Link under GnomeMeeting (I think it uses v4l2?). 

I have been able to use this D-Link on other linux distros. I've used it on DSL (DamnSmallLinux [http://www.damnsmalllinux.org](http://www.damnsmalllinux.org) ). It seems to work fine with Motion and Gqcam.  

I haven't tried to compile the SPCA drivers yet but I guess it might come to that. I'll have to do some more reading, I'm not fimilar with how to do the compiles under ubuntu...... or maybe I'll just keep using Windows for the webcam stuff, seams a lot easier and I've already got the software loaded.

ps:
I tried the CS330 and Logitech on the DSL box and they didn't work.  I didn't fiddle much with them. Just plugged them in and crossed my fingers.

---

### Post by newOldUser on 2005-10-10
OK... a few more baby steps.....

I re-read [http://www.ubuntuforums.org/showthread.php?t=70657&page=3&highlight=cs330](http://www.ubuntuforums.org/showthread.php?t=70657&page=3&highlight=cs330) Arnieboy's post #21.  Seems like he was telling us how to compile the driver....

I tried his method the first time. The only thing I change was I used 20051001 instead of 200509xx since there's a newer driver available.    I got some error about 
```

spca5xx: version magic '2.6.10-5-386 preempt 386 gcc-3.4' should be '2.6.10-5-386 preempt 386 gcc-3.3'

```

So I re-did all his steps again, using the 20051001 driver, but instead of gcc-3.4 I used gcc-3.3   That seems to have made some progress. Now when I plug my CS330 in and do a dmesg I see

```

 USB SPCA5XX camera found. Type Intel Create and Share (SPCA501?+SAA7113?)
 [spca5xx_probe:8764] Camera type YUYV

```

I can even go into xsane (Applications....Graphics.....Xsane) and aquire a picture. I was fiddling with the settings when I lost the camera.  The colors in the picture were off but you could see an image. Not sure what happened. I'm getting a "Failed to start scanner" message now.

I tried doing a reboot but all I'm getting is VIDEOCAPTURE: Invalid Format (7, 9, 14, 13, 16, etc) messages.

Maybe someone can build on this and get us closer to an answer.

Good thing it's a holiday and I got some time to kill.

---

### Post by skelooth on 2005-10-12
I've actually given up on the webcam idea anyway since it's less than ideal for what I'm using it for.

I was REALLY curious if anyone has a digital camera that was/is inexpensive and works with gphoto??? I don't want to buy one online unless I know for a fact it's going to work. I might make a seperate topic for it.

---

