---
title: "Upgrading NVIDIA Graphics Card"
date: 2013-08-16
forum: Hardware
---

### Post by Josh_Mustillo on 2013-08-16
Hello guys,

I recently made my move to Ubuntu, but I have a question regarding upgrading my Graphics card, in Windows all I would have to do is take my old card at put the new one in, clean install the Drivers, but how do I accomplish this is Ubuntu?

---

### Post by Crusty Old Fart on 2013-08-17
I believe Ubuntu has a default driver built into it for Nvidia graphics cards (the "nouveau" driver). If I were you, I'd install the card, boot up, and see if I liked what appeared on my monitor. If so, I wouldn't mess with anything. However, in the event I wasn't satisfied with the default driver, or I wanted to download a proprietary driver for the video card to determine if I liked it better, then I'd change it.

Changing the driver should be a relatively simple thing to accomplish, unless you run into compatibility problems with other hardware, software, or your BIOS.

You can determine if Ubuntu has loaded the "nouveau" driver by issuing the following command:
```

lsmod | grep nouveau

```

If you install the card and have problems with it, I'll be happy to work with you to get things running.
Before installing the card, you should try to determine if it is compatible with your operating system.
If you post the version of Ubuntu you have installed, and the model number of your Nvidia card, I can help you determine compatibility.

Best wishes,

Crusty

---

### Post by grahammechanical on 2013-08-17
It all depends on which version of Ubuntu you are using. I could tell you how to do this but there is a choice of two ways to do it. It all depends upon whether you are using Ubuntu 12.04 and earlier or Ubuntu 12.10 and later.

Before you put in the new graphics card make sure that the Nouveau open source video driver is activated. That will avoid issues because of having a proprietary driver that is not suitable for the new graphic card.

After the installation of the new graphic card reboot and see how it goes. Nouveau has been improved a lot over the past 18 months. If you want to activate a proprietary video driver you need to open the Additional Drivers utility and select a driver from the list which also includes Nouveau and should be the current driver.

Where do you find the Additional Drivers utility? In 12.04 it is in the Dash. In 12.10 and later we go to System Settings>Software Sources or Software and Updates (for 13.04 & 13.10) and click on the Additional Drivers tab. Allow the utility time to locate the drivers. The machine must be connected to the Internet. You should get a selection of 4 drivers for your make of video card. Installing a proprietary video driver will also install a configuration manager for the driver. That will be put in the Dash.

If things do not work out well when you reboot. Try selecting Recovery Mode>Resume at the Grub menu. That may get you to a desktop where you can change drivers and try again. If you get a desktop with only the wallpaper, try right clicking the desktop and selecting Change Desktop Background. That will open System Settings and from there you can get to Additional Drivers.

Regards.

---

### Post by Josh_Mustillo on 2013-08-17
[SIZE=3]Thank You for that reply, I wont be purchasing my new Graphics Card anytime soon but it is a: ASUS GeForce GTX 760 DirectCU II OC 2GB, Link: [http://www.pccasegear.com/index.php?main_page=product_info&products_id=23996](http://www.pccasegear.com/index.php?main_page=product_info&products_id=23996)[/SIZE]
[SIZE=3]I have Ubuntu 13.04 latest, it says my Driver is?: Gallium 0.4 on NVE7[/SIZE]

---

### Post by Crusty Old Fart on 2013-08-17
Howdy Josh:

After reading grahammechanical's post, I realized that much has changed since I last dealt with graphics card upgrades. Consequently, most of what I know about getting everything working correctly does not apply to the newer versions of Ubuntu. Rather than making a fool of myself by wasting your time with a bunch of irrelevant guidance, I think the best thing for me to do would be to get out of the way and watch this thread progress from the sidelines.

I have no doubt that you would be much better served by grahammechanical.

Carry on lads, and good luck.

Crusty

---

### Post by Yellow Pasque on 2013-08-17
> **Josh_Mustillo said:**
> in Windows all I would have to do is take my old card at put the new one in, clean install the Drivers, but how do I accomplish this is Ubuntu?

It's basically the same in Linux (and often easier because open-source drivers don't conflict with each other):
1. If you have a proprietary driver installed, remove it (in both Windows and Linux, you may be able to get away with just swapping the cards if they both use the same driver, but better not to risk it). In your case, you are using open-source driver, which does not need to be removed.
2. Shut down and swap the cards.
3. Boot and if you need/want a proprietary driver, install it. Note that the GTX 760 needs nvidia driver >= 319.32, and this is not found in the raring/13.04 repos. Maybe someone with an nvidia card can point you to the best/easiest source.

---

