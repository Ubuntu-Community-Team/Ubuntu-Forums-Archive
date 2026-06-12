---
title: "Dell Vostro 1500 display problems"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by chintan.patel on 2007-09-14
I am using a Dell Vostro 1500 with Intel Core2Duo T7200, 2GB of RAM, nVidia GeForce 8400M GS graphic card.
My problem is that when I started Ubuntu 7.04, the screen went completely blank. Suspecting graphic driver problems, I installed in text mode. But even now, it does not show anything when booting. I do not have any idea what is going on in my system.

---

### Post by DellCAJohn on 2007-09-19
Chintan-

My name is John, and I work as a support analyst at Dell headquarters.

If I understand you correctly, you were able to succesfully install Ubuntu in text mode, but after installation, you get no video. If this is the case, it sounds like you kernel is incorrectly configured. Have you configured your kernel to work with the video card, ie, have you installed the NVidia driver for the 8000 series cards? 

If you can boot from CD, you should be able to mount the system drive, and make the configuration changes from there. If you can't boot from CD, have you tried a different distro? Are you getting video when booting from the Windows CD? If not, you may have a hardware problem.

If you are having a hardware issue, I could probably be more helpful. If that ends up being the case, let me know, and I will do what I can to help.

John
Dell Customer Advocate
[email]customer_advicate@dell.com[/email]

---

### Post by w4ett on 2007-09-19
I'd start by reconfiguring your xorg.conf.....from the Grub menu, boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by fak3r on 2007-10-11
...Also, if you are still having issues, let me recommend that you install the normal desktop iso of 7.10 Gusty Beta.  It boots, installs just like a liveCD should and works perfectly (graphic wise) on the Vostro 1500 -after install I even did the the auto install of the nVidia drivers too - so had zero problems on mine, display wise.  Sound, suspend needed some work, but the forums helped me there.  It's a great laptop for Linux IMO, and shows off Gusty nicely!  Keep at it, all the issues are small and easily solved.

---

