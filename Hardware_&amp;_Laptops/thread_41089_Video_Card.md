---
title: "Video Card"
date: 2005-06-11
forum: Hardware &amp; Laptops
---

### Post by sorrowsbeyond on 2005-06-11
I am fairly new to Linux/Ubuntu and I need to know what kind of video card to get.  the one I currently have only allows 800x600 res.  I have both PCI and AGP slots on the mobo.  It's a fairly new mobo and CPU, not even a month or so old.  I cannot find any drivers for the vid card I currently have so I need a Linux/Ubuntu friendly vid card that's reasonably priced.  If you have any suggestions, I'll look on here every so often, or you can either IM me or e-mail me.  My AIM u/n is sorrowbeyondhere and my e-mail is [email]sorrowbeyondhere@gmail.com[/email].  Thank you.

---

### Post by codejunkie on 2005-06-11
first what kind of video card is it that you can't find the driver for.
and second my recomendation is buy an NVIDIA card they seem to have better support for linux than other cards but thats just been my experience.

---

### Post by Hokputooy on 2005-06-11
I'd say go with an agp ATI or nVidia card, but check [here](http://www.linuxcompatible.org/compat.php?cat=hardware&sort=All&idx=0)   to be sure if it's compatible.

---

### Post by sorrowsbeyond on 2005-06-11
The video card is a Cirrus Logic GD5462  I looked and could not find the drivers anywhere what-so-ever.  Also, I just want to make sure about this, how is it that you install the driver.

---

### Post by codejunkie on 2005-06-11
you could try the vesa driver it might work but i doubt that 3d support will be all that great but by using it you should be able to set the resolution to something other than 800x600.

---

### Post by sorrowsbeyond on 2005-06-11
The thing is, I'm a dumbass and don't know how exactly to do that :?  :-#

---

### Post by kleeman on 2005-06-12
According to the following site cirrus is the driver you need:

[http://www.linux.com/howtos/Hardware-HOWTO/video.shtml](http://www.linux.com/howtos/Hardware-HOWTO/video.shtml)

To configure X use xorgconfig at the command line and follow your nose  :smile:  :smile: . You may also wish to search this forum for more straighforward HOWTO advice on video configuration

---

### Post by codejunkie on 2005-06-12
[QUOTE=sorrowsbeyond]The thing is, I'm a dumbass and don't know how exactly to do that :?  :-#[/QUOTE]
you can manualy edit the xorg.conf file by opening a terminal and typing sudo gedit /etc/X11/xorg.conf just find the section that says driver and replace what's listed there with "vesa". another option is from the terminal type sudo dpkg-reconfigure xserver-xorg in the first section it will give you a list of modules/drivers to load choose vesa or if a module is already listed there for your card use it you can usually just press enter through the rest of the configuration because most things are autodetected but it gives you the option to change settings if you want you should also backup your xorg.conf file just incase something goes wrong with 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup hope this helps.

---

### Post by sorrowsbeyond on 2005-06-13
ok, I checked and "vesa" is already in there.  I'll just need to buy a new video card.  Thanks for the help though.

---

