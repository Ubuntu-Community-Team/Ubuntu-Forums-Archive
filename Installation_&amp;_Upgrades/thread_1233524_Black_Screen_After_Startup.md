---
title: "Black Screen After Startup"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by bennettron on 2009-08-06
I've been running ubuntu successfully on my old Toshiba laptop for nearly two years.  Recently, my home theater pc's hard drive crapped out and I decided to install Ubuntu on it.  Unfortunately, my video card needs reconfigured to be able to display the GUI.  I had to install the OS via the alternate text installation.

Now, upon startup, I see all the text based loading screens as well as the initial loading screen for ubuntu only and then I hear the African drums, so I know that the OS is installed.

After reading a few forum postings on the black screen topic I tried reconfiguring xorg, which seemed to be the resounding piece of advice given.  Lucky me, my version of xorg will only allow me to reconfigure my keyboard...  My keyboard has been configured about 10 times now, should be working just fine.

I've been theorizing on the possibility of loading the nvidia drivers from a cd burned from my laptop (which is being used to make this post).  Can I do that from the command line (which is the only thing I can get to), and if so how?

Thank you in advance for any advice that can be given.


My computer is: 
HP Media Center PC M8530F
AMD Phenom 9550 X4 64-bit
nvidia GeForce 9300 GE

---

### Post by bennettron on 2009-08-07
Ok, another possibility if someone can please walk me through how to do it.  If I can somehow choose VESA as my video driver (remember xorg only allows me to configure my keyboard) that will allow me access to my desktop and I can then install the nvidia drivers.  I've read some things about xconf, but I'm not really sure what to do with that.

Help me Obi Wan Kenobi... You're my only hope...

---

### Post by darktruth2 on 2009-08-07
Hey there,

Sorry you are having trouble with your display. I have been there and done that but hopefully this helps you get your nvidia drivers installed through the command line as you said.  From the command line type these commands and press enter.

apt-get install module-assistant nvidia-kernel-common

m-a a-i nvidia

apt-get install nvidia-glx

Let me know how if that works for you and we can go from there.  CHEERS!

---

### Post by bennettron on 2009-08-07
Will that pull it from a cd, or direct from the internet? Thanks

---

### Post by bennettron on 2009-08-07
Ok, so the middle command line that you gave me failed, but I was able to install the nvidia driver (nvidia-glx-180) from the command line.  Upon rebooting I was again greeted by the black screen after ubuntu loaded.

Is there a way that I can configure my video settings from the command line that does not involve using xorg?  Like I said before, it only allows me to reconfigure my keyboard.

---

