---
title: "radeon x1600 driver problems"
date: 2008-07-14
forum: General Help
---

### Post by whalogreg on 2008-07-14
I've recently installed ubuntu 8.04 and have been trying to install the ati driver for my graphics card so I can use the visual effects.On a fresh install, when the "extra" visual effects check box is selected, the screen goes white (the mouse pointer is still visible) for about one min and then returns to a normal view, with the "none" check box selected... I figured this is because the driver isn't updated...

In the restricted hardware drivers, the ati driver is listed and shown as "in use" but the "enabled" check box is not selected. When I do select it and restart (as it informs me to), I get past the black Ubuntu screen with the orange scroll bar under the logo, but the computer freezes on a black screen and does so every time i boot unless I run the recovery option on the boot menu and select the "Xfix" option...


I've searched high and low through these forums and tried every instruction to install the driver from ati's website, but none of them seem to work (including the directions from ati's site). With all of the commands I run in terminal, I eventually end up with an error stating "bash" or "command not found" or some other errors..

I used to run Ubuntu 7.10 on the same machine and did not find the same problem as I am having with 8.04.... any help would be great!

~Greg

---

### Post by tuxxy on 2008-07-14
This sounds interesting as I have the x1250 running here right now fine, also I plan to install a x1650 tomorrow but after seeing this post I am not so sure now =p

What is the output of this in a terminal?

```
compiz --return 
```

Also check your version and be sure you are not trying to use your old compiz from 7.10 as it will not work backporting like that make sure your version is up to date 0.7.4 or later

```
compiz --version
```

---

### Post by Execute_Method on 2008-07-14
I have an x1650 that had the same problem. I couldn't get the proprietary driver working.

The good news is the latest ati(radeon) driver works with our cards w/ 3d
Here's the links to install:

[http://www.phoronix.com/forums/showthread.php?t=9951](http://www.phoronix.com/forums/showthread.php?t=9951)

I am very happy with the way these drivers are working.

I get > 2300fps in glxgears, and can run many 3d games as well as compiz w/out a hitch. The best part is that by using these drivers you are supporting Open Source! :)

---

### Post by whalogreg on 2008-07-15
> **tuxxy said:**
> This sounds interesting as I have the x1250 running here right now fine, also I plan to install a x1650 tomorrow but after seeing this post I am not so sure now =p

What is the output of this in a terminal?

```
compiz --return 
```

Also check your version and be sure you are not trying to use your old compiz from 7.10 as it will not work backporting like that make sure your version is up to date 0.7.4 or later

```
compiz --version
```

Ok, so the output of "compiz --return" is as follows

greg@greg-desktop:~$ compiz --return
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c2 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '--return'

/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
metacity: Unknown option --return



And when I run it, my window tops (with the close/minimize/maximize buttons on top) disappear....

the output of "compiz --version" is as follows....


greg@greg-desktop:~$ compiz --version
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c2 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
compiz 0.7.4

---

### Post by whalogreg on 2008-07-15
> **Execute_Method said:**
> I have an x1650 that had the same problem. I couldn't get the proprietary driver working.

The good news is the latest ati(radeon) driver works with our cards w/ 3d
Here's the links to install:

[http://www.phoronix.com/forums/showthread.php?t=9951](http://www.phoronix.com/forums/showthread.php?t=9951)

I am very happy with the way these drivers are working.

I get > 2300fps in glxgears, and can run many 3d games as well as compiz w/out a hitch. The best part is that by using these drivers you are supporting Open Source! :)

Ok, I've tried this post as well... when i get to the command "$ chmod +x easy-drm-modules-installer" in the install process I run into this problem....

"greg@greg-desktop:~$ chmod +x easy-drm-modules-installer
bash: $: command not found"

I don't know... Should I just give up? Or am I doing something wrong?

---

### Post by whalogreg on 2008-07-15
Ok, I'm an idiot... but i realized that and figured out what i was doing wrong... I got to the end of the install and try to edit my "xorg.conf" I cannot save the file.. I get the error...

"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

Again, it's been a while since I've used Ubuntu or any other linux... Can I use another app instead of gedit to get access to save this file?

---

### Post by Execute_Method on 2008-07-15
It is likely the file did not download in your home folder. For instance if you're using firefox, it probably dloaded to the desktop, and by default terminal opens into your home dir.

make sure the "easy-drm-modules-installer" file is in your home folder.

---

### Post by Execute_Method on 2008-07-15
you need to run gedit as SU:

```
sudo gedit /etc/X11/xorg.conf
```

---

