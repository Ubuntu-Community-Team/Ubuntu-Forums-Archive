---
title: "ATI graphic card and driver problems"
date: 2010-12-15
forum: Hardware
---

### Post by hanansela on 2010-12-15
Hi all
I have Ubuntu 10.4 version installed on a PC with  Gigabyte GA-G31M-ES2L motherbord and Intel Core 2 Duo E7400 possessor. Gnome version 2.30.2. The graphic card is  Spphire which seems to be parallel to Ati Radeon with ATI/AMD proprietary fglrx diriver and LG Flatron W1942T LCD screen.  I am not satisfied with display of images in FireFox and fonts in PDF files (various software), they are some times blurry. I think also that the driver is locking my screen (when i am using FireFox) so I need to restart (Alt-Ctl-f1 is not functioning when the screen is locked). Is there any way to get a better display ? should i swich to a more frindly graphic card that have Ubuntu drivers? I do not need the card for gaming, only for the web (images and text), PDF files and Open Office applications. 
Thank you

---

### Post by coffeecat on 2010-12-15
Welcome to the forum. The one most important piece of information you haven't told us is: which ATI Radeon card do you have?

---

### Post by hanansela on 2010-12-15
Sorry, you are right: the grapic card is ATI HD 4350 512MB GDDR2 DX10.1 HDTV DVI PCI-E2.0

---

### Post by coffeecat on 2010-12-15
> **hanansela said:**
>  ATI HD 4350

Well, well. That's the graphics chipset in the machine I'm posting from. :) I have no problems with this, either fuzziness or locking up. But I'm not using the proprietary fglrx driver - rather the default open source driver. In fact with the 4*** range I believe it is better to use the open source driver. When I tried the fglrx driver I could detect no advantage at all. 

You don't need to change graphics card. If you are not a gamer, you can get all the 3d acceleration you need for compiz effects with this card and the open source driver. I suggest you uninstall the fglrx driver and see if that helps. Go to System > Administration > Additional Drivers. Disable the fglrx driver and reboot and see how you get on. If you do this you will have the open source ATI driver.

---

### Post by hanansela on 2010-12-16
Hi 
Thanks for the advice, at first i have used the open source driver but the display was blurry for small fonts in and images in PDF files and some delicate images in FireFox (like the staples that mark attachments in Gmail) I have switched to fgrlx and the result was a bit better but not perfect. however I have tried today to remove fgrlx and restarted with the restart button on the computer, not on the screen, the result is that i have now a pink screen with nothing on it, (i can still go to safe mode but i have no idea how to proceed)  can you advise my how to gain back any driver functionality? If I use the open source driver how can i setup it's parameters? 
Thank you

---

### Post by coffeecat on 2010-12-16
> **hanansela said:**
> however I have tried today to remove fgrlx

How did you try to remove fglrx? With the Additional Drivers utility or through a package manager? If the latter, the driver and associated stuff will not be removed completely.

> **hanansela said:**
>  and restarted with the restart button on the computer, not on the screen,

That was very inadvisable. You risk serious filesystem corruption by using the hardware reset button.

Back to removing the driver. Boot up in recovery mode and choose 'drop to root shell prompt' from the recovery menu. You will be presented with a # prompt. This is a root prompt. Be careful what you type and double-check everything before you press enter. You need to do the following if you didn't use Additional Drivers to disable the fglrx driver, but try this anyway.

At the prompt, run this command:

```
apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev 
```Now you need to remove the xorg.conf file generated for the fglrx driver:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.fglrx
```Make sure you get capitalisation right. X11 is capital-X-eleven.

Now:

```
reboot
```So long as you don't have filesystem corruption, the system will reboot using the open source driver. 

If you are getting fuzzy fonts, I suggest you experiment with the rendering settings in System > Preferences > Appearance > Fonts tab. Also, press the 'auto' button on the monitor. It may need tuning into your card output.

---

