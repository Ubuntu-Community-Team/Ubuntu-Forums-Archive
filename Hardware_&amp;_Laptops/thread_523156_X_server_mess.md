---
title: "X server mess"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by Licurgo on 2007-08-11
Hi guys:
I installed Ubuntu edgy on a USB, it works fine, but this morning suddendly crashes and appears the message_ failed to start the X server_ 
I use the Ubuntu at home and at work, so there are different machines, with different hardware but that was not a problem before.
After that at start I selected disc and started as a live CD, then I explored the files and find the /casper-RW/var/log/Xorg.O.log and says:

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux ubuntu 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 10 10:53:28 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) | |-->Monitor "SyncMaster"
(**) | |-->Device "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/10 0dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscale d,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/ 100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/ x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
X.Org ANSI C Emulation: 0.2
X.Org Video Driver: 0.8
X.Org XInput driver : 0.5
X.Org Server Extension : 0.2
X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
compiled for 7.0.0, module version = 1.0.0
Module class: X.Org Font Renderer
ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
compiled for 7.0.0, module version = 1.0.0
ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

Those are the data of the hardware that I have at home (The monitor and the video card) so why do not detected automatically this hardware? How I can resolve this? 
Please help

---

### Post by aysiu on 2007-08-11
I'm kind of amazed that it wouldn't crash *before*. Xorg isn't dynamic and usually is tailored to a particular set of hardware.

Just do ```
sudo dpkg-reconfigure xserver-xorg
``` the next time that happens.

---

### Post by Licurgo on 2007-08-12
Aysiu:
I give the commands: sudo dpkg-reconfigure xserver-xorg
and Says: Sudoers is in mode 00 and most be 0440 when I tried to run sudo visudo says the same problem; because is an USB installation, what is the Administrator password?

---

### Post by aysiu on 2007-08-12
Reboot and select recovery mode (this will make you root).

Then type ```
chmod 0440 /etc/sudoers
chown root:root /etc/sudoers
reboot
```

And then boot into regular mode.

---

### Post by Licurgo on 2007-08-13
Aysiu:
I tried to start in recovery mode but in the main page says USB, live, and other options, in the status bar F1 help, F2, F3, F4 VGA.
If I press F1 the F4 option says recovery mode but when I enter in the main page and press F4 opens a pop up window with the options for the monitor;
then I entered as a live CD, change the directory and modified the sudoers file as you indicated and restart.
When I restart (as USB) everything was gone somoothless but suddendly the monitor goes blank and asked me the run level, I pressed 5 (random number) then goes one line above and the cursor was blinking, I waited 10 minutes and nothing.
I must reinstall??
How I can check the integrity of this USB pendrive?? Supposing of damaged sectors

---

### Post by Licurgo on 2007-08-16
(Solved)
Hi guys:
I forget to mention that my usb pendrive is a cruzer titanium 2.0 GB with U3, and this is critical.
Because the installation process implies partition and formatting I don't realize that the U3 files are still there and when accidentally inserted the USB in an Win environment the U3 started and created a partition, erased my boot and some stuff.
Then downloaded the unistall program, run it, and followed the ubuntu  installation process and now I'm pleased with ubuntu runing smoothly.
Thanks Aysiu for your rapid response in this mess.
Thanks all guys for reading this, I hope this may be helpfull for other ubuntu users.:guitar:

---

