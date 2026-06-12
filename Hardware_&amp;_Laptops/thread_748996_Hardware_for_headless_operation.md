---
title: "Hardware for headless operation"
date: 2008-04-08
forum: Hardware &amp; Laptops
---

### Post by hyperlobic on 2008-04-08
Greetings all.

I am currently looking at deploying Unbuntu server and a small form factor PC and have a couple of questions.  My experience is primarily with Solaris on Sun hardware.

What I need to know:

Is there any PC based hardware that allows connection via serial port?  I'd like to do an install without needing to install a video card, monitor and keyboard.  Can , for example, one make a vt100 connection via a serial interface to handle install and configuration of unbuntu.  Is there any hardware that supports this (other than Sun)?

Any suggested mini hardware for Ubuntu?

Thanks

---

### Post by mrsteveman1 on 2008-04-08
Grub can be made to redirect its output to a serial terminal, and you can direct the kernel to start the console on a serial port, but thats AFTER installation, and to do that stuff before install you have to have bios support for preboot serial terminals, something most pc hardware can't do. You probably won't find anything but rack mounts with this sort of built in serial console support. 

If the goal is no KVM at all on the box even before installation, you HAVE to have bios support for that terminal, there won't be any other way to do anything.

Is using serial essential? Could you make it work with IP lights out management? There are some add-in cards for any random box that let you do lights out over IP, complete with a little web interface that runs independently of the operating system.

---

### Post by mrsteveman1 on 2008-04-11
I found out syslinux can also boot using a serial console, so perhaps you could use a usb stick or a custom ISOLINUX cd (the ubuntu CD) to start the machine, start a serial console, and go from there.

The syslinux documentation has some info on this: [http://syslinux.zytor.com/wiki/index.php/SYSLINUX#SERIAL_port_.5Bbaudrate_.5Bflowcontrol.5D.5D](http://syslinux.zytor.com/wiki/index.php/SYSLINUX#SERIAL_port_.5Bbaudrate_.5Bflowcontrol.5D.5D)

---

