---
title: "[SOLVED] Compiz fusion (I think)"
date: 2008-08-19
forum: General Help
---

### Post by claymater on 2008-08-19
Im new to linux (and ubuntu) I have only played around with them on live CD's and virtual machines.. but I desided to install ubuntu on my computer (dual booting with windows) and I noticed that the desktop effects wont work... (they give me some message like "Could not load desktop effects" or something along thos lines) and I was wondering if I did something wrong... 

I dont think its my graphics card (258Mb ATI 1300) or my ram (1GB) 
or my CPU (3GHz)... any help?

---

### Post by lackoblacko on 2008-08-19
did you install the drivers for you video card and under administration options under hardware drivers, check to see if they are enabled.

---

### Post by claymater on 2008-08-19
> **lackoblacko said:**
> did you install the drivers for you video card and under administration options under hardware drivers, check to see if they are enabled.

No I didnt! But ill try that now!

---

### Post by billgoldberg on 2008-08-19
You should be good after you installed the drivers and rebooted.

Be sure to check out my guide (link in signature) about customizing Ubuntu.

I'm sure you'll find it usefull.

The guide on codecs is also a must read.

---

### Post by claymater on 2008-08-19
> **lackoblacko said:**
> did you install the drivers for you video card and under administration options under hardware drivers, check to see if they are enabled.

Ok so it is enabled, but it says "not in use"..what should I do?

---

### Post by saidinesh5 on 2008-08-19
you need to download and install the ATI drivers buddy.i had the same problem...you may choose various ways to install the drivers...like ENVY or manually download the installation file and install it...or disable it and then enable it...so that ubuntu will automatically download and install the drivers for you!!!

---

### Post by MaxIBoy on 2008-08-19
But be sure you've got a root user password set, in case you need to fall back on the recovery mode console. I did (the ATI drivers made the individual rows of pixels not line up, so the screen was gibberish except in text mode.)

---

### Post by jerome1232 on 2008-08-19
I get that on my initial login (drivers won't install), update the computer (should be a little icon annoying you top right) reboot then enable your drivers.

---

### Post by claymater on 2008-08-19
Ok thanks guys, Im going to download the ATI driver... ill keep you'll posted! :)

---

### Post by claymater on 2008-08-19
Ok so I downloaded the ATI driver.. but I dont know what to do with it now :( the file name is "ati-driver-installer-8-7-x86.x86_64.run" and I dont really know how to open it.. or use it for that matter (Im really new to linux...) So any help? 




(Oh and sorry for double posting)

---

### Post by jerome1232 on 2008-08-19
Okay there's a couple better ways to install drivers in linux.

A) In ubuntu use the hardware drivers that was mentioned earlier (system-administration-hardware drivers)

B) Use enyng,  You can install it and run it like this.

```
sudo apt-get install enyng-gtk
sudo envyng -g
```

---

### Post by pretobomba on 2008-08-19
you should try doing the following:
sudo apt-get install build-essentials debhelper
(cd the driver folder) ./ati-driver-installer-8.38.6-x86.x86_64.run --buildpkg Ubuntu/(your ubuntu version, hardy, feisty...)
take a look at the following post:
[http://ubuntuforums.org/showthread.php?t=497175](http://ubuntuforums.org/showthread.php?t=497175)

---

### Post by claymater on 2008-08-20
> **jerome1232 said:**
> Okay there's a couple better ways to install drivers in linux.

A) In ubuntu use the hardware drivers that was mentioned earlier (system-administration-hardware drivers)

B) Use enyng,  You can install it and run it like this.

```
sudo apt-get install enyng-gtk
sudo envyng -g
```

Ok I did that code, and it comes back to me with this... 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package enyng-gtk
home@home-desktop:~$ sudo envyng -g


```

Did I do  everything right?  (IM REALLY new to linux... I have almost no clue what to do, lol)

---

### Post by claymater on 2008-08-20
Wait.. I might be getting somewhere... now when I look at my "Hardware driver" I see this [IMG]http://i183.photobucket.com/albums/x23/coenat/Screenshot.png[/IMG] It says that is is enabled, and "in use". but.. I still cant enable desktop effects :( 

Does anyone know what is going on? (and Yes I have rebooted)

---

### Post by jerome1232 on 2008-08-20
Sorry that was a misstype, en**v**yng-gtk, but that's not the issue at hand now anyways you have the driver installed.


Just to make sure 3d is working, if you type glxgears in a terminal do you get three rotating gears? (yes I'm sure I typed it right this time :))

---

### Post by claymater on 2008-08-20
> **jerome1232 said:**
> Sorry that was a misstype, en**v**yng-gtk, but that's not the issue at hand now anyways you have the driver installed.


Just to make sure 3d is working, if you type glxgears in a terminal do you get three rotating gears? (yes I'm sure I typed it right this time :))

YES! I do get the gears :D, what now?

(oh and I get this!) 

home@home-desktop:~$ glxgears
20967 frames in 5.0 seconds = 4193.246 FPS
18408 frames in 5.0 seconds = 3681.476 FPS
18425 frames in 5.0 seconds = 3684.492 FPS
21172 frames in 5.0 seconds = 4234.342 FPS
20466 frames in 5.0 seconds = 4092.783 FPS
19928 frames in 5.0 seconds = 3985.421 FPS
15182 frames in 5.1 seconds = 2972.495 FPS
16612 frames in 5.0 seconds = 3321.627 FPS
19556 frames in 5.0 seconds = 3911.092 FPS
18728 frames in 5.0 seconds = 3745.552 FPS
18145 frames in 5.0 seconds = 3628.995 FPS
16701 frames in 5.0 seconds = 3340.164 FPS

---

### Post by claymater on 2008-08-20
Hey help?..I need it soon... please :( 


(sorry for double posting.. again..)

---

### Post by jerome1232 on 2008-08-20
At this point I'm not sure, If 3d acceleration is working then compiz should be working.

---

### Post by claymater on 2008-08-20
> **jerome1232 said:**
> At this point I'm not sure, If 3d acceleration is working then compiz should be working.

I know.. but I have rebooted (a bunch) and it still gives me that "desktop effects could not be enabled"... im sad :(

---

### Post by saratchandra on 2008-08-21
Type compiz --replace in the terminal and post the output

---

### Post by claymater on 2008-08-21
Ok just typed it, and this is what I got...

```
home@home-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7183 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed


```

---

### Post by claymater on 2008-08-21
Oh wait.. I got it to work! I messed up something on ubuntu so I had to reinstall it (I know.. it sucks) But when I came back I just needed to update the driver, and BAM all done! IT WORKS!!!! Thanks guys for all your help! Bye

---

