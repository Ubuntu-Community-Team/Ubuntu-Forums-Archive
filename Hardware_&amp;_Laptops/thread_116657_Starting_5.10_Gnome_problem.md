---
title: "Starting 5.10 Gnome problem"
date: 2006-01-13
forum: Hardware &amp; Laptops
---

### Post by spock2263 on 2006-01-13
Hello to everyone!
I've an Acer Aspire 1693WLMi with ATI MOBILITY RADEON X700 PCI Express With 128MB VRAM.
I've installed Ubuntu 5.10 on my laptop and it boots ok, but just before the Gnome starts I get a black screen. I press Ctrl-Alt-F1 and I am prompted to login in a command line. I login, type my password and I get this: jim@ubuntu:~$ (jim is my username)
I was told many things to do but they had no, or weird results:
I typed 'sudo dpkg-reconfigure xserver-xorg', I reconfigured whatever I was asked to and then I got the same jim@ubuntu:~$
I typed 'more /etc/X11/xorg.conf' and I got a list of something like command choices I thing, I have no idea what to do next...
Also with ;sudo nano -w/etc/X11/xorg.conf I got a weird list...
What I am supposed to do?
Please help me if you have any ideas
Thank you all in advance

---

### Post by 23meg on 2006-01-13
As a temporary solution see if changing the driver indicated in "Driver" line in the "Device" section in your xorg.conf file to "vesa" helps. This driver is slow but compatible with many cards; install the ATI fglrx driver later if your card is supported (it most likely is).

---

### Post by spock2263 on 2006-01-13
Thanks my friend, I changed the 'ati' to 'vesa' and the Gnome started ok!
I have 2 more questions to ask:
1st, How can I adjust the screen resolution to fit to my widescreen? When I configured the xorg.conf file I choosed 1280x800 but now it gives me only 1024x768 so everything is streched to fit the screen.
2nd, I have a dial-up internet connection (I can hear laughs!), I'm going to have a DSL-Cable connection in a few days, but until then I cannot fin a way to connect to the Internet from Ubuntu

---

### Post by 23meg on 2006-01-13
For resolution problems consult to [this thread]("http://www.ubuntuforums.org/showthread.php?t=83973"). I suggest you resort to the vesa driver as a last resort though; if you want the best performance, install the proprietary ATI drivers if your card is supported. Do a forum/wiki search for instructions on how to do that.

For dialup, is your modem listed in System / Administration / Networking? If it's not it's most likely not supported; can you see its brand and model in System / Administration / Devices?

---

