---
title: "Desktop Won't Appear"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by Admiral Sauce on 2006-02-15
Greetings. I am very new to Linux. This is my first experience in fact. I've installed Ubuntu, resolved the driver conflict with my nVidia card, have finally gotten a visial past the kernal load screen. I can see the logon, I can sign in. After logging on, the screen goes to all brown, the expected background, however, that's all. A full brown screen, with my mouse, which I can move around.

Suggestions?

---

### Post by linear on 2006-02-15
Most likely the Ubuntu Date Bug:

[https://wiki.ubuntu.com/UbuntuDateBug](https://wiki.ubuntu.com/UbuntuDateBug)

---

### Post by thepocketdrummer on 2006-02-15
I had this same exact problem when I first installed Ubuntu.

Hit ctrl+alt+F1
Then it should ask you to log in. Type your username (if asked) then your password. (Don't be alarmed if nothing shows up when you type. It just doesn't show the letters)

After that, type in (exactly)

```
sudo nano /etc/X11/xorg.conf
```

Remember, it is case sensitive, so the capital X must be capital or it doesn't work.

Part of the way down it will say either "nv" or "vesa". If it is "nv" (like mine was), change it to "vesa". If it is "vesa", change it to "nv".

After you do that, press ctrl+x
say y to the next part, then hit enter.

After that, type in
> sudo reboot

and that should do the trick.

Lemme know if anything goes wrong. (I'm still kinda new to this too, lol)

---

### Post by BobbyWatson on 2006-02-18
I tried to install Ubuntu 5.10 on my PC today and I also ran into this brown screen problem.

The installation process went very smoothly. I can start the PC and get to the login screen. I input my username/password, and then I get this brown screen with the mouse arrow in it. The mouse responds, I can get a console using CTRL-ALT-F1 just fine, but even after an hour the desktop still won't appear. 

I have an ATI Radion 9800 card, not an nVidia. I tried using VESA instead of ATI in the X.org configuration, but that didn't change anything. 

The date is correct, so this is not related to the Ubuntu date bug.

Network is working, I can ping my other computers.

Is there anything else I could try? 

In case they are needed, here's the specs for my computer :

AMD Athlon 64bit 3700+ (yes, I am using the 64bit edition of Ubuntu)
1 Gb RAM
ASUS motherboard
ATI Radion 9800 AIW video card (128 Mb of VRAM)
Generic PS2 keyboard and Logitech USB optical mouse
LG DVD +/- RW

(For some reason, trying to boot with with Live CD gives the same brown screen.)

---

### Post by MachineBucket on 2006-02-18
Hi, I'm new to linux and I'm getting the same problem. Ubuntu installed fine. Ubuntu boots, gets to the login screen, I login. Then I get a brown screen with one garbled image where i believe a little status box should come up showing the apps loading. My mouse still reacts to my input, but the ctrl+alt+F1 wont work. Any help would be great, as I know pretty much know nothing about linux distros at this point. Thanks.

Ubuntu 5.10 32 bit
Asus A8N SLI Deluxe
AMD Athlon 64bit 4000+ San Diego
2 gigs ram pc3200
Western Digital 320 gig 16mb cache SATA2 HD
eVGA 7800 GT 256mb pci-e (overclocked)
Sound Blaster Audigy 2 ZS Platinum

---

### Post by KansasJoe on 2006-02-18
I had a similar problem when i installed and I have nvidia.... here's how i got it working

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo apt-get install linux-restricted-modules-`uname -r`
(I know u can do all of the above on one line but I like to do them individually)

sudo nano /etc/X11/xorg.conf

Then scroll down until you see Video Card section and make it look exactly like what you see below -DO NOT CHANGE IDENTIFIER 

Section "Device"
Identifier "Whatever it says here do not mess with and leave alone even if it's ur integrated card"
Driver "nvidia"
BusID "PCI:1:0:0"

Then hit CTRL+O to save
CTRL+X to exit

sudo startx

I'm not sure about the ati cards...problem i had was my BusID was showing PCI:0:2:0 so I changed it to the above settings and it works perfectly....I'm no pro at this but it worked for me

---

