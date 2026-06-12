---
title: "Nvidia Xorg Xserver Xgl Xset?"
date: 2009-08-05
forum: Hardware
---

### Post by Jack Hammer on 2009-08-05
I am having a lot of difficulty not installing my graphics card but configuring it. Everytime I install Nvidia 180 (or any) drivers either within Ubuntu or Mint upon reboot the desktop window manager (gdm) will not function.

My computer spec:

CPU: Intel Core 2 Duo Quad Core Q6600 (2.66Ghz)
RAM: OCZ 800mhz (2x2Gb)
HDD: Grub boot loader installation IDE 200Gb
          Main installation SATA 750Gb
          1x750Gb SATA
          3x300Gb SATA (RAID JBOD 900Gb)
GPU: 2x Nvidia GeForce 8800 GTS 640Mb (Not SLI'd)
VDU: 1x 24" 1900x1200 Dell
          1x 37" HDTV 1200x800 Samsung

Terminal output:

jackhammer@mint ~ $ sudo compiz --replace
[sudo] password for jackhammer: 
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: xterm 
no xterm found, exiting

At the moment I think that a lot of the files such as Xorg and Xserver have not been configured. Though I am new to Linux and for this I apologise. When it boots up it loads a terminal and no GUI and I am not capable of using linux command line very well.

I have had this problem for a week with no-one being able to assist me in any way. I am starting to think that no-one can help me.

---

