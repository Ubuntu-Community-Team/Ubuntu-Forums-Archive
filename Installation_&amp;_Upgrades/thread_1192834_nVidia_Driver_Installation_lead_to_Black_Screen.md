---
title: "nVidia Driver Installation lead to Black Screen"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by papasmurf6768 on 2009-06-20
Hey everyone.  My problem today is that I'm trying to install the nVidia driver on my laptop so I can use 3D Graphics.  What happens though, is after navigating to System>Administration>Hardware Drivers I get the screen that says nVidia Accelerated Graphics Driver (version 96).  I click that, then click enable.  It tells me to restart the computer, so I do.  Ubuntu 9.04 boots up just fine, but then I get the problem.  NO LOGIN SCREEN!  I know everything is working correctly though, because I here the little Ubuntu bongo beat when it's all booted, and w/out seeing a screen, I type in my Uname, Password, and then I hear the Ubuntu login beat.  So basically the problem is no video is being transmitted to my laptop monitor.  I had this exact same problem before on another laptop a while ago, and I was able to solve it by simply adding a line to some file.  It'd a blur now, but I just can;'t seem to find the website where I followed instructions from before.  If anyone knows what I have to do EASILY to get nVidia to work, please post.  I know there's a way to get video back by enabling a different driver, but I DON'T WANT TO DO THAT!  I WANT nVIDIA FOR 3D GRAPHICS!  Thanks everyone in advance.

---

### Post by Tews on 2009-06-21
Try rebooting, press ESC and boot into recovery mode and select the last option .... Fix Xserv ... or something to that effect ... this will re-write xorg.config to a default setting and your resolution will be 800x600 but we'll fix that once you can login again ... lemmie know when you're ready to proceed ... ;)

---

### Post by papasmurf6768 on 2009-06-25
I did this, but it doesn't work how I want it to.  I enabled the nVidia Driver, booted to Recovery Mode, and chose the "Fix Graphics Problems" or something like that.  Doing this gives me a login screen, but it disables nVidia.  I want nVidia enabled, which I know is possible because I've done it before.

---

### Post by papasmurf6768 on 2009-07-15
Please someone how do i fix this!!!! I want to keep nvidia graphics so i can do desktop effects!

---

### Post by gianluca.pettinello on 2009-07-15
Why you don't install the last drivers 180.xx which are more reliable?

If you are not able via menu you can open, in recovery mode, synaptics and install the following packages

nvidia-180-kernel-source
nvidia-180-modaliases
nvidia-180-libvdpau
nvidia-glx-180

Then you can rebuild your xorg.conf by typing in a terminal

sudo dpkg-reconfigure -phigh xserver-xorg

Finally restart

Ciao
Gianluca

---

### Post by lateralforce on 2009-07-15
> **gianluca.pettinello said:**
> Why you don't install the last drivers 180.xx which are more reliable?

If you are not able via menu you can open, in recovery mode, synaptics and install the following packages

nvidia-180-kernel-source
nvidia-180-modaliases
nvidia-180-libvdpau
nvidia-glx-180

Then you can rebuild your xorg.conf by typing in a terminal

sudo dpkg-reconfigure -phigh xserver-xorg

Finally restart

Ciao
Gianluca
I have the exact same problem as papasmurf6768. I'm using a 6800 GT. I've tried installing the 180 drivers through the jockey ("Administration -> Hardware Drivers") and with envyng. Would "sudo dpkg-reconfigure -phigh xserver-xorg" do something different then what envyng does?

---

### Post by papasmurf6768 on 2009-07-16
> **gianluca.pettinello said:**
> Why you don't install the last drivers 180.xx which are more reliable?

If you are not able via menu you can open, in recovery mode, synaptics and install the following packages

nvidia-180-kernel-source
nvidia-180-modaliases
nvidia-180-libvdpau
nvidia-glx-180

Then you can rebuild your xorg.conf by typing in a terminal

sudo dpkg-reconfigure -phigh xserver-xorg

Finally restart

Ciao
Gianluca


OK...I did what you said...but under Hardware Drivers, it still says nVidia is disabled... Is there any way I can test to see if its working?

P.S.  There wasn't a nvidia-glx-180 package but there was a nvdia-glx-180-dev  so i installed that instead...

Thanks for the help

---

### Post by brant762 on 2009-07-16
I have the same thing going on with my GeForce 4 Ti4400 I am attempting to install the 96.43.13 driver. The 96.43.10 driver will not give me better resolution options than 640 X 480. I get Root access, Disable X server, install the driver, start-up X server, reboot and get a blank(black) login screen.

---

### Post by lateralforce on 2009-07-17
I get black screen with the 180, 173 and 96 version drivers. I've searched on launchpad to see if this bug is reported but i haven't seen it. Maybe someone else can double check before we report..

---

### Post by lateralforce on 2009-07-19
The same result with the 185.18.14 driver!

Could someone with a little more ubuntu experience confirm that this needs to be reported and point me in the right direction?

---

### Post by lateralforce on 2009-07-19
SIGH! The DVI port was disabled by default in the nvidia drivers.

---

