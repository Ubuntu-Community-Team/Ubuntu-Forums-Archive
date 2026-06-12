---
title: "Cannot boot into OS - Need help removing ATI driver"
date: 2009-05-13
forum: Hardware
---

### Post by patrickalexson on 2009-05-13
I decided to try downloading the latest drivers from ATI's website in a feeble attempt to fix my display problems myself. The restricted drivers worked enough for me to get better resolution but the whole experience with it was terrible. I got a wonderful unsupported hardware watermark, flickering screen, and applications that ran full-screen would flash and minimize every so often. I know the card works, as when I dual boot into Windows, Ive never had a problem.

After installing the newest ATI package through terminal, I cannot boot into the OS. At the very last second of the Ubuntu splash screen, the screen flickers and then freezes with the Ubuntu logo and some random text on the screen.

I can access terminal I guess through the GRUB menu so what do I need to enter to wipe my display drivers back to defaults?

I would not really want to wipe and reinstall if possible. This is the ONLY thing thats keeping me from being 100% happy with Ubuntu. I have an ATI Sapphire Radeon HD 2900.

Thanks!

---

### Post by patrickalexson on 2009-05-13
I am at a shell awaiting what to type in

---

### Post by patrickalexson on 2009-05-14
I tried the following:

```
sudo apt-get remove xorg-driver-fglrx
```

I then received this as a response

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package xorg-driver-fglrx is not install, so not removed
The following packages were automatically installed and are no longer required:
dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Im guessing it couldnt find the driver to uninstall.

Someone please help me. What can I try next?

---

### Post by Locutus_of_Borg on 2009-05-14
in the interim, switch inside your xorg.conf, the driver you are using from ATI to VESA, this will allow you to use GNOME/KDE/etc. but only at 1024x768, which is better than nothing

then, use synaptics and uninstall all packages that turn up with a search for ATI

then try this: [http://ubuntuforums.org/showpost.php?p=4308023&postcount=6](http://ubuntuforums.org/showpost.php?p=4308023&postcount=6)

---

### Post by patrickalexson on 2009-05-14
Alright I believe I get the jest of what we are doing. Someone is going to have to help me on this because Im not sure of the commands.

What do I need to type to access the configuration file and then how do I switch to the VESA driver?

---

### Post by Locutus_of_Borg on 2009-05-14
from a terminal/bash shell enter the following two lines:

sudo -i

nano /etc/X11/xorg.conf

after the second command, you will be in a text editor, using the arrow keys, move the cursor down until you get to the area marked: 

Section "Device"

and look for the line starting with Driver

change what is in parentheses after Driver to read "VESA"

save the document by holding Control and pressing X, then letting go of control and pressing Y, then pressing Enter

back in the shell, type "reboot"

you should now be able to boot 'normally' but without high resolution, and without use of compiz

once this is successfully, we can try to get your ati card working properly

---

### Post by patrickalexson on 2009-05-14
Alright well it seems that our friendly fsck regime has overthrown my government's power and is forcing a file system check. My guts tell me that my harddrive SHOULDNT have any problems given that its a Western Digital and its brand new... plus Spinrite 6 verified no ECC, Seek, or SMART errors existed and that all blocks appear in good working condition...


Im letting it run a FSCK pass on the file system. Then we shall continue. Thank you Locutus_of_Borg, I believe once I get up and running, I should be able to continue using that somewhat simple set of instructions.

---

### Post by patrickalexson on 2009-05-14
Alright well I took a look at the configuration file and it WAS already set to use the VESA driver.

I thought screw it, if we start from scratch it might be easier so I just reinstalled.

Ok SO HERE WE GO...

If I enabled the restricted driver for my ATI card from within Ubuntu, I will get an annoying AMD Unsupported Hardware watermark and it will make my applications very unstable.

SO, any suggestions on how to get a stable driver? (WITHOUT THE WATERMARK)

---

### Post by Locutus_of_Borg on 2009-05-14
try using envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by patrickalexson on 2009-05-14
I installed EnvyNG via the package manager

Its downloading the 8.600-0ubuntu2 ATI driver

Hopefully we will not experience any issues. The watermark at this point is not that much of a concern to me but application stability is.

I dont want to have to stick with Windows just because of a mess with drivers. Im finding this OS much more advanced.

...


Its now restarting my system...
Its passed the GRUB menu...
Its going through the Ubuntu splash screen...

Dam that watermark is back...unsupported hardware

Resolution just increased quite a bit, much sharper image (I guess to be expected)

Alright now lets see how everything runs...

---

### Post by patrickalexson on 2009-05-14
Well its doing the same thing as far as bluring the text, however, I havent tried my applications yet (havent been able to reinstall them yet)

I guess I have to expect this when we have so many different kinds of hardware and drivers...

This does suck, but not a fault on the part of Ubuntu

---

