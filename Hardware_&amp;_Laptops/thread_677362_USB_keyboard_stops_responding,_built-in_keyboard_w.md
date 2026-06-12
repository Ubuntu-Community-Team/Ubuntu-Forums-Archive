---
title: "USB keyboard stops responding, built-in keyboard works fine"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by MilosBGood on 2008-01-24
Hi :)

I tried to look around the forums but didn't find any  advice on this matter in similar threads. 

I have a Logitech Alto keyboard which is also a laptop stand and an usb hub. Suddenly the keyboard part stops responding (mouse is plugged in the Alto's hub, and sometimes still works, sometimes doesn't). The only solution i found is to unplug and replug Alto's usb from laptop... 
While this is happening, the regular (built in) keyboard and touchpad work fine...

Any advice?


Thanks, 
Milos

---

### Post by Dngrsone on 2008-01-24
Change the batteries?  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/eh.gif[/IMG]

---

### Post by MilosBGood on 2008-01-25
It doesn't work on batteries ):P
[http://www.logitech.com/index.cfm/notebook_products/stands/devices/190&cl=us,en](http://www.logitech.com/index.cfm/notebook_products/stands/devices/190&cl=us,en)

---

### Post by Dngrsone on 2008-01-26
Ah... sorry about that.  You said USB and I read wireless for some weird reason (note to self... take your meds).  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

Well, does anything else work in those USB ports on the computer?  Is there a possibility that the USB cable on the keyboard is damaged/worn?

---

### Post by MilosBGood on 2008-01-26
:)
Well, actually there are two kinds of the behaviour...
When the keyboard stucks, i just unplug/replug and it starts again. But sometimes this doesn't help and at that time all of the usb ports on the laptop are dead (i tried with different devices, no signs of life).
The keyboard was working perfectly until i installed Ubuntu... :)

---

### Post by MilosBGood on 2008-01-29
Anybody? :)

---

### Post by DrOlaf on 2008-01-29
I have a similar-ish problem with my laptop (HP Pavilion dv2000 series), where USB devices become sluggish and unresponsive if I don't type anything or move the mouse for 10 minutes or so. I'm able to bring things back by unloading and reloading the USB driver by typing:

```
sudo modprobe -r -v ehci_hcd && sudo modprobe -v ehci_hcd
```

I wish I could find a permanent solution though.

---

### Post by MilosBGood on 2008-01-29
Thanks :)
I'll try this when it happens again. Although it's not a permanent solution, it's much better than restarting the computer. ;)

---

