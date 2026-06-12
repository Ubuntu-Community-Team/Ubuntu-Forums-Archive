---
title: "Intel Graphics card not recognized 12.10"
date: 2013-01-20
forum: Hardware
---

### Post by HomeTheaterGuy on 2013-01-20
lspci -v | grep -i vga output:  VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)  System Settings states: Driver - Unkown Experience - Standard  Tried rebuilding the repository and went to intel site and could only find this: sudo apt-add-repository ppa:glasen/intel-driver sudo apt-get update sudo apt-get install xserver-xorg-video-intel  Seems to be addressing 12.04. Interesting side note: when I removed unity and installed Gnome 3 (on my first attempt before blowing out and reinstalling) I could get the driver to load using the aformention set of commands. Any suggestions to get my video card driven properly?

---

### Post by Cheesemill on 2013-01-20
The Intel graphics drivers are included in a standard Ubuntu installation, you are already using them.

There is, however, a bug in Systems Settings which causes it to display the graphics as 'Unknown' even when you are using the correct drivers. This can be easily fixed by installing the mesa-utils package.

---

### Post by HomeTheaterGuy on 2013-01-20
Thanks, that seemed to correct the rendering issue! I still have one more issue and I'm sure it is something simple that I missed... When Ubuntu boots up, it doesn't seem that the picture is correct; everything is bunched up into the top left corner. Once I login, it's corrected and everything is displayed properly.... Something I have to do to the boot file?

---

### Post by Mark Phelps on 2013-01-21
Unless you want to spend hours hacking away at details in the GRUB config file -- and risking breaking it such that you can't boot anymore -- I would suggest you look into installing Grub-Customizer.

When  you run that, you will get a menu-driven app that will allow you to set resolution sizes for the GRUB boot screen.

---

### Post by wozniak on 2013-03-29
> **Cheesemill said:**
> The Intel graphics drivers are included in a standard Ubuntu installation, you are already using them.

There is, however, a bug in Systems Settings which causes it to display the graphics as 'Unknown' even when you are using the correct drivers. This can be easily fixed by installing the mesa-utils package.

Thanks... worth searching....! :D

---

