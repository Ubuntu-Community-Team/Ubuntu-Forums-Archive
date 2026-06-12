---
title: "Mounting  a USB 2.0 Manual Share Switch Hub"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by gjohnno on 2009-06-08
I have just installed a USB 2.0 Manual Share Switch Hub . One conection going to a laptop ( Windows XP) and the other to a desktop ( Ubuntu 9.4 ) From the 4 usb ports I have connected a printer , a scanner, an external floppy disk drive. The 4th USB port is vacant for now.

When I switch the HUB to the Windows XP connection , this system recognises the devices hanging off the USB hub

However when I switch over to the Ubuntu 9.4 connection , none of the devices are recognised.

I previously have had the printer , scanner and external floppy drive install direct to the Ubuntu and they have all worked

Please could someone please advice what steps I need to take so my ubuntu system recognises the USB 2.0 Switch Hub and the devices connected to it

Thank you

Gjohnno

---

### Post by geekygirl on 2009-06-16
Hiya - psst its me!  lol ;)

Ok here is what I would try first:

You need to check that Ubuntu is actually even able to see the hub itself.

Unplug everything, including the other computer and do the following in the terminal:

```
lsusb
```You should get a result that suggests there is a USB Hub device attached.

Since all the devices work when plugged in on their own directly - we can safely say this is an issue with the hub itself and it might be a case of when its being used by the XP machine, of course it will not see it, however the hub itself is not sending a signal, or Ubuntu is not picking up when switch is flicked.

Have you also tried flicking the switch and then plugging the hub into your Ubuntu machine and see what happens then? 

Just sounds like the actual switching process is not being recognized....

Another thing to try, switch over the hub as you expect to do so if it was to work and in a terminal type the following:

```
dmesg
```

Post the last few lines from that here as it might give a bit of an insight as to whats happening  :)

---

