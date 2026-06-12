---
title: "Live CD won't boot with geforce 8400 gs - Segmentation Fault"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by AeroTITAN on 2008-12-30
I recently installed a Geforce 8400 gs with 512MB graphics card.  I am now trying to install Ubuntu.  I have the Live CD for 8.04 and 8.10.  The Live CD's check out fine because I have installed both systems before as a second partition with XP SP3, but without the graphics card physically installed (I have an integrated graphics card with my motherboard).  

The cd will boot to the main menu but if I click install or even boot, the screen displays a lot of output ending with a segmentation fault.  I cannot boot the cd in order to install the driver for the graphics card.

I have tried "vga=normal" and "noload=intel_agp noload=agpgart agp=off" found from another forum post.

I have searched the forums regarding graphics cards updates, but each one already assumes you can boot up with the graphics card already installed.  Mine won't boot.  Because it won't boot, the driver installation guides won't see the hardware the installation of the driver fails.

Here's my system:
HP Paviliion a749c
Geforce 8400 gs with 512MB (PCI)
2.5GB RAM
HP w1907 (1440x900)
Dual boot with XP and the card works brilliantly there

Any ideas?  I am always on here so I can respond in a matter of minutes.

---

### Post by AeroTITAN on 2008-12-31
So I've been working on this since my last post.  Noob comes to mind now.  My computer has a built in video card.  I have actually been pulling out the modem.  I have to laugh when I think about that.

Anyway in the BIOS I have the option of choosing PCI, PCI-Express, or Onboard.  So far I have no luck running the LiveCD using my new PCI card.

I have "successfully" done an Envy install of my Nvidia card.  I say "successfully" because it installs without errors (both envy and the drive).  However, I still cannot boot into 8.04 with the BIOS set at PCI.  So then I tried the restricted driver in the Hardware Drivers section.  It recognized my card and eventually stated it enabled, however the splash screen freezes.  If I prevent "quiet" and "splash" during Grub boot, I still could not logon.

Now that realize I can boot using BIOS Video "Onboard" and still have the PCI card installed, I'm trying a fresh install hoping something will be enabled because my PCI card is installed.  I saw that if you press F6 twice at the LiveCD menu there is an option of using a Driver Update CD.  I have been trying to find out what that is.  Does anybody know?  I also tried the "Use Free Software" option, but no joy.  We'll see how the fresh install goes.

---

### Post by compabeto on 2009-02-05
In case you are still interested. You are not alone.

[http://ubuntuforums.org/showthread.php?t=1056369]("http://ubuntuforums.org/showthread.php?t=1056369")

---

