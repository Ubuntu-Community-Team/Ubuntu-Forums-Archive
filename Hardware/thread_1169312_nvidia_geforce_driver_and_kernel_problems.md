---
title: "nvidia geforce driver and kernel problems"
date: 2009-05-25
forum: Hardware
---

### Post by chrisbay90 on 2009-05-25
Hi,

 Can't seem to get the driver for my nvidia grpahics card to work properly in ubuntu.

[SIZE=2]**My Specs**[/SIZE]
OS: Ubuntu 9.04
Desktop: GNOME 2.26.1
Laptop: HP Pavilion dv5000
Graphics card: NVIDIA GFORCE (sorry don't know model number or anything, if you need it and know how i can find it out i will do so)

[SIZE=2]**Overview of the problem**[/SIZE]


[LIST]
[*]    I tried installing driver for the card (System > Administration > Hardware Drivers)
[*]    Jockey kept crashing but it eventually installed
[*]    Screen flickered every few minutes so i uninstalled the driver.
[*]    Ubuntu warns me about a bad driver config so i attempt to reinstall the driver.
[*]    Nothing happens when i press actiivate(under System > Administration > Hardware Drivers)
[/LIST]


[SIZE=2]**More info (if needed....but maybe its just me being longwinded)**[/SIZE]

**[SIZE=2]Original installation trouble[/SIZE]**
I needed to install the proprietry driver for my NVIDIA graphics card (System > Administration > Hardware Drivers)
It came up with the 'NVIDIA accelerated graphics driver (version 180) [Recomended]' (as well as version 173 and 96). I selected the recomended version and pressed activate.
It stayed on 0% for about 20 minutes then i got a message saying the 'Jockey' had crashed. After persistently (or maybe that would be ignorantly) restarting Hardware Drivers and pressing Activate as well as a few restarts of Ubuntu it finally decided to install all the way to 100% with no errors.

[SIZE=2]**Problems when driver was installed**[/SIZE]
The screen periodically flickered. About every 5 minutes, sometimes every 10 seconds even. Until eventually Ubuntu foze oneday with a garbled screen and then restarted itself. from that point on when ever tried to access any of the virtual terminals (Alt+Ctrl+F1-6) the screen just truned to a garbled mess of colours.

**[SIZE=2]So i uninstalled it the driver[/SIZE]**
(System > Administration > Hardware Drivers)

The flickering stoped and the virtual terminals worked.

However when i startup ubuntu i get the warning

> Ubuntu is running in low-graphics mode

The following error was enountered. You may need to update your configuration to solve this

(EE) NVIDIA(0) Failed to load the NVIDIA kernal module
(EE) NVIDIA(0) ***Aborting***
(EE) Screens(s) found but none have usable configuration.I am then presented with a few option such as debug or view log files etc. Not knowing what to do i just go to 'reconfigure > Restore default (generic) display).

I then get another warning

> There already appears to be an X server running on display :0. Should another display number be tried? Answering no will cause GDM to attempt starting the server on :0 again.If i select 'NO' the x server fails to load and brings me back to the above warning.

If i select 'YES' then restarts the X server ubuntu logs in normally (but without the driver for my graphics card.

Attempting to reinstall the driver
just plain doesnt work.

going to System > Administration > Hardware Drivers and pressing Activate brings up a progress bar for about 2 seconds witch then disapears.

I'v tried installing the recomended driver, as well as earlier verison. I get the same problem.

I'v uninstalled/reinstalled the Hardware Driver program. Doesnt help.

I'v marked all packages that turn up with the search term 'nvidia' in the synaptics package manager for re installation and applied. Didnt help.

And now im out of ideas.

[B]Please does anyone know what to do?
Any help at all would be greatly appreciated.[/B]

---

### Post by chrisbay90 on 2009-05-26
bump

---

### Post by UrbenLegend on 2009-05-26
Do a manual install with official Nvidia binaries.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Make sure you have kernel-headers package installed (should be installed by default) and the necessary compile tools (make, gcc, and the like). The nvidia installer will tell you what compile requirements are missing if there are any.

Run the installer with X server turned off, otherwise it won't work. To do this, log out and select console login in the login menu.

Hopefully this will help solve the problem.

---

### Post by chrisbay90 on 2009-05-26
> **UrbenLegend said:**
> Do a manual install with official Nvidia binaries.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Make sure you have kernel-headers package installed (should be installed by default) and the necessary compile tools (make, gcc, and the like). The nvidia installer will tell you what compile requirements are missing if there are any.

Run the installer with X server turned off, otherwise it won't work. To do this, log out and select console login in the login menu.

Hopefully this will help solve the problem.

That worked perfectly. Thank you UrbenLegend!

---

### Post by UrbenLegend on 2009-05-26
Congratulations! Glad it helped.

---

### Post by Flash412u on 2009-05-29
> **UrbenLegend said:**
> Do a manual install with official Nvidia binaries.
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Make sure you have kernel-headers package installed (should be installed by default) and the necessary compile tools (make, gcc, and the like). The nvidia installer will tell you what compile requirements are missing if there are any.
Run the installer with X server turned off, otherwise it won't work. To do this, log out and select console login in the login menu.
Hopefully this will help solve the problem.
My problem is similar but apparently I need some extra hand-holding to fix it...

After upgrading to 8.10 my nvidia drivers are not working and I am running legacy video that works.  The aliasing on the fonts is very annoying.  

BTW, I have a chip that IS on the list: GeForce 6150SE nForce 430 (rev a2) 0X0240 and it is running on an AMD 64 box.

I apt-get...purged nvidia.  
I got the proper NVIDIA-Linux-x86-180.51-pkg2.run source.
Synaptic sez I have *make, gcc* and the like all installed.  My menu.lst is correct (with 8.10 and ...-2.6.27-14 in all the right places).  

When I turn off the X server and run the NVIDIA...180...run, I get the following error

   [I]The compiler used to compile the kernel (gcc 4.1) does not exactly match the current compiler (gcc 4.3).  The Linux 2.6 kernel module loader rejects kernel modules built with a version of gcc that does not exactly match that of the compiler used to build the running kernel.

   If you know what you are doing and want to ignore the gcc version check, select "No" to continue installation.  Otherwise, select "Yes" to abort installation, set the CC environment variable to the name of the compiler used to compile your kernel, and restart installation.  Abort now?[/I]    

I hit NO and it went around again and so I hit YES.

   [I]ERROR: Installation has failed. 
[/I] 
Synaptic tells me that the version of gcc installed is the latest version, 4:4.3.1-lubuntu2
But some of the 4.3 packages have the Ubuntu circle thing and some do not.  Yet all are marked as installed.  Some of the older packages have the Ubuntu circle thing in Synaptic.    

What the heck do I need to do to get the "180" driver compiled?  What directory do I need to be in, what needs to be in there and what do I run (with X off, of course) to get this installed.  Or do I need to do some work in Synaptic instead?  Or both?

Thank you in advance for your expertise.

---

### Post by UrbenLegend on 2009-05-30
You probably got a new version of gcc from one of your repos. Try installing gcc 4.1 by forcing the version in synaptic or downloading a package from launchpad and rerunning the nvidia installer.

Here is a link to the gcc 4.1 launchpad page in case you need to download it.
[https://launchpad.net/ubuntu/intrepid/+source/gcc-4.1](https://launchpad.net/ubuntu/intrepid/+source/gcc-4.1)

Best of luck.

---

### Post by afderrick on 2009-06-07
I'm having issues installing the gcc-4.1 tar file...  I'm hoping this will work for me.  How did you get it installed?

---

### Post by UrbenLegend on 2009-06-13
Don't install the tar file, that is the source code. Install the binary packages listed on that site. The main package is gcc-4.1. Download that and install. It might ask you to download some of the other packages for dependency reasons.

Btw, sorry for the late reply I was busy with finals.

---

