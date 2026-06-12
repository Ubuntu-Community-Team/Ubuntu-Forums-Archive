---
title: "Install Ubuntu without cd-rom or network"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by generic_idea_machine on 2008-12-05
Hi all, 

I have no network, cd-rom or floppy on this one spare laptop I have. The laptop cannot boot through usb and I have already tried the netboot option (Ubuntu installer)...but it's not working for me. 

What are my options here? I have heard that I can get a converting cable, which will allow me to hookup a desktop cdrom tray to my laptop. Can someone please help me out on this one? Which cable should I exactly be looking @ for this specific purpose. 

thanks!

---

### Post by Nathan Sweeney on 2008-12-05
> **generic_idea_machine said:**
> Hi all, 

I have no network, cd-rom or floppy on this one spare laptop I have. The laptop cannot boot through usb and I have already tried the netboot option (Ubuntu installer)...but it's not working for me. 

What are my options here? I have heard that I can get a converting cable, which will allow me to hookup a desktop cdrom tray to my laptop. Can someone please help me out on this one? Which cable should I exactly be looking @ for this specific purpose. 

thanks!

How old is this laptop?  What are the specs?  Are you even sure that it can run ubuntu?  I don't know what you mean by converting cable, convert to what?  I am assuming convert from IDE but I don't know to what it could convert to.

---

### Post by generic_idea_machine on 2008-12-05
> **Nathan Sweeney said:**
> How old is this laptop?  What are the specs?  Are you even sure that it can run ubuntu?  I don't know what you mean by converting cable, convert to what?  I am assuming convert from IDE but I don't know to what it could convert to.

It fairly old. I've had it for about 8 years now. It's a Toshiba Satellite 2600 DVD model. 
 The laptop has a win2k installation on it right now and it functions without any problems per say. When it comes to running Ubuntu, it exceeds the specs for minimum requirements. However I am planning to through Ubuntu Server/Lamp on it for a basic web-server/wiki/wordpress project and it should be able to handle the load. 

 As for conversion. I have no idea. All I need it to plug in a regular desktop DVD to the laptop. What kind of cabling do I need for this?

thanks!

---

### Post by girishsasikumar on 2008-12-05
I suggest you try installing it through the USB drive .... 
This definitely works, if ur system supports USB boot
[http://www.pendrivelinux.com/2008/11/04/live-ubuntu-810-usb-persistent-install-windows/]("http://www.pendrivelinux.com/2008/11/04/live-ubuntu-810-usb-persistent-install-windows/")

---

### Post by generic_idea_machine on 2008-12-06
> **girishsasikumar said:**
> I suggest you try installing it through the USB drive .... 
This definitely works, if ur system supports USB boot
[http://www.pendrivelinux.com/2008/11/04/live-ubuntu-810-usb-persistent-install-windows/]("http://www.pendrivelinux.com/2008/11/04/live-ubuntu-810-usb-persistent-install-windows/")

Thanks. My laptop does not support usb boot.

---

### Post by generic_idea_machine on 2008-12-24
Any other tips?

Is there a way I can partition the drive and then run the install from the HDD itself?

atm the laptop is running win2k pro

---

### Post by Nathan Sweeney on 2008-12-24
Would Wubi work in this case? [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

