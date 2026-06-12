---
title: "Sixaxis Documentation"
date: 2008-06-21
forum: Hardware
---

### Post by jdwilm on 2008-06-21
Hello all.

I've put together a guide to getting the PS3 Sixaxis controller working under ubuntu at [https://help.ubuntu.com/community/Sixaxis]("https://help.ubuntu.com/community/Sixaxis").  

Included in the guide is:
Bluetooth Support
Using the Sixaxis as a pointer device

I would appreciate some feedback from people who follow the guide so i can improve it.

Thanks!

edit: can someone please move this to tutorials forum? thanks!

---

### Post by cold_fu5ion on 2008-06-23
Hi,

I've been following the guide for a little while waiting for the xorg section to be complete (I always have trouble with xorg.conf).

I just noticed today that it had been completed so I gave it another shot, but I still have troubles. I'm using 8.04 so I compiled the driver from source, and I can see the controller connects to my bluetooth dongle after disabling and enabling it. 

But after entering the required information into the xorg file I can't move the cursor in the test x-server.

The output of ls /dev/input/by-id gives this:

```
usb-Logitech_USB_RECEIVER-event-mouse  usb-SiW_SiW_060000F61100-event-joystick
usb-Logitech_USB_RECEIVER-mouse        usb-SiW_SiW_060000F61100-joystick

```

So I changed the line in my xorg.conf file to be

```
Option          "Device"        "/dev/input/by-id/usb-SiW_SiW_060000F61100-event-joystick"
```
 
and when the sixaxis controller is off it gives this:
```
usb-Logitech_USB_RECEIVER-event-mouse  usb-SiW_SiW_060000F61100-joystick
usb-Logitech_USB_RECEIVER-mouse

```

with usb-SiW_.... being in red font. So it looks like it is connecting properly but I think the problem must be with my xorg.conf file. Any ideas would be great, I'm hoping to be able to play neverball with the sixaxis controller :)

Thanks.

---

### Post by jdwilm on 2008-06-24
Do you have the controller on when you run the command to open a new X?  If you don't turn the controller on prior to that it will be unresponsive.  

Also, can you post the contents of your Xorg.1.log file to the ubuntu paste bin?

-Joe

---

### Post by cold_fu5ion on 2008-06-24
Hi,

Thanks for the quick reply. I tried out the process again to see if it was something I was doing wrong, but no luck. I am connecting the controller before starting the x session, I checked the output of  ls /dev/input/by-id before I connected the controller and then again before I started the x session.

One thing I did come across going through the second time that I forgot to mention is this line in the bluetooth section required me to do sudo

```
hidd --server --nocheck -n
```

I pasted the log file: [http://paste.ubuntu.com/22729/]("http://paste.ubuntu.com/22729/")

I didn't know that the paste bin existed, pretty handy for things like this!

Hope this helps.

---

### Post by jdwilm on 2008-06-25
sorry, can you also post your xorg.conf.sixaxis?

---

### Post by cold_fu5ion on 2008-06-25
Sure,

it's here: [http://paste.ubuntu.com/22793/]("http://paste.ubuntu.com/22793/")

---

### Post by jdwilm on 2008-06-25
Your xserver is having issues loading the joystick module.

```
(II) LoadModule: "joystick"
(WW) Warning, couldn't open module joystick
(II) UnloadModule: "joystick"
(EE) Failed to load module "joystick" (module does not exist, 0)
(EE) No Input driver matching `joystick'

```

There are a few possible causes i can see.
1.  You installed the driver from the repository before compiling your own and it's conflicting now.  In this case you should uninstall the repo version and reinstall yours.

2.  After you compiled your drivers you forgot to install them.  

-Joe

---

### Post by cold_fu5ion on 2008-06-25
Hi again,

I had previously installed "xserver-xorg-input-joystick" from apt-get but I removed it before compiling "xf86-input-joystick". I checked Synaptic and a package just called "joystick" was installed, I thought that this could be the problem so I completly removed it, I also uninstalled the driver I compiled using 'sudo make uninstall' from the source dir.

I then deleted the source and went through the guide again but I get the same result, " Failed to load module "joystick" (module does not exist, 0)" still shows up in my xserver log.

Do you think it could be that I have to compile the module "joystick" from source? It makes sence that it cant find 'joystick' now, since I just removed it. But before it did exist.

---

### Post by jdwilm on 2008-06-26
I have to go to work now so this will be a short reply.  Here are a few lines from my X log.  Hopefully they will be of some assistance until i can give you a better reply.

```
joe@joe-media:~$ less /var/log/Xorg.1.log | grep joystick
(II) LoadModule: "joystick"
(II) Loading /usr/lib/xorg/modules/input//joystick_drv.so
(II) Module joystick: vendor="X.Org Foundation"
(**) Option "Device" "/dev/input/by-id/usb-Broadcom_Corp_BCM92045B3_ROM_00191567386A-event-joystick"

```

xserver sees the xserver-xorg-input-joystick driver simply as joystick.

---

### Post by cold_fu5ion on 2008-06-27
That was just what I needed!

After reading your post I searched my file system for "joystick_drv.so", I found t but instead of being in "/usr/lib/xorg/modules/input/" like your log file says, mine was in "/usr/local/lib/xorg/modules/input". So I uninstalled the module again and reinstalled to see which files are actually created. I moved the 2 files created to the same folder that yours are in and now it works in xorg.

I have no idea why the driver would install to a different place on my system that it would on yours though.

Thank you for all your help, no I just have to work on getting it to work with some games.

---

### Post by jdwilm on 2008-06-27
It would appear i forgot to add an option needed by the configure file to put the library where xorg is going to look for it.  The configure line should look like this...
```

./configure --libdir=/usr/lib

```

---

