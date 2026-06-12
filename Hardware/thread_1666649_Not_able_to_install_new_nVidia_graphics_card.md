---
title: "Not able to install new nVidia graphics card"
date: 2011-01-14
forum: Hardware
---

### Post by WannabeKiwi on 2011-01-14
Hello,

Not sure if I'm in the right forum, but...

I'm trying to install a new nVidia card into my desktop, but when I try to boot up Ubuntu all I get is some flashing text containing "nouveau" and then a black and white horizontally striped screen with random green and red pixels all over. After this nothing happens, it just keeps that striped display.

This is my system:
eMachine model [[COLOR="Blue"]_T5226_[/COLOR]]("http://www.emachines.com/support/product_support.html?cat=Desktops&subcat=T%20Series&model=T5226") (Follow the link for the specs. I haven't changed anything in it except the power supply to support the new card.)
nVidia GeForce 9800 GX2
Ubuntu 10.04 32-bit

I have not installed the drivers because I obviously cannot get into Ubuntu.

Please let me know if more info is needed. Thanks.

---

### Post by darkdragn on 2011-01-14
Did you install any of the Nvidia drivers? Try booting into single usermode, running dhcp, then running 
apt-get install nvidia-current

---

### Post by papibe on 2011-01-14
If you have a xorg.conf file, it may be causing the trouble. Boot in text mode and remove it (or better rename it):
```
$ sudo mv /etc/xorg.conf /etc/xorg.conf.old
```
and then reboot:
```
$ sudo reboot
```
BTW, when you get the black screen, it may be possible to go back to a text mode interface by pressing Alt-Ctrl-F1, so you avoid a hard reset.

Regards.

---

### Post by WannabeKiwi on 2011-01-14
Okay, I was able to run in single-user mode and install the nvidia-current package. That helped immensely as I'm now able to actually get into Ubuntu.

I'm still not sure if my card is fully functional, though. I tried installing the driver NVIDIA-Linux-x86-260.19.29.run, but it keeps complaining about an X server. I tried booting into level 3, but it still complained about an X server.

Also tried renaming my xorg.conf file, but nothing changed.

Is there any way to tell if my card is working yet? When I go to the NVIDIA X Server Settings under the System menu, it says I'm not using the NVIDIA X driver. I suppose this means it's not working yet, huh?

---

### Post by WannabeKiwi on 2011-01-14
Okay, finally killed the X server via ```
/etc/init.d/gdm stop
```, ran the installer (it said the pre-setup script failed, but I continued anyway), and then restarted the X server. Let's see if this works...

---

### Post by WannabeKiwi on 2011-01-14
Damn, it started up in low-graphics mode and says this

```
Failed to initialize the NVIDIA kernel module.
Please see the system's kernel log for additional error messages and consult the NVIDIA README for details.
*** Aborting *** Screen(s) found, but none have a usable configuration.
```

---

### Post by WannabeKiwi on 2011-01-14
Found this in the kernel log:

"API mismatch: the client has the version 260.19.29, but this kernel module has the version 195.36.24"

How do I get the kernel module to have the same version as the client, whatever that means?

---

### Post by papibe on 2011-01-14
If the old graphic card was an onboard/built-in/motherboard card, it may be necessary to go to BIOS and change some settings in order to properly use the new PCI card.

Just a thought.

---

### Post by WannabeKiwi on 2011-01-17
Hi all,

I still have not figured this out. I've tried it three different ways (after installing the graphics card):

1. Boot in recovery mode, use low-graphics/failsafeX mode, install proprietary driver via the Hardware Drivers application.
2. Install the driver via [FONT="Courier New"]apt-get install nvidia-current[/FONT].
3. Download the driver from nVidia and install it according to their instructions given [here]("http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/README/index.html"). (Everything seems to run fine except the pre-install script, whatever that is.)

Sometimes I'm lucky enough to see the Ubuntu load screen (purple background with the little red/white dots underneath "ubuntu"), but then the monitor loses the signal and the screen goes black.

Any ideas??? I've been banging away at this for a week but to no avail. :frown:

---

### Post by efflandt on 2011-01-17
There was more to it than just installing **nvidia-current**.  You also should have installed **nvidia-settings** and **nvidia-current-modaliases**.  That may have helped configure the 195 drivers.

If you needed newer drivers than 195.36.24 there would have been a much easier way to install a 260.19.29 package for Lucid or Maverick by adding the x-swat repository and using sudo apt-get to install the above packages.  [http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

But since you manually ran the run script from nvidia, which I have never used, I would not know how to explain how to undo that and get back to a state where you could update or install Ubuntu nvidia packages.

Just curious what type of video card you had before this one and were you using an xorg.conf or anything other than default video drivers before.  Usually the default nouveau driver works fine with nvidia cards, at least well enough to boot, just not nearly as fast as nvidia drivers.

---

### Post by WannabeKiwi on 2011-01-17
Thanks efflandt. At this point I can't recall all the different methods that I've tried, but do remember that I did include [FONT="Courier New"]nvidia-settings[/FONT] and [FONT="Courier New"]nvidia-current-modaliases[/FONT] in one attempt of mine. No luck, though.

No worries on any undo stuff. I'm just re-installing Ubuntu at this point (I know, it's a big hammer, but I don't trust that --purge or remove will get my system back to where it was previously, and there's nothing on there that I need to keep anyway.)

The desktop I'm working with never had a video card before this. It's just an "old" (2007?) system that I got off my dad that I'm trying to get running so that I can do some research for school on GPU processing. I don't know the details of my work yet since I just started, but I figure there are two things I need:

1. The system needs to be utilizing the graphics card, and
2. I need to be able to inject code into the graphics pipeline, probably through OpenGL calls.


I wonder if the nouveau driver would be sufficient for this? **Does anyone know if I *need* the nvidia driver to do this, or would the nouveau be enough?**

---

### Post by BicyclerBoy on 2011-01-17
Cuda is not going to work on the nouveau driver, it is nvidia only.

OpenCL may have some support with nouveau but I doubt it is very important to them.

You need to post your /var/log/Xorg.0.log..

You most likely need to blacklist the nouveau kernel module because this stops nvidia driver from loading. Thank Ubuntu for this.. 

You don't need to treat linux like windows by re-installing when there is a problem. The package management system is a defining feature of Ubuntu linux.

You most likely did not have the kernel headers to compile the nvidia driver.
If you use X-swat or nvidia 3rd party ppa for pre-compilied binaries you do not have the problems of headers & updates breaking stuff.

---

