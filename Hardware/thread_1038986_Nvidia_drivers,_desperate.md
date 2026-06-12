---
title: "Nvidia drivers, desperate"
date: 2009-01-14
forum: Hardware
---

### Post by Fuwisu on 2009-01-14
Ok after 2 days of non-stop trying to get my drivers to work I'm out of ideas. I have a 8600M GT card, and Kubuntu Intrepid Ibex 8.10 (KDE). I have my laptop connected to an external screen.
So far the best I had was that my laptop screen was ok and the device driver section said I had 177 enabled. The bad thing was that my external screen didn't work.

Things I have tried so far:
-Envyng, mostly gave a libGL error so I had to copy that one from my ubuntu cd
-Download from the nvidia site
-Many other things

Every time I got one of these results:
-Bugged screen, mostly after doing nvidia-xconfig
-Couldn't find module "nvidia", "type 1", etc...
-Got something, but only on laptop screen + it said I had to do nvidia-xconfig, but after doing that it kept saying it.
...


Now I am wondering if anyone else has had these problems, and what they did to fix it? Because everytime I finally got some results, it disables the drivers again, like it wants to make fun of me...

---

### Post by Fuwisu on 2009-01-14
bump

---

### Post by balaknair on 2009-01-14
Try the latest stable nVidia driver 180.22
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)


Download the latest driver from here
[http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html) 
and save it to your home folder.

To install it you'll need to exit the GUI and use a text console.
Get envyNG to uninstall the old driver safely first.
Then install the nvidia driver and restart the GUI.

Steps:
ctrl-alt-F1 to get to text console

Login with your user name and password

Stop the Xorg GUI
```
sudo /etc/init.d/kdm stop
```

Install the tools and packages needed to compile a kernel module
```
sudo apt-get install build-essential libncurses-dev gettext xmlto xmltoman linux-headers-`uname -r`
```

Install envyng and use it to uninstall the older nvidia drivers without borking your system.
```
sudo apt-get install envyng-core
sudo envyng -t

```
Use envyng to uninstall the nvidia drivers(select the uninstall option)

Now install the new drivers you have downloaded to your desktop
```
sudo sh ./NVIDIA-Linux-x86_64-180.22-pkg2.run
```
 Your driver version might be different(I'm using the 64bit version of Ubuntu), so just hit TAB after typing up to the N and the rest of the file name will automatically appear.


This will start the installer--> click OK for all steps till it's done but choose x.org automatic configuration at the last step in the installation.

Now restart the GUI
```
sudo /etc/init.d/kdm start
```

This should get your nVidia cards up and running.


You can also stick with the 180.17 or 180.18 drivers since some people have reported issues with the 180.22 drivers and some cards(*(EE) Failed to load module "type1"(module does not exist, 0)* like what you get) though I think installing the linux headers will eliminate this error.

Hope this was helpful.
All the best.

---

### Post by Fuwisu on 2009-01-14
Ok thanks, I'll try that tomorrow. Btw, how do I edit my xorg file so I can enable my external monitor? Got something to do with dualview?

---

### Post by balaknair on 2009-01-14
Have you tried using the nVidia settings manager to configure the dual monitors?

Remember to run it with admin privileges(alt-F2--> *kdesu nvidia-settings*)

Select Xserver Display Configuration--> Detected displays will be shown in the 'Layout box'(If not, click the 'Detect Displays' button)--> Set the configuration to 'Twinview'--> Choose the monitor to configure from the 'Layout' box--> Choose whatever position settings and resolution you want for each screen--> click 'Apply' and see if the set-up is as you want it.

When you're done, click on the 'Save to X configuration file' button at the bottom of the window. This will modify the contents of the Xorg.conf file to reflect the new configuration.

If you get an error(saying the Xorg.conf could not be written to or something like that), click the 'Save to X configuration file' button--> select the 'Show preview' button, copy the entire contents shown in the preview, open the Xorg.conf file in the text editor(alt-F2--> kdesu kate /etc/X11/xorg.conf) and delete everything in it and paste the contents you copied from the 'Show preview' option in nVidia settings.

**IMPORTANT**: Remember to make a backup of the existing(working) /etc/X11/xorg.conf file before making any of these changes.

---

### Post by Fuwisu on 2009-01-15
It gives me the usual module type 1 error. During installation it also gave me a few errors. It also said that it had to compile the kernel because he didn't find any or something like that.
I don't get it, the newest driver works for 8.10, not?

---

### Post by Fuwisu on 2009-01-15
HOORAY, after 4 days of trying, I finally got my nvidia drivers to work :D
I read somewhere that you have to comment out the "type 1" module in the xorg file, so I did that and the nice nvidia logo came up ^^

Thanks for the help though.

---

### Post by balaknair on 2009-01-15
Glad to see you got it working.

Compiling the kernel: not an error, that is to be expected, since unlike for an install from the Ubuntu repositories(where the latest version is 180.18, I think) the particular preconfigured kernel module is not available for download. If you have removed the previous nVidia kernel module, the newer one will work fine, but in some cases where the previous drivers have not been completely uninstalled, you tend to get errors and you end up with low-res graphics(safe graphics mode).

---

