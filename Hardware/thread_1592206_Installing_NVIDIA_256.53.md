---
title: "Installing NVIDIA 256.53"
date: 2010-10-10
forum: Hardware
---

### Post by klapointe on 2010-10-10
I'm running an older version of NVIDIA which resulted in many Lucid Lynx crashes, and now I'm wondering if installing the newest version will help with my computer.

I just upgraded to Maverick today however it crashed during upgrade and I had to run a partial upgrade to fix it. I have downloaded the NVIDIA package but whenever I try to run the file [NVIDIA-Linux-x86_64-256.53.run] it comes up with errors stating that I have to exit the X-screen.

I have tried 
$ sudo stop gdm

but whenever I do so it brings me to the Ubuntu 10.10 screen and I can't do anything. I'm a bit uncertain with terminal commands so I don't know how to do some things. 

How can I install this?

---

### Post by tudor117 on 2010-10-10
Reboot in recovery mode, it's the other option in grub.
Next start a root shell.
Then: ```
 telinit 3 
```
Then you can login, and run the Nvidia installer.

An other option is to kill gdm like this:
```

sudo /etc/init.d/gdm stop

```
But I don't remember for sure because I don't use this way anymore.

---

### Post by ellgor on 2010-10-10
Hi,

You almost had it, I found a couple of guides that gets them in and running, I've put them together so use what you need:

If you have a black screen give it a few minutes, try pressing  Ctrl-Alt-F1 (or any F upto 6) should this fail to give you a working environment (console) reboot and as soon as any text shows press the Tab key(keep it pressed) this should show a grub boot screen where you can choose to boot into a terminal, note this works most times. 

For those considering changing nvidia drivers, this little snippet prevents ending up with a black screen that does nothing:

Modify modprobe:
sudo gedit /etc/modprobe.d/blacklist-framebuffer.conf  

put a # in front of  blacklist vesafb and ADD blacklist vgafb16

Modify modules:
sudo gedit /etc/initramfs-tools/modules

Add fbcon and vesafb (after the vesa entry enter a blank line, close and save)

Update:
sudo update-initramfs -u

Modify grub:
sudo gedit /etc/default/grub

search for GRUB_CMDLINE_LINUX="" and ADD vga=771 or 795(first is better) between the quotes, then do:

sudo update-grub

**
Once the drivers have been loaded in you may need to change the vga=771 back to blank "", as it may affect the login screen.
**

1) Download latest driver from Nvidia site (that matches your card)

2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf

3) Add these lines and save: (might be a blank doc, adding these creates it now)

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*

5) Reboot your computer

6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)

7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have) be precise as errors will result in "no such file"

Note: If you get an error message like this "Unable to find kernel source tree", do this:
$ sudo apt-get install linux-headers -`uname -r'

then run the installer again

8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Hope this is of help.

Regards, Ellgor.

---

### Post by efflandt on 2010-10-10
What video card do you have (at least the line from output of lspci)?  What nvidia version were you having trouble with before?

I am curious if it is best to uninstall proprietary video drivers before a distribution upgrade, especially if video was installed from outside sources instead of through Ubuntu repositories.  I normally install fresh and the only upgrades I have done were with default video drivers.  In a 32-bit 9.10 to 10.04 upgrade, I did notice that ubuntu-restricted-extras disappeared and flashplugin-installer appeared to be installed, but did not show up in Firefox until Marked for Reinstallation in Synaptic.

Sometime after 10.10 beta or during RC the default nvidia version for new enough supported cards changed from 256.53 to 260.19.06.  Although, there are still 173 and 96 versions for older cards.

Someone with a card similar to mine (GT 220) has an overheating problem with 260.19.06, but it looks like their GPU fan is not working (shows fan 0%).  Mine with same ID peaks much cooler with fan only running 30% @ 99% GPU.

Note that 32-bit flashplayer.so 10.1 r85 installed by flashplugin-installer in 64-bit 10.04 or 10.10 segfaults, crashing npviewer.bin of Firefox 3.6.10.  Although, I never noticed when it crashed other than the logs (maybe flash ads).  I have had no issues with real 64-bit flash 10.2 r161 in Lucid or Maverick.

---

### Post by ca1ig0la on 2010-10-12
> **ellgor said:**
> 
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)


What if I don't get that error?

> **ellgor said:**
> 
9) Start GDM

What if the system freezes after starting gdm? When it gets to load the nvidia module the log says "Failed to initialize GLX extension (Compatible NVIDIA X driver not found)".

Any clue?
Is there any chance that either the system is looking in the wrong place or the modules are stored in the wrong directory?

regards

caf

---

### Post by ellgor on 2010-10-12
Hi,

If you don't get that error I take it it boots up normally, log in as normal and open a terminal, what happens now is that the GDM has to be stopped for the process to go ahead with no problems, this is done with:

sudo stop gdm

whereupon you will be left at a blank screen with command line access, go to number 7), if you arrive at an unresponsive black screen follow the instructions as per guide.

Regards, Ellgor.

---

