---
title: "Installing on a Dell Optiplex 320"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by timmahoney on 2009-02-22
Hi All - first time poster here. 

I searched high and low for instructions on this one, but couldn't find anything, so I sort of figured it out and I thought I might share. 

When I tried to install Ubuntu 8.1, 8.04, Xubuntu 8.04, Live CD, Alternate, etc versions on this new Optiplex I got, It would boot the CD, install the OS fine, but then when reboot to start the new system, it would hang directly after GRUB with a flashing cursor. I tried changing GRUB options, to no avail.

I was very upset. :(

I found, however, that what I needed to do was the following:

[LIST=1]
[*]Use the Ubuntu 8.04 Alternate Install CD.
[*]On booting the installation, hit F6 to enter boot options, and put at the end: acpi=off pci=nomsi
[*]During the installation, after the installer finishes installing the various packages, it tries to install GRUB. Do NOT let it do this. hit escape until it brings you back to the Install order list. Select "Install LILO as your bootloader," and install LILO to your Master Boot Record (MBR)
[/LIST]
That's about it. I have it working correctly now, and I'm doing the updates to bring it up to current. 

My thanks to everyone who works on this OS. I hope this helps someone out!

---

### Post by rezponze on 2009-04-13
hi timmahoney!

Thanks a lot for your post. It has been really useful. I had to install ubuntu 8.1 on three Dell Optiplex 320 and I was freaking out because I couldn't understand what the hell was happening. 

I followed your instructions and now finally I'm installing the Ubuntu distros on my lab. 

Thanks again!  

Rez

---

### Post by mrq201 on 2009-04-13
Im really a newbie to Linux.  Is grub the screen where you enter in your user name and password?

After i enter in teh user name and password, the screen sort of hangs, where I can only see the mouse cursor and the background wallpaper.   If i follow timmahoney's instructions, do you think it will solve my problem?

---

