---
title: "Blank screen when trying to install 9.04"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by KayakJim on 2009-11-07
I am trying to install Ubuntu 9.04 Desktop 64-bit on my Toshiba Satellite P505-S8950 laptop, which has an ATI 4650HD video card. Shortly after I select the language the screen goes blank. I have even tried the install in Safe Graphics Mode but still had a blank screen after selecting the language.

Does anyone know how I can get Ubuntu 9.04 installed on my system?

---

### Post by KayakJim on 2009-11-08
Any help would be appreciated on resolving this.

All of the search results say to use Safe Graphics Mode but that isn't working.

---

### Post by wallaroo on 2009-11-09
I have this problem whenever clean installing ubuntu on my laptop (ATI video). My fix is to reduce the color-depth to 256 colors during the install phase.  This may work for you too.  When you are on the options screen and with 'Install' highlighted, press F6 to bring up the 'other' options, press ESC to close the pop-up screen and this will put you in edit mode for the boot options. Just type vga=771 (which will be appended to the end of the boot script). Then just press [Enter] to continue with the installation.  The addition of 'vga=771' sets video mode to 800x600 x 256 colors. If you prefer you can use 'vga=773' which sets it to 1024x768 x 256 colors.  This only sets the video mode for the installation phase.

---

### Post by KayakJim on 2009-11-09
> **wallaroo said:**
> I have this problem whenever clean installing ubuntu on my laptop (ATI video). My fix is to reduce the color-depth to 256 colors during the install phase.  This may work for you too.  When you are on the options screen and with 'Install' highlighted, press F6 to bring up the 'other' options, press ESC to close the pop-up screen and this will put you in edit mode for the boot options. Just type vga=771 (which will be appended to the end of the boot script). Then just press [Enter] to continue with the installation.  The addition of 'vga=771' sets video mode to 800x600 x 256 colors. If you prefer you can use 'vga=773' which sets it to 1024x768 x 256 colors.  This only sets the video mode for the installation phase.

Thank you wallaroo. I will give that a try tonight when I get home from work.

---

### Post by KayakJim on 2009-11-09
> **wallaroo said:**
> I have this problem whenever clean installing ubuntu on my laptop (ATI video). My fix is to reduce the color-depth to 256 colors during the install phase.  This may work for you too.  When you are on the options screen and with 'Install' highlighted, press F6 to bring up the 'other' options, press ESC to close the pop-up screen and this will put you in edit mode for the boot options. Just type vga=771 (which will be appended to the end of the boot script). Then just press [Enter] to continue with the installation.  The addition of 'vga=771' sets video mode to 800x600 x 256 colors. If you prefer you can use 'vga=773' which sets it to 1024x768 x 256 colors.  This only sets the video mode for the installation phase.

That worked perfectly! 

Thank you very much for the help. :)

---

### Post by wallaroo on 2009-11-10
Glad to help.
Now we'd better point those other poor souls with the same problem to this solution.

---

