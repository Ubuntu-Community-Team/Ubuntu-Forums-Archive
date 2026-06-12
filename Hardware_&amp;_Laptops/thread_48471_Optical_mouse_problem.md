---
title: "Optical mouse problem"
date: 2005-07-12
forum: Hardware &amp; Laptops
---

### Post by geocritter on 2005-07-12
Hi Everybody,

I just installed Hoary on my 2nd hard drive, and it went well, BUT...it doesn't seem to like my mouse.  It's a Micro Innovations ps/2 optical mouse.  Here's what happens:

1.  As computer is booting, mouse "lights" up
2.  As ubuntu is booting, it gets to the "loading modules" part, and light goes out.
3.  When booted, mouse buttons seem to work, but because the optical light isn't working, you can't move the mouse or anything.

Any ideas?  I'm new to Ubuntu (used other linuxes before, though), and I thought about trying to reconfigure the mouse, but I don't know much about this "sudo" thing, plus I wouldn't know what the mouse is called anyway.  And without being able to log into root, I'm lost.

Does anyone know what's killing off the optical part of my mouse?  Is it a module problem, or something?

Thanks so much,
Dan

---

### Post by wes on 2005-09-30
Just thought I would chime in.. I don't have a solution, but I have the same exact problem, although I'm using (or rather, not using) Breezy. I tried googling stuff like "micro innovations linux module" to see if maybe there's another mouse driver that I should use, but I didn't come up with anything.. Can anyone help? Have any ideas? 

btw geocritter, sudo lets you run things as root.. ie "sudo aptitude" .. the command "sudo -s" will give you a root shell.. there is no root password, use your password when asked

---

### Post by mlomker on 2005-09-30
>  you can't move the mouse or anything.

The usb mice use the **usbhid** module.  Try **lsmod | grep hid**.

You can see what device your mouse is using by looking through **dmesg** or opening the /etc/X11/xorg.conf file.

Are you running Hoary or Breezy?  I ask because Breezy has had some bad kernels...

> to reconfigure the mouse, but I don't know much about this "sudo" thing, plus I wouldn't know what the mouse is called anyway.  And without being able to log into root, I'm lost.


Just preface your commands with **sudo** and use your regular password.  You could also **sudo passwd root** to set a different root password.

---

### Post by wes on 2005-10-01
Thank you for replying, mlomker.. Your mention of usb brought to mind the idea of connecting the mouse to a usb port using a ps/2 -> usb adapter. Tried it. It works now (albeit without the functionality of the 4th and 5th buttons, and still no help to those without an adapter). Good enough for me though!

---

### Post by greenwom on 2005-11-02
I'm also having the same problem with my Optical mouse, with an adapter it works but it shuts down (on this machine when Ubuntu boots). 

So minus the adapter how do I get it to run? 
 I need the adapter for my latpop :) and I'm out of USB ports on the desktop anyway!

---

