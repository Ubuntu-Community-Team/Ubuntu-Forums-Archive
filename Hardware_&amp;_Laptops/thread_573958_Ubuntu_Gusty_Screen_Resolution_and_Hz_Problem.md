---
title: "Ubuntu Gusty Screen Resolution and Hz Problem"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by Siwel on 2007-10-12
I am still very new to Ubuntu and Linux in general and apologize if I am not posting this to the right place.  I just installed the new release candidate of Ubuntu Gusty.  I am using a Dell UltraSharp 2007WFP 20" monitor with a Nvidia GeForce 8600 GT graphics card.  When I started up the computer for the first time, Ubuntu detected my monitor perfectly and had set the resolution to 1680 x 1050 @ 60Hz.  However, when I enabled the driver for my Nvidia card, the monitor defaulted back to 1024 x 768.  I went in to "Screens and Graphics" and changed it back to 1680 x 1050, but it would only let me do that when the monitor is at 62Hz. I would greatly appreciate any advice as to how to get my monitor to display at 1680 x 1050 @ 60 Hz with the Nvidia driver.  

Thanks

---

### Post by virtuallinux on 2007-10-12
Are you using the Ubuntu utility for changing display settings?  I know the Nvidia drivers also provide a nice gui for changing display settings.  Try typing ```
gksudo nvidia-settings 
``` into the command line and use that utility to customize your display.

---

### Post by Siwel on 2007-10-12
I was using the "Screens and Graphics" menu as well as the "Screen Resolution" menu.  I went to the NVIDIA x Server Settings and set the resolution to 1680 x 1050 and the Hz to "Auto".  Now when I go into "Screens and Graphics" it says "Model: Dell 2007WFP" "Resolution: 1680 x 1050 at 57 Hz".  The screen looks crisp and everything seems to be working properly, so is it ok that its not 60 Hz?  Is this bad for the monitor, or does it not matter since it is below the maximum of 60 Hz?  

Thanks for the help

---

### Post by cubeist on 2007-10-12
I have a similar issue on my laptop screen... the hardware spec say it runs at 1440x900 at 60Hz but I can only get 50Hz... I am not concerned though because it looks good and sharp.  I doubt it is harmful to the monitor, but I am not an LCD expert...

---

### Post by virtuallinux on 2007-10-13
In my experience, the higher the resolution, the lower the highest available refresh rate is.  Also, the refresh rates on LCD's generally don't go as high as CRT's.

---

