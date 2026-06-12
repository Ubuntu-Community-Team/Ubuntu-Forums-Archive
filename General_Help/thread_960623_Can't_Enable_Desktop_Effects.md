---
title: "Can't Enable Desktop Effects"
date: 2008-10-27
forum: General Help
---

### Post by compucv621 on 2008-10-27
Hello,

I recently installed Ubuntu 8.04 on my main PC (64-bit) and my laptop (32-bit). The main PC is a custom built machine with an ATI 2600 HD Pro Video card, and the laptop is a Dell Latitude D830 with the Nvidia Quadro NVS 140M. I cannot enable desktop effects on either machine. How can I fix this problem? I know I should definately be able to do this on the desktop, because I had done it before when I ran 7.10 a long time ago.

Thanks in advance

---

### Post by cdtech on 2008-10-27
What desktop effects?

If your talking Compiz then check out this link....
[http://ubuntuforums.org/showthread.php?t=799070&highlight=compiz-check](http://ubuntuforums.org/showthread.php?t=799070&highlight=compiz-check)

---

### Post by Zer0d on 2008-10-27
Do you get any kind of error messages?
Maybe this webpage could be of any help [http://easylinux.info/wiki/Ubuntu:Hardy#How_to_enable_Compiz_Fusion_in_Ubuntu]("http://easylinux.info/wiki/Ubuntu:Hardy#How_to_enable_Compiz_Fusion_in_Ubuntu")

Your graphics drivers are correctly installed?
There is also written more about Graphics drivers here [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Graphics_cards_and_displays]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Graphics_cards_and_displays")


What happens if you open terminal and login with **sudo -s** and write **compiz**?

---

### Post by compucv621 on 2008-10-27
The only error message I get is "Desktop effects could not be enabled"

When I type that into the terminal, I get the following,

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:9589 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

I am only trying to enable the desktop effects built into Ubuntu.

Thanks

---

### Post by brandon88tube on 2008-10-27
Well your problem is probably because you need to install the restricted drivers for your ATI card. I think its called flgx or something. When you are done installing that, you should probably be able to enable effects.

---

### Post by compucv621 on 2008-10-27
After following the steps found on both of your links I got it to work on my Desktop, and I'm going to work on my laptop soon. Thanks a lot!

---

