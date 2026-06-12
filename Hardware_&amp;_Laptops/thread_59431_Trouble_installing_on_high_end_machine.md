---
title: "Trouble installing on high end machine"
date: 2005-08-24
forum: Hardware &amp; Laptops
---

### Post by Rapture on 2005-08-24
I'm new to Ubuntu and have searched for a solution to my problem and haven't been able to find one, I may be blazing something of a new trail here and here's why:

I have an nVidia 7800 GX PCI-E video card driving an Apple Cinema 30" LCD display which has a native resolution of 2560x1600 (honest).  When I install clean Ubuntu onto my second hard drive and boot I get the login screen, drum greeting, etc.  However, when I enter my username and password and press ENTER the login begins but then the graphics corrupt and the machine hangs.  I can't use ctrl-alt-f1 to get a console.  I can, however, get a console if I don't try to login to X first.  So...

Obviously the first order of business should be to get the latest nVidia drivers going on this monster but I'm unable to do that just yet because during install Ubuntu didn't recognize my Broadcom 5751 PCI-E gigabit network card that's built onto the Dell GX280 motherboard.  The tg3 driver apparently works with it but I can't figure out how to get it going manually.  When I do "dmesg | grep eth" I get "tg3: Could not obtain valid ethernet address, aborting."  Any ideas on how to fix this?

Rapture

---

### Post by s_p_a_r_k_y on 2005-08-24
yea give me the machine : ) ... and the monitor

maybe try the latest and greatest stable kernel, 2.6.12 i think. What drivers are you using for the nvidia card? Its weird that gdm starts up but not gnome once ya try to login. Have you tried another window manager? fxce... fwm... kde?

---

### Post by Rapture on 2005-08-24
Hey sparky, thanks for the quick response.

I'm not frustrated enough to give the machine away yet.  :)

It's a clean install and I'm not much of a linux user yet.  It's one reason I chose Ubuntu...  So it's X, Gnome, etc.  The same setup works fine on a clunker machine (I'm typing on it now in ubuntu).  I can't download anything yet since I don't have networking...  so it's stock stuff.  Could you point me to a resource on how to, from scratch and via the command line, install a nework card driver?  In this case tg3.

Rapture

---

### Post by tseliot on 2005-08-24
I dont' know how to help you with your network card. However after you solve this problem you can have a look at my guide if you want to install NVIDIA drivers:

[http://ubuntuforums.org/showthread.php?t=57368&page=1](http://ubuntuforums.org/showthread.php?t=57368&page=1)

---

### Post by Rapture on 2005-08-24
tseliot,

I've successfully used your guide to install nVidia drivers onto my low-end machine and it went pretty smoothly.  I did have to download and recompile the kernel to get it working though.  For some reason just the headers didn't work...

I just need to bootstrap my network card so I can get Internet connectivity working, then I can do the same thing on this Windows machine.

Rapture

---

### Post by Rapture on 2005-08-24
Back to Windows for me then.  :(

Rapture

---

### Post by s_p_a_r_k_y on 2005-08-24
you could get a cheap network/wireless card for 20 bucks...usually anything 1-2 years old should be supported. I've had lots of success with linksys devices.

---

