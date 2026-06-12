---
title: "How do you re-initialise the usb module?"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by handy on 2007-01-02
Can anyone give me the command line to re-initialise the usb module?

I have edited

**/etc/modprobe.d/options**

to speed up usb mouse polling & want to test the results without rebooting, because my machine is busy for a couple of more days.

Thanks :)

---

### Post by bernied on 2007-01-02
I don't know which module it is, but try
```
lsmod
```
to see what's running, then
```
lsmod | grep usb
```
to find modules that have 'usb' in them.
Then,
```
rmmod <module>
```
to stop <module> 
**but** look out for modules that are using the one you wan't to stop, you can't stop a module that is in use by another.
Then,
```
modprobe <module>
```
to run/load a module - restart it.

---

### Post by handy on 2007-01-02
Thankyou... :KS

---

### Post by lswb on 2007-01-03
Using " sudo modprobe -r module-name " is considered "safer" than "rmmod" and it will also go through the dependencies of the module, removing others that are not needed, but that the module being removed depends on. 

You may find that you will not be able to remove all usb related modules. Even if nothing is plugged in, the usb interface itself may be considered "in use" as long as it is physically part of the system. For just a usb mouse, though, removing and reinstalling the appropriate mouse module will probably work OK.

---

### Post by samurai1200 on 2007-01-04
this is driving me insane.

i'm having an odd problem with my mouse where it stops responding and shuts off after a few minutes of being idle. after that, plugging any of my other mice (though they are all microsoft mice) doesnt work, as they are not being powered (they flash on and off once, and wont respond).
I wanted to see if restarting the usb module would work, but i cant get it to!

i have tried:

sudo modprobe -r usbhid 
(or usbcore, etc)

and

sudo rmmod usbhid

to no avail. i hit enter, it asks me for sudo password, and then nothing. it doesnt return to the shell, doesnt output anything. just blank (but still allows typing into the buffer... or wherever text goes). to escape, i must Ctrl+C.

something im missing?

---

