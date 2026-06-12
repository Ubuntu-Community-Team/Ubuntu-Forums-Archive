---
title: "what does syslinux do?"
date: 2008-10-18
forum: General Help
---

### Post by flyingsliverfin on 2008-10-18
hi, I tried to make my USB stick bootable, using the instuctions at [http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install](http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install) 
but it didn't work. I'm trying to understand all of what its asking me to do, but I can't figure out what syslinux or mtools does. Can someone tell me?

thx

---

### Post by caljohnsmith on 2008-10-18
The way they use it in that tutorial, the syslinux command installs a boot loader to USB stick so it is bootable on start up. Have you seen the [Ubuntu help page about creating a bootable USB stick]("https://help.ubuntu.com/community/Installation/FromUSBStick")? I think it's more up-to-date than that tutorial you linked to. Let me know how it goes.

---

### Post by flyingsliverfin on 2008-10-19
ill check it out soon. I have to do homework first

---

### Post by flyingsliverfin on 2008-10-19
ok, I tried the unetbooting or whatever, but it didn't work. I also tried the manual approach, but it didn't work. I always end up in GRUB 0.91. All I did was use syslinux to make the usb stick bootable, then I copied the files in isolinux and install, along with vmlinuz and initrd.gz.Then I renamed isolinux to syslinux and isolinux.cfg to syslinux.cfg. all I did after that was boot from the stick. I got a old DOS looking screen except for GRUB. The top said GRUB version 0.91. 

Why doesn't it work???

---

