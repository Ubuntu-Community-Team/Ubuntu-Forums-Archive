---
title: "ATI and a T400 :|"
date: 2010-01-14
forum: Hardware
---

### Post by BrandonBan6 on 2010-01-14
Man, I tell you I will never use linux on an ATI video card AGAIN!!! So much frustration, over nothing!!

Anywho, enough vent, down to the nitty and gritty. 

I am running 9.10 on a Lenovo T400 w/ ATI Mobility Radeon HD 3400 series graphics controller. 

I had things running smoothly, but I, in a very naive sense, blindly ran all ubuntu updates when prompted and after the reboot I noticed compiz would not load and I seem to be powerless in trying to get it to load. 

I'm not sure where to start with this post, so let me say this much. I tried to reconfigure the ATI drive with the following command.

```

:~$ sudo aticonfig --initial
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-10

:~$ sudo aticonfig --dtop=clone
Error: Options, e.g. --dtop and --desktop-setup, are not supported when RandR 1.2 is enabled!
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-11

```
And here is where I am stuck, I have no idea what RandR 1.2 is or how to disable it. Any pointers out there? 

Thanks for reading!

---

### Post by BrandonBan6 on 2010-01-19
Well, I managed to resolve this issue by starting from square 1. 

- Wiped out the install and put a fresh copy of 9.10.
- Followed manual instructions listed [here.]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually")
- I also had to write a script for my setup, sometimes I boot to docking station and want to use only an external monitor, if I set the video card up for that, I can't boot up the laptop by itself. So I have script that interchanges the xorg.conf file as needed.

---

