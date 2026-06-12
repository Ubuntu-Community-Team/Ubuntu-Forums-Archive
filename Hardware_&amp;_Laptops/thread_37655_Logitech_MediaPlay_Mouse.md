---
title: "Logitech MediaPlay Mouse"
date: 2005-05-28
forum: Hardware &amp; Laptops
---

### Post by spacemonkey on 2005-05-28
I'm wondering if anyone can help me get my Logitech MediaPlay wireless mouse working on Hoary.  Right now it works great as a mouse, and it's plugged into the ps2 port, but I want the media buttons on it to be functional.  The only thing I've been able to find is this:

[http://daemon.prozone.ws/~david/projects/lmpcm_usb/](http://daemon.prozone.ws/~david/projects/lmpcm_usb/)

I tried to follow these instructions, but many of the files and folders it talks about simply do not exist on Ubuntu.  I tried compiling the driver, and the folders it tried to install to don't exist, so it gives me errors.  Does anyone know how to modify this driver to work for ubuntu.  I assume I will have to plug the mouse into the USB port to get the media buttons to work also.

---

### Post by doliveira on 2005-06-07
Hi!

Well, I don't know what files and folders you are talking about but if it's kernel source, that's necessary to compile any kernel module (driver).
Post here your compilation results, that might help.

Regards

---

### Post by spacemonkey on 2005-06-29
It says it can't find /lib/modules/2.6.10-5-686-smp/build directory.  Would that be because I don't have the source installed?  And if so, do I need to install the linux source for 2.6.10 from synaptic?

---

### Post by orangelamp on 2005-06-30
I'm trying to get this to work now. did you have any sucess with the mouse?

---

### Post by spacemonkey on 2005-07-04
nothing yet, but I e-mailed the developer, and he said he got it to work on Ubuntu by compiling a custom kernel.  So in the near future I plan to follow the howto on compiling a custom kernel (it's in the tips and tricks forum), then attempt to install the driver.  I'll let you know if I come up with anything.

---

### Post by CompShrink on 2005-12-10
Check out what I posted at: [http://ubuntuforums.org/showthread.php?t=65471&page=14](http://ubuntuforums.org/showthread.php?t=65471&page=14)

I got all but the 2 side buttons on my Logitech Mediaplay cordless mouse to work in Breezy. No kernel recompile or anything.

---

### Post by daynah on 2006-01-27
CompShrink, where did you stop following the original post and start modifying it for the MediaPlay mouse?

---

### Post by CompShrink on 2006-02-07
I outlined what I did here: [http://ubuntuforums.org/showpost.php?p=560528&postcount=140](http://ubuntuforums.org/showpost.php?p=560528&postcount=140)

---

### Post by MblKiTA on 2006-02-16
> 
Once you do the following, it works after reboot only when you execute the following in a terminal:

Code:
```

$ sudo rmmod usbhid
$ sudo rmmod lmpcm_usb
$ sudo modprobe lmpcm_usb

```

And if I've also got a Logitech usb keyboard?
When I do this *$ sudo rmmod usbhid* it stops working too ;(
I have to use PS/2 keyb?

---

### Post by TaopaiC on 2006-03-20
**To MblKiTA :**
I use this method to work with MediaPlay mouse and a usb keyboard

Follow the install guide but not remove usbhid from /lib/modules/your-kernel-version/misc/modules.dep

edit a new file in /etc/modprobe.d
```
sudo geditor /etc/modprobe.d/lmpcm_usb
```
and paste this code into the file
```
install usbhid  /sbin/modprobe lmpcm_usb; /sbin/modprobe --ignore-install usbhid

```

after reboot, usb keyboard and mouse work correctly.

**To spacemonkey :**

This can solve the problem of "missing folder"

```
sudo apt-get install module-assistant
sudo module-assistant prepare
```


Regards

---

