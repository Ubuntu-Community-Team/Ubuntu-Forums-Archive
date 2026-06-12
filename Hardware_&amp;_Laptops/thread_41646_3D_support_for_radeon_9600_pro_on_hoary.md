---
title: "3D support for radeon 9600 pro on hoary"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by tristan.buckmaster on 2005-06-14
hi,

I have spent ages trying to figure out how to get 3d support for my radeon 9600 pro to work with the new fglrx drivers to no avail.  I have tried everything.  The driver loads fine, but when I try to open an opengl program, it freezes after 5 seconds or so.  I then lose screen input depending on whether I have Option "UseInternalAGPGART" "no" or Option "UseInternalAGPGART" "yes".  I have since found on the ubuntu wiki that the 9600 series is not supported ([http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards)](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards)).  Has anyone found any work around to get the radeon 9600 series cards working on hoary?  It used to work fine on warty.

Thanks,

Tristan

---

### Post by Curlydave on 2005-06-14
Go to the ATI website, and download the installer. Run the script. Edit /etc/X11/xorg.conf, and find the "Device"section. Change "ati" to "fglrx". Reboot and you're set.

---

### Post by tristan.buckmaster on 2005-06-15
I tried that and I got the same problem.  I have tried three different methods.  I have tried the debs, the rpm and the installer.  I get the same problem with all three methods.  Have you got a radeon 9600?

---

### Post by kleeman on 2005-06-15
I have a Radeon 9600 Mobility on a laptop and it works great with the latest ati drivers. I am using Hoary. I noticed with earlier versions of the driver that lockups occurred often. Maybe you have a version of the 9600 which still has buggy driver support....

---

### Post by tristan.buckmaster on 2005-06-15
2D support works fine, although after about 5 seconds after running an opengl program the screen freezes.  The screen then looses it's signal if I have UseInternalAGPGART is set to yes or just freezes without loss of signal if UseInternalAGPGART is set to no.

---

### Post by Mau on 2005-07-12
[QUOTE=kleeman]I have a Radeon 9600 Mobility on a laptop and it works great with the latest ati drivers. I am using Hoary. I noticed with earlier versions of the driver that lockups occurred often. Maybe you have a version of the 9600 which still has buggy driver support....[/QUOTE]
 Sorry for bringing this thread back up, but I was curious if anyone had any success with the ATI Radeon 9600?  I have that card (mobile version) and I am considering installing Ubuntu.

---

### Post by kleeman on 2005-07-12
I have that card on Hoary and the latest ati drivers (installed manually, although the standard Hoary ati drivers also appear fine). I have used it for 3 months and have never had a problem and the 3d works great!

---

### Post by Mau on 2005-07-13
[QUOTE=kleeman]I have that card on Hoary and the latest ati drivers (installed manually, although the standard Hoary ati drivers also appear fine). I have used it for 3 months and have never had a problem and the 3d works great![/QUOTE]
 Good to hear!  I tried running flxgears (or whatever it is, I cannot remember atm), and I got 400 FPS at default window size. At full screen, I got around 16 FPS  - 1600x1280 (?) resolution.  I hear that's pretty *bad*?  (400FPS sounds pretty good, but then again it's only 3 gears).

I also noticed that I have the *Pro* version of that card - that wouldn't make it any difference would it?

---

### Post by kleeman on 2005-07-13
There are two test programs:

fgl_glxgears   (My result is 392fps) - tests 3d
glxgears          (my result is 1942fps)- tests 2d

---

### Post by 0xception on 2005-07-13
i get in the 3000-4000 range with flxgears but when i try and run fgl_glxgears i get 

```
$ fgl_glxgears
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32
``` 

any ideas?

sorry Mau i'm not trying to steal your thead :) ... just wondering what this means ...

---

### Post by Mau on 2005-07-13
[QUOTE=0xception]sorry Mau i'm not trying to steal your thead :) ... just wondering what this means ...[/QUOTE]

No worries... I already stole this one.  :-\"

Does running the gears program on the live CD make any difference?

---

### Post by mirak63 on 2006-05-03
[http://www.ubuntuforums.org/showthread.php?t=89213&highlight=9600+pro](http://www.ubuntuforums.org/showthread.php?t=89213&highlight=9600+pro)

Has they say in that thread you must build a custom kernel without ati radeon support.


Here I am asking to dapper forum wich solution could be found to not have the pain to build custom kernel.
[http://www.ubuntuforums.org/showthread.php?t=169509](http://www.ubuntuforums.org/showthread.php?t=169509)

---

