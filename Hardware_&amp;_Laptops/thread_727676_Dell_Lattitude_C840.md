---
title: "Dell Lattitude C840"
date: 2008-03-18
forum: Hardware &amp; Laptops
---

### Post by halvara1 on 2008-03-18
I recently aquired a Dell Lattitude C840 and installed Gutsy Ubuntu 7.10 on it. The installation went well, updates went without a hitch too. I noticed there was a proprietary drivers icon in the tool bar. when I opened it is showed my NVidia 64MB video card as not enabled. So, I clicked enable and after reboot i have a blank screen. How can I get back to "vga" mode and change the settings if I cant see the screen. screen works during reboot however, as soon as the driver kicks in it goes blank.  If anyone can help I will certainlu appreciate it.  

Desparate Ubuntu Rookie...

---

### Post by erginemr on 2008-03-19
Don't worry. Patience is the best friend of a Linux user.

When you are kicked to the terminal, if you can have a text screen that accepts any keyboard input, write down the next set of commands.

Otherwise, you can change to a virtual terminal by Ctrl+Alt+F1 (or F2, F3 ... F6), login with your user name / password to a different text-mode session and proceed from thereon.

There is a config file "/etc/X11/xorg.conf" in your system that holds the settings for the graphical screen. We shall edit that one. (You may consider jotting these down on a scrap of paper.)

```
sudo nano -w /etc/X11/xorg.conf
```

Find the lines that say:
```
Section "Device"
        .......
        Driver          "nvidia"
        .......
EndSection
```

Replace the line **"nvidia"** with **"nv"**. Save the file with Ctrl+O and exit with Ctrl+X.

Now issue the command
```
startx
```
or alternatively, restart your computer to start your graphical server again.

Post back here when you (hopefully) get your desktop back first and we shall keep on working on enabling the binary driver later on.

Good luck.

---

### Post by halvara1 on 2008-03-21
Thank you so much for the assistance that did the trick! i was able to get back into the system and change to default setting. Whew. Again, many thanks. :guitar:

---

### Post by erginemr on 2008-03-22
Great news! :D I am happy that you have your screen back. Now is the time to enable the 3-D and desktop effects (Compiz Fusion) for your card:

1. Now that you have replaced "nvidia" (binary driver form NVIDIA) with "nv" (open-source driver from Ubuntu), I assume that you have 3-D disabled. Let's check that one as well:
```
glxinfo | grep -i direct
```
If the reply is "yes" then your 3-D is enabled and you can live happily ever after. Otherwise, read on...

2. First things first, let us learn what card you have:
```
lspci | grep -i vga
```

You should look-up your card from this link:
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html)

to see in what category it falls:
Group-1: Newest cards, "nvidia-glx-new" in Synaptic.
Group-2: Medium aged cards, "nvidia-glx" in Synaptic.
Group-3: Archaic cards, "nvidia-glx-legacy" in Synaptic.

For instance, I have been using "NVIDIA GeForce 4 MX" which falls into the second group, so I have "nvidia-glx" installed in my system by the "restricted drivers manager".

3. A good Linux user, besides being patient, also likes reading a lot. ;) So, you should first read the following howto thoroughly:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

4. Once you feel ready for the action, you should, first and foremost, back up your working system config from a terminal with:
```
sudo cp /ect/X11/xorg.conf  /ect/X11/xorg.conf.mybackup
```
so that, should things go wrong, you can always revert to your working settings with:
```
sudo cp /ect/X11/xorg.conf.mybackup  /ect/X11/xorg.conf
```

5. Then, go to Synaptic (Main Menu -> System -> Admin), remove nvidia-glx-* and reinstall the correct one you have found from your above research. Attached screenshot shows the ones in my system. Then, run:
```
sudo nvidia-xconfig
```
from a terminal which will simply replace "nv" with "nvidia".

6. You should stay away from the tool "Screens and Graphics" at all costs. It is buggy and will screw your system. In lieu of that tool, you can use the tool coming from the  "nvidia-glx-*" package by running: 
```
Alt+F2 -> gksudo nvidia-settings
```
You can adjust pretty much everything from there including screen resolutions and refresh rates.

7. The counterpart of that tool on the command line is:
```
sudo dpkg-reconfigure xserver-xorg
```
which asks you a couple of questions including the driver "nv, nvidia, ati, fglrx, intel, et al." and a set of resolutions you will like to use "800x600, 1024x768, 1280x800, 1440x900 et al.". So if you are not happy with the screen resolutions you have got, it is worth a try, 

8. You can also give a try to 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
which acts on your behalf and tries to configure your graphics setting automatically. I always liked this command, as I has saved my err,,, you know what... in quite a few nasty situations.

9. Finally, there is a reputable script among fellow Ubunteros, called ENVY, which serves both NVIDIA and ATI users alike and fetches the appropriate NVIDIA binary driver directly from their web site along with some Xorg development packages and installs them:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) 

The drawback of using ENVY is that; the driver is compiled by Envy as compatible with your current kernel only, thus it will give rise to incompatibility problems when you upgrade your kernel as part of the standard periodic Ubuntu updates. Or worse, you may find yourself staring at a text-mode screen, when you decide to upgrade your system to Hardy, which will be released a month from now.

So, although the installation with Envy is a piece of cake, I still suggest you to use it as a last resort; in other words, only if the above methods don't work in your system.

10. To give you an example, I am attaching the xorg.conf file I have. This config works with Compiz enabled in my system with a standard CRT monitor with 4:3 screen ratio.

So, good luck and keep us posted. As a final bit of advice, no matter what you experiment with in Linux, you can usually (but not always) restore your system in Linux if you take a back-up of a few config files first.

---

### Post by erginemr on 2008-03-26
> **halvara1 said:**
> Thank you so much for the assistance that did the trick! i was able to get back into the system and change to default setting. Whew. Again, many thanks. :guitar:

Any news?

---

