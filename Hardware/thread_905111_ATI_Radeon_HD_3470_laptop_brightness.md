---
title: "ATI Radeon HD 3470 laptop brightness"
date: 2008-08-30
forum: Hardware
---

### Post by Ivanho on 2008-08-30
This is for Ubuntu 8.04

I'm a Linux noob, so please spare me :) I have a Sony Vaio VGN-FW190 with an ATI Radeon Mobility HD 3470 video card. It's not letting me change the brightness at all. I got the driver for the video card, and the resolution and everything else is fine (1600x900) but no brightness. If you can help that'd be awesome, and if more info is needed, I'll need instructions on how to get it.

Thanks!

---

### Post by pscaffardi on 2008-08-30
I've a Sony VGN-FW11M with same ATI Radeon HD3400 video adapter, too.
I cannot change the LCD brightness from inside linux.

It seems thebrightness control is not supported by ACPI driver!

cat /proc/acpi/video/GFX0/DD01/brightness

prints:

<not supported>

Any help?

---

### Post by Ivanho on 2008-08-30
uh oh! That's no good. I honestly can't stand my brightness on high all the time.

---

### Post by cloudlight on 2008-08-30
> **Ivanho said:**
> This is for Ubuntu 8.04

I'm a Linux noob, so please spare me :) I have a Sony Vaio VGN-FW190 with an ATI Radeon Mobility HD 3470 video card. It's not letting me change the brightness at all. I got the driver for the video card, and the resolution and everything else is fine (1600x900) but no brightness. If you can help that'd be awesome, and if more info is needed, I'll need instructions on how to get it.

Thanks!

Hello Ivanho!
I am a complete newbie to Ubuntu, too. How on Earth did you manage to get the HD 3470 to work properly on your Sony? I have a Vaio VGN- FW140D and am almost pulling my hair out. Am currently working in standard 800x600 resolution, which is a nuisance. Could you instruct me how you installed the driver(s). Any help will be greatly and gratefully appreciated.
Thank you. Niclas.

---

### Post by Ivanho on 2008-08-30
Absolutely! I actually reinstalled Ubuntu because I messed up my Vista partition while doing it. I'll be doing the video soon so I'll make sure to copy everything I do!

---

### Post by Ivanho on 2008-08-31
Okies I'm all done. Here is how I got my video card working. At least it worked for me.

Right after first boot get all the available updates. After installing said updates restart Ubuntu.

Click System > Administration > Hardware Drivers

In there you will see "ATI Accelerated graphics driver" just check the check box and click "Enable" in the new window. It will download the new driver for you and then you'll have to restart and your video card should work just fine.

---

### Post by pscaffardi on 2008-08-31
Do you mean brightness control now works? i already did system updates but no way controlling the brightness. Do you?

---

### Post by Ivanho on 2008-08-31
I wish! :) That was just how to get the video card to display the correct resolutions. I have no idea how to get the brightness working.

---

### Post by cloudlight on 2008-08-31
Many thanks to you, Ivanho;
I will do as instructed and see whether this does the trick. I have the feeling I reinstall Ubuntu, though. As soon as I have done so, I'll let you know what came of it.
Again, Thank You for the immediate response.
Niclas.

---

### Post by Ninjaraffe on 2008-09-03
I've been considering buying the Sony FW so I've been reading about it on various forums. My understanding is that the function and media buttons area on this laptop is a separate piece of hardware (unrelated to the keyboard) that requires its own driver (from sony). Whats more, Sony only supports and makes drivers for Windows Vista on this laptop, so the brightness control won't even work in Windows XP.

I'd still really love to pick one of these up so I'd be interested to know if anybody gets everything functioning properly in Ubuntu.

Have you guys run into any other snags with Ubuntu on the FW?

---

### Post by pscaffardi on 2008-09-04
Anyway, there is a linux driver that supports some of the new Vaio buttons, called sony-laptop. But it seems not to detect ALL buttons but only some. I think it should be updated to support all new ACPI bios calls (that return the keyboard status, i think).

I think it could be easily implemented by hacking that driver, but i cannot get an answer from the official driver mantainer.

Brightness is the most important unsupported feature. 

Why anyone is working at that?

---

### Post by cloudlight on 2008-09-08
Awesome, Ivanho, it worked like a charm. THANK YOU VERY MUCH for your assistance.!!!
Niclas.

---

### Post by a3qp on 2008-09-09
I have a Sony Vaio VGN-SR129E/B, with a Graphic Card: ATI Mobility Radeon HD 3470 too, and still can not controll the brightness.

The fn brightness keys don't work, and the screen is too dark.

Any help in controlling the brightness will be appreciated.

Thanks,

---

### Post by josepcoves on 2008-10-07
Hi,

I have the same problem with the brightness...

I managed to install the proper ATI driver using EnvyNG software (which detects, downloads and installs the proper drivers) but it doesn't allow to change the brightness and the function keys doesn't work either. 

If anybody needs help on Wifi, I managed to install wifi drivers properly. 


Any help will be appreciated,

Josep

---

### Post by josepcoves on 2009-01-20
Hi,

I solved the brightness problem following this how-to:

[http://vaioubuntu.wordpress.com/2008/12/04/finally-a-brightness-how-to-for-vaio-fw-series/]("http://vaioubuntu.wordpress.com/2008/12/04/finally-a-brightness-how-to-for-vaio-fw-series/")

I recommend this blog for all vaio vgn users!

Hope it helps!

Josep

---

### Post by s.l.i.m on 2009-09-09
If brightness works. How to verify it without using the **fn** key ?
I have an ATI X1400 card.

i found this : [Adjusting Contrast, Brightness and Gamma on Linux. ATI Proprietary Driver (fglrx). « k3mist&#8482;]("http://k3mist.com/linux/contrast-brightness-gamma-linux/")  it works. But it is better to do this with a button an not with a command line.

Thanks.

---

### Post by Pitxyoki on 2009-09-30
Just to add to the discussion that I have the same graphics card on an Acer 5630G. I installed Debian 'squeeze' (testing) on it and the brightness keys worked without any additional configuration on my side.

As such, this problem seems to be related with the keyboard or laptop model and not with the graphics card.

---

