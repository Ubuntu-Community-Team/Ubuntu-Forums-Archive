---
title: "Dell Optiplex GX260 won't boot with PCI matrox graphics card"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by megagram on 2007-07-03
Hey guys. I have a Dell GX260 Optiplex machine with a Matrox Millennium G450 Low-profile PCI graphics card plugged in to one PCI port. Whenever I change the default video controller in the BIOS from "Onboard" to "Auto" in order to select the PCI card and then I boot into Ubuntu, it always crashes when it starts to Load Hardware Drivers.  I tried installing with an alternate install but whenever I try and boot up with a GUI it crashes like this.

Anybody have any ideas? Thanks!

Graham

---

### Post by craig.ciurca on 2007-08-06
I'm having the same problem with my gx260 and an ATI radeon 9250 card.

I wish the onboarrd video card could be completely disabled.  I haven't figured that out yet.  I got the  machine for free, because someone tried upgrading from windows 2000 to xp and couldn't find a driver for the integrated display adaptor.  Well, I did find one, and got it into XP, and it works fine.  

Now, I just want to make my machine a dual boot machine, and linux wants to use the onboard card as the default xserver adapter, and when I reboot after install, I just get errors too.

Anyone else have a clue???

---

### Post by aquinashub on 2008-03-06
What is it with these GX260's? I've got one too, with a Radeon 9250 PCI, but alas, my system boots to the splash, then hangs at about the one-fifth mark on the progress bar.

I've followed several How-To's for the ATI card, so for craig.ciurca, I'd say check out the Sticky on installing the linux ATI drivers under the Multimedia and Video forum section. There are two, beware: One is supported by the ubuntu community and can be found in the repositories, the other you must manually install from ATI's binaries. Try that out and let me know how it goes, since you and I have the same setup..

For you megagram, I wish I could help a little more.

I'm not sure what your level of experience is, but I'm like a... a sort of noob... so, using your onboard setup first, make sure the card is being detected, such as:

lspci

Get the latest drivers for your card, ie: [http://www.matrox.com/graphics/en/corpo/support/drivers/driverInfo.php?id=143]("http://www.matrox.com/graphics/en/corpo/support/drivers/driverInfo.php?id=143")

install that, then after making a backup of your xorg.conf file, edit your xorg.conf file so it says under the "device" section, beside "driver", the name of the new driver - this, of course, if the matrox driver install didn't already set that up for you.
Reboot and try again!

Hope that helps you guys! I'm still looking for a solution myself!

aquinashub

---

### Post by luvit on 2008-03-13
I upgraded my bios and used the alternate ISO imgage! I have pure success and optimal video settings on my GX260! :)  Heres what I did:

I downloaded the alternate ISO and it solved my video problem on my GX260.  I now can leave my BIOS at 256MB Video RAM _and_ have 1024x768 75Hz refresh rate.

For reference I viewed my display settings:
  System>Administration>Screens and Graphics - Graphics Card Tab - Driver: intel Experimental modesetting driver for l...

Before I installed Ubuntu I upgraded my BIOS which may have contributed to my fantastic video success. You can get the BIOS update from my blog. Lemme Know!

---

