---
title: "Black screen on ubuntu jaunty AND karmic on gateway laptop"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by unchatvert on 2009-11-05
Hi,
I just bought a new laptop, a Gateway NV5813h, and tried installing ubuntu Karmic 64 with the install CD. As soon as I choose install on the boot menu, the screen shuts and restart with no image at all... all black.
I tried the safe mode with the same result, also tried installing Jaunty.
I plugged another screen on the laptop and could see everything correctly, successfully installing Karmic. But I cant have any image on my laptop's screen... can you help? Thanks!

Gateway NV5813h
Processor Intel Core 2 Duo Processor T6500
Processor Speed 2.1GHz
Memory 4GB DDR-2 SDRAM
Graphics Chipset Mobile Intel GMA graphics 4500M
Video Memory n/a
Display 15.6" Widescreen LCD w/ Ultrabright

---

### Post by unchatvert on 2009-11-06
bump...
I think it might be related to the graphic chipset... but unfortunately, I'm not the best when it comes to computers. Any help? I'd hate to have to go back to windows...

---

### Post by KayakJim on 2009-11-08
You are not alone. I have an ATI 4650HD video card and am having the same problem.

---

### Post by Skilly on 2009-11-09
+1 standard grpahics on centrino chip (single core)

---

### Post by KayakJim on 2009-11-10
> **wallaroo said:**
> I have this problem whenever clean installing ubuntu on my laptop (ATI video). My fix is to reduce the color-depth to 256 colors during the install phase.  This may work for you too.  When you are on the options screen and with 'Install' highlighted, press F6 to bring up the 'other' options, press ESC to close the pop-up screen and this will put you in edit mode for the boot options. Just type vga=771 (which will be appended to the end of the boot script). Then just press [Enter] to continue with the installation.  The addition of 'vga=771' sets video mode to 800x600 x 256 colors. If you prefer you can use 'vga=773' which sets it to 1024x768 x 256 colors.  This only sets the video mode for the installation phase.

This helped me get installed although the screen is not very readable.

---

