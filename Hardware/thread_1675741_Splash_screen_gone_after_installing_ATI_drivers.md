---
title: "Splash screen gone after installing ATI drivers"
date: 2011-01-26
forum: Hardware
---

### Post by Black Magix on 2011-01-26
My splash screen is corrupt when I load ubuntu unless i use xforcevesa at the bootup, All I get is a purple screen with a bunch of colored pixels at the top of my monitor. This happens immediately after installing the ati drivers for linux (which at this point have caused more nightmares than done any good for me.) Any ideas on how to fix this OR remove the ati modules off ubunutu and run the propeteiry drives supplied by ubuntu?

---

### Post by sikander3786 on 2011-01-26
Plymouth has got some issues ever since it was introduced in Ubuntu. After the installation of proprietary drivers (Nvidia or ATI), it goes out of shape. For a workaround, see here.

[http://ubuntu4beginners.blogspot.com/2011/01/fix-ugly-plymouth-usplash-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/01/fix-ugly-plymouth-usplash-in-ubuntu.html)

---

### Post by coffeecat on 2011-01-26
> **Black Magix said:**
> This happens immediately after installing the ati drivers for linux (which at this point have caused more nightmares than done any good for me.) Any ideas on how to fix this OR remove the ati modules off ubunutu and run the propeteiry drives supplied by ubuntu?

If you installed a driver for an ATI card and this caused an uglified Plymouth splash, then you must have installed the proprietary fglrx/catalyst driver. The open-source 'ati' driver is the driver that comes as default. So - I'm not quite clear what you mean by 'remove the ATI modules'.

Do you want to remove the driver you installed and revert to the default? If so, post details of exactly what you did to install whichever driver you installed. Did you install from the Hardware Drivers utility or from a package downloaded from the ATI site?

Also - post details of your ATI card. Some ATI chipsets seem to work better with the default open source ati driver.

---

### Post by 0N3 on 2011-01-26
Hope this helps worked for me

---

### Post by Black Magix on 2011-01-26
I actually downloaded the ati driver and installed it using the sudo sh command.


Here's the issues I'm having.

My laptop is a dual gpu system. One 4230 for low power and one 5650 for gaming and higher power applications. Windows (using catalyst) has no issues switching between these two on the fly. Catalyst in linux sees that there is a 5000 series card but has no idea what it is.

I'm trying to find a way to switch between the two or use the 5650 by default. Now then. after I installed the ATI driver from the ati website, A lot of stuff went woncky. Compiz Fuzion was having issues and X was giving me some errors. Got those worked out but now my splash screen is corrupt. I'm feeling that I got better performance (regardless of whatever card I might've been using) using the default drivers rather then the ones downloaded from ATI's website.

---

### Post by Black Magix on 2011-01-27
Splash screen works!!! Thanks!

---

### Post by 0N3 on 2011-01-27
Did the resolution fix sort it?

---

### Post by kevin82485 on 2011-03-01
> **sikander3786 said:**
> Plymouth has got some issues ever since it was introduced in Ubuntu. After the installation of proprietary drivers (Nvidia or ATI), it goes out of shape. For a workaround, see here.

[http://ubuntu4beginners.blogspot.com/2011/01/fix-ugly-plymouth-usplash-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/01/fix-ugly-plymouth-usplash-in-ubuntu.html)

Thanks, the instructions in this link totally solved my problem with the splash screen.

---

### Post by sikander3786 on 2011-03-02
> **kevin82485 said:**
> Thanks, the instructions in this link totally solved my problem with the splash screen.
You are Welcome :-)

Glad to know it worked for you.

---

