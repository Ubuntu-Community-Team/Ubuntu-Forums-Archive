---
title: "ubuntu &amp; pci express/ nvidia 6200 Le does not work!"
date: 2006-01-21
forum: Installation &amp; Upgrades
---

### Post by aterreno on 2006-01-21
I have a problem with the post-installation of ubuntu, the system freezes showing "Starting hotplug subsystem".

May this due to the pci express architecture? 

I have an  "nVidia GeForce 6200 LE" Connected with pciExpress and 0 Agp ports on my pc... 

The full specs of this Desktop is here: 
[http://support.packardbell.com/uk/mypc/?PibItemNr=PB34213001](http://support.packardbell.com/uk/mypc/?PibItemNr=PB34213001)

nVidia GeForce 6200 LE/TC 64MB (256MB Total) VGA + TV-Out 
Name: nVidia GeForce 6200 LE/TC (NV44) PCI Express
Type: 2D/3D Video card

Sunshine (GA-8I915PM Ver 1.1) 
Name: Sunshine (GA-8I915PM Ver 1.1)
Type: µATX motherboard
Manufacturer: Gigabyte

---

### Post by beerorkid on 2006-01-23
I have no real clue, but.  I have a 6800 gs PCI e vid card and have not gotten it to work yet.  My friends at work had a few suggestions though.

-get rid of the frame buffer.  I saw that there is a way to do something with the frame buffer when you hit the function keys while installing ubuntu.

- disable DRI

They told me that everything is compiled with AGP stuff and it will mess up an install with a PCI e card.

I am going to mess with this a bunch tonight and will post if I figure anything out.

Or any other suggestions would be welcome.

---

### Post by simple on 2006-03-01
i don't think it has to do with the pci-e architecture, because i am having the same exact problem, and my card is PCI.. must be the 6200 card itself? after a month did you get it to work? what did you guys do..?

---

### Post by beerorkid on 2006-03-01
hmmmmm.....

Well I was having issues with the driver in xorg.conf.  When I set it to "vesa" I was able to get in.

Then I installed the nvidia drivers and it is working good now. video that is.

Many other issues though   sigh...

I guess most of my issues are cuz the chipset is not in the kernel or something.

here is a link with my issues getting the vid card to work: [http://ubuntuforums.org/showthread.php?t=120863](http://ubuntuforums.org/showthread.php?t=120863)

---

### Post by simple on 2006-03-01
dang :( maybe i'll just stick with the onboard graphics.. :mad:

---

### Post by KenzoIX on 2006-03-05
[QUOTE=simple]dang :( maybe i'll just stick with the onboard graphics.. :mad:[/QUOTE]
Try to disable the sound card. Yes, it sounds strangle, but i work for me :D
P/S: my integrated VGA is ATI Xpress 200, but I think this should work for you :P

---

### Post by tseliot on 2006-03-05
[QUOTE=simple]dang :( maybe i'll just stick with the onboard graphics.. :mad:[/QUOTE]
Boot in Recovery mode (as soon as you turn on your computer choose it from the Grub menu)

nano /etc/X11/xorg.conf
Get to the Section Device

Set the driver to "vesa" instead of "nv"

CTRL+O to save
CTRL+X to exit

then
sudo reboot

You should be able to see the Desktop Enviroment.

Then install the Nvidia Drivers as described in my guide

---

