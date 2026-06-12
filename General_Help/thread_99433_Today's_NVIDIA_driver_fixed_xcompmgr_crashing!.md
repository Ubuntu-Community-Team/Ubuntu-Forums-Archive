---
title: "Today's NVIDIA driver fixed xcompmgr crashing!"
date: 2005-12-05
forum: General Help
---

### Post by theh0g on 2005-12-05
Good news for all you eyecandy lovers...today's driver, released by NVIDIA (1.0-8174) finally fixes the famous crashing bug, where only mouse still works while everything else freezes. I've been trying it for last few minutes, shadows, fading, everything just works :) For details how to get xcompmgr working, search this forum as there are some awesome guides here. Good luck :KS

---

### Post by maruchan on 2005-12-05
Sounds cool...What's the best way to get this latest driver?

---

### Post by theh0g on 2005-12-05
Here is what I did:
1. download the driver from NVidia ([http://www.nvidia.com/object/linux_display_ia32_1.0-8174.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8174.html))
2. I did Ctrl-Alt-F1 and "sudo killall gdm"
3. and as a root I ran "sh NVIDIA-Linux-x86-1.0-8174-pkg1.run"
4. you also need to add this to your xorg.conf:
```
Section "Extensions"
        Option  "Composite"     "Enable"
EndSection
```
5. I rebooted and ran xcompmgr when I got to gnome.

That's it, the installer now also modifies your xorg.conf file so it actually works. I also noticed some minor speed increase from 3.500 to 3.600 in glxgear (which is basicaly not a benchmark tool, but if you run it on same machine, you can notice the difference).

And for xcompmgr, I'm using:
```
xcompmgr -Ccf -I 0.1 -O 0.1
```

I've added it to Session and it has to be ran BEFORE metacity loads, otherwise gnome won't load (at least on my machine).

---

### Post by pmj on 2005-12-05
It seems to have fixed this problem for me too. Thanks for letting us know!

---

### Post by daedalusman on 2005-12-05
Well I downloaded and tried to install these new drivers but it is telling me that I need to compile a kernel module. It first told me to get the correct version of g++ installed, which is did. Now its telling me that I need to make sure that I got the development files of libc for my distrobution installed and to make sure that cc is a valid complie command. I have searched in synaptic for these but can't seem to find the right one. Can someone point me to the what I need or provide some help, thanks.

---

### Post by chaumurky on 2005-12-05
If it's already installed go: **export CC=gcc-3.4** in the terminal, then try again.
 
EDIT: Seems to work with dual monitors as well (just dont run the config...).

---

### Post by daedalusman on 2005-12-05
[QUOTE=chaumurky]If it's already installed go: **export CC=gcc-3.4** in the terminal, then try again.
 
EDIT: Seems to work with dual monitors as well (just dont run the config...).[/QUOTE]


Well I did what you said and now I'm getting this message...

Unable to find the development tool `cc` in your path; please make sure
       that you have the package 'gcc' installed.  If gcc is installed on your
       system, then please check that `cc` is in your PATH.

What do you think?

---

### Post by chaumurky on 2005-12-06
you need to install **[COLOR=black]gcc-3.4[/COLOR]** and **g++-3.4**

Anyway, I spoke too soon. On reboot I X won't start:

Xorg.0.log:

> (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):      that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):      that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):      Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"

If I run the install script again I can sebsequentially start X so perhaps there is a module loading problem on boot. Any suggestions?

---

### Post by daedalusman on 2005-12-06
Yeah I figured that, I have both g++-3.4 and gcc-3.4, and I'm still getting that error. Man I would like to try this new drivers out, they are sounding pretty cool.

---

### Post by chaumurky on 2005-12-06
OK, I had to uninstall **nvidia-kernel-common **(that took** linux-restricted-modules-2.6.12-10-686** with it). Now it starts up fine on boot. I hope I didn't need any of those other restricted modules though. On first glance I don't think I do.

@ daedalusman, I found this from a post by **tseliot**:
[I]
 3) If the installer complains in this way:
 ...
 ERROR: Unable to find the development tool `cc` in your path; please make sure
 that you have the package 'gcc' installed. If gcc is installed on your
 system, then please check that `cc` is in your PATH.[/I]
[I]The user Reid has suggested this solution:

 To find out where 'gcc' is located I did:
 Code:

 which gcc


 which returned:
 Code:

 /usr/bin/gcc


 then I made a symbolic link to gcc called cc so programs trying to use 'cc' would get gcc, with this code:
 Code:

 sudo ln -s /usr/bin/gcc /usr/bin/cc

 Then try the installer again.[/I] 

Any help?

---

