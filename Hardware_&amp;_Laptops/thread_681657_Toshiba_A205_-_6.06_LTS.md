---
title: "Toshiba A205 - 6.06 LTS"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by coladons on 2008-01-29
Multiple problems.  Recently purchased a Toshiba A205 (with Vista pre-installed).  Shrank the partition in half in preparation to install Ubuntu 6.06 LTS (which I have on my other computers at a remote site).  When I put the Live CD in, I got an Xserver error so I attributed that to the display chipset which is an Intel Mobil 965 Express Chipset Family.  Decided to download the 7.10 iso and that went fine.  Now the problems.  I don't have a functioning Linux system at this location other than 6.06 on old hardware that does not have a DVD burner.  So I need to burn the ISO image using Vista.  However, it looks like Vista does not support burning ISO images so I need a Vista program to download to accomplish that.  Assuming I find one of them, I would like to know if the 7.10 ISO image will support the display driver in my Toshiba.

Option two would be to somehow get 6.06 installed maybe in text mode (can't get past the Xserver problem) and then install the display drivers (looks like one is available).

Anybody have any suggestions?

Steve

---

### Post by Yellow Pasque on 2008-01-29
When you use the LiveCD, can you get to a terminal? (Try pressing Ctrl+Alt+F1). If your internet works, you should be able to use the two commands below to update your video driver and reconfigure X (choose the "intel" driver).

The other option is to use the 6.06 alternate install CD. That way, you can use the text installer. 

To get your display working, I imagine you would just need an updated video driver, and then reconfigure xorg.conf, so:
```
sudo apt-get install xserver-xorg-video-intel
sudo dpkg-reconfigure -phigh xserver-xorg
```
If you're using the LiveCD, you would then need to find some way to kill and restart X. (Ctrl-Alt-Backspace and then startx command?)

---

### Post by coladons on 2008-01-30
When using the LiveCD, after the Xserver fails, it drops me into terminal mode.  However, at this time, nothing has been installed on the PC and consequently I have not been able to configure the internet.  So I am at a loss as to how I can proceed with the LiveCD when I haven't been able to install anything.

Thanks.

Steve

---

### Post by Yellow Pasque on 2008-01-30
If you're running off a regular wired LAN and the LiveCD has the driver for your LAN chip, your internet may actually work "out of the box" without anything needing to be configured or installed. Try it.
Edit: I guess some wireless chipsets/connections may work too, but it's not as likely.

---

### Post by coladons on 2008-01-30
Unfortunately I am not running off a wired LAN and my only internet connection is dial-up (yet to be configured in Ubuntu) although I am having Verizon fios installed soon.  So right now, I'm kinda dead in the water here.

Thanks for your suggestions.

Steve

---

### Post by Yellow Pasque on 2008-01-30
You could always download the latest vid driver from packages.ubuntu.com and load on a CD or floppy.

---

### Post by coladons on 2008-01-31
I took a look there and the xserver-xorg-video-intel driver is not available for Dapper.  I think my best shot here is to download an ISO burner for Vista and burn the 7.10 iso image and install that and then just wait for the next LTS release to come out.

Steve

---

### Post by coladons on 2008-01-31
Problem Solved

1) Downloaded the ubuntu-7.10-desktop-i386 iso image from ubuntu
2) Downlaoded imgburn v2.3.2.0 from [www.imgburn.com](www.imgburn.com)  ## this is the free utility that allows you to burn iso images with Vista.  The utility is very easy to use.
3) Burned the iso image to a CD-R CD.
4) Booted the LiveCD.

Everything worked.

Thanks for all the assistance.

Steve

---

