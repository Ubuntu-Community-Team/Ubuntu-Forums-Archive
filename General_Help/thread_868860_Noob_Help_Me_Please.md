---
title: "Noob Help Me Please"
date: 2008-07-24
forum: General Help
---

### Post by Jimbo101 on 2008-07-24
Hi All,

I m completely new to Ubuntu and a ahving some issues getting started. Any help would be very much appreciated.

I am not sure if this is the right place to put this post so apologies if it isn't.

I have spent the last two days trying to slve this problem and tried many things form this forum to no avail as yet.

I have installed Hardy onto my PC which has an nvidia graphics card. Everything installed fine apart from the drivers for nvidia. I finally managed to install the driver and change my screen resolution but am left with two problems since the driver installatin.

1.) When I boot up or reboot the system hangs on a blank screen. I can only log in by ging through recovery mode.

2.) When I finally log in my screen is distorted. It has coloured stripes all across it and buttons only appear if my cursor is hoverin over them.

3.) Also it now likes to randomly log itself out.

Like I said any help would be really gratefully appreciated.

Many Thanks
Jamie

---

### Post by silkstone on 2008-07-24
Could you give us some details of your hardware?

What processor, which Nvidia graphics card, etc?

Also, how did you install the drivers?

---

### Post by Jimbo101 on 2008-07-24
I will give what info I can about hardware but some I am not sure about.

Processor AMD Athlon 64 bit 1700+ (Compaq Presario 6000 series)
The nvidia card I am not sure on but I think it is a GeForce 200 series. Hope this helps

---

### Post by silkstone on 2008-07-24
Sorry I can't give you a definite answer - that's quite an old card. There are Nvidia drivers available through Synaptic, for old and new cards, and I guess you've tried these.

Many people have success with Envy...

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by mikedemario17 on 2008-07-24
well you should deff go with ubuntu 7.10 if ur pc is not all that new because 8.04 was slow for me and i couldnt get any thing done...but installing a new 7.10 on ur system might take care of that.

if u want info on ur pc then type this into a terminal...

> sudo lshw

---

### Post by timcredible on 2008-07-24
how did you install the driver?  you should have been able to just click on the restricted hardware drivers.

---

### Post by Ryadt on 2008-07-24
> **Jimbo101 said:**
> Hi All,

I m completely new to Ubuntu and a ahving some issues getting started. Any help would be very much appreciated.

I am not sure if this is the right place to put this post so apologies if it isn't.

I have spent the last two days trying to slve this problem and tried many things form this forum to no avail as yet.

I have installed Hardy onto my PC which has an nvidia graphics card. Everything installed fine apart from the drivers for nvidia. I finally managed to install the driver and change my screen resolution but am left with two problems since the driver installatin.

1.) When I boot up or reboot the system hangs on a blank screen. I can only log in by ging through recovery mode.

2.) When I finally log in my screen is distorted. It has coloured stripes all across it and buttons only appear if my cursor is hoverin over them.

3.) Also it now likes to randomly log itself out.

Like I said any help would be really gratefully appreciated.

Many Thanks
Jamie
Try disabling your graphic card driver. Reboot and see if it solves the problem.System > Hardware Drivers.
Also type in terminal ```
lshw -C Display
```
and print the display.

---

