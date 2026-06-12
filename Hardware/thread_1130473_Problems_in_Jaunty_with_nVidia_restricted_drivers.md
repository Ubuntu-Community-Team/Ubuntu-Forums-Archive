---
title: "Problems in Jaunty with nVidia restricted drivers"
date: 2009-04-19
forum: Hardware
---

### Post by Hunter Sean on 2009-04-19
I keep having problems with the nVidia restricted drivers.  It started in 8.10 so I went back to 8.04.  Now that 9.04 is almost out officially, I tried it too and I am having the same problem again.  I am using driver version 180.  Here is part of my Xorg.0.log file with the problem:

[SIZE="1"](II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:2:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.[/SIZE]

I've tried all sorts of things suggested on forums such as this but with no success.  Any ideas?

---

### Post by trubendall on 2009-04-20
I'm having the same problem.  Worked fine in 8.04, but 8.10 and 9.04 they don't load.

Any help?

Thanks,

---

### Post by dhysk on 2009-04-20
Did you do a clean install or an upgrade.  I had the same problem when I finally upgraded to 8.10 last week.  It disabled my driver that I installed myself from the Nvidia web site.  I then enabled the driver threw the restricted driver menu.  When I restarted I had that same issue.  What I did was use the recovery menu to reset the x server.  Then I just reinstalled the Nvidia driver manually.  Then I used the old xorg.conf file from the 8.04 install because the Nvidia drivers automatic xorg configurations utility didn't work.

I think the problem had to do with the changes in the x server.  If I remember the x server was updated in 8.10 and 9.04.  Anyway if you updated try rolling back your xorg.conf file.

---

### Post by Hunter Sean on 2009-04-21
I tried a fresh install of 8.10, an upgrade from 8.04 to 8.10, and a fresh install of 9.04, all with the same results.  I also used the recovery menu to reset the x server but I did not install the driver manually or use my old xorg.conf.

I will try installing 8.04 again, enabling the restricted drivers, and then saving my xorg.conf file to a disk.  Then I will install 9.04 again, manually install the driver, and then copy/paste the xorg.conf file.  I'll let you know how it goes.

---

### Post by Hunter Sean on 2009-04-21
My last post was from within Windows.  I figured that I would try booting into 9.04 and then taking the xorg.conf file off the install disk but when I logged in, the resolution was correct this time with no problems.  I checked and it appears that after all my steps, I just needed to reboot.

For what it's worth, I tried *sudo dpkg-reconfigure -phigh xserver-xorg* and then I believe I had to add the *driver      "nvidia"* line under *Section "Device"* just below *Identifier      "Configured Video Device"*.  Next, I went to *System > Administration > Synaptic Package Manager* and removed all packages beginning with *nvidia* except for the following:

[I]nvidia-180-libvdpau
nvidia-180-modaliases
nvidia-settings[/I]

Next, I went to *System > Administration > Hardware Drivers* and the only thing that came up as an option to activate was *nvidia* so I activated it.  Next came the reboot and everything seems to be fine.  When I went into Synaptic again (*System > Administration > Synaptic Package Manager*) it showed more nvidia packages had been installed:

[I]nvidia-96-kernel-source
nvidia-96-modaliases
nvidia-glx-96[/I]

I don't fully understand it but it works so it's all good.  It appears that it installed the 96 driver and is ignoring the packages for the 180 driver.  Perhaps my card (GeForce 7600 GS) is too old to use the newer driver.

Anyways, I am really sorry if this is not much help.  I am still pretty new to Linux but I'm getting the hang of it.  Unfortunately, I was up late trying to fix this problem and so I didn't copy any of my steps.  Hopefully, what I recalled here is all that it would take to help someone in a similar situation.  I will try to recreate the situation and follow the steps listed here to see if takes me to the same place, but it may take a while to finish.  I'd say to check back once a week to see if/when I am successful.  If, however, you cannot wait or have to try to fix it yourself (two traits I possess), good luck!

---

### Post by Hunter Sean on 2009-04-23
Okay . . . After trying all sorts of things, I have come to the conclusion that only the nvidia 96 driver works with my card.  I did not try any lower versions, but 173 did not work, nor did 180.

---

### Post by unprinted on 2009-04-28
I will be interested to see if it continues to work. I have just uninstalled the 96 drivers from a PC with a Ti4200 card.

With them, when the screensaver kicked in, CPU usage for the Xorg process went to 100%, even with a simple screensaver module, and effectively locked it up: pressing keys and moving the mouse having no effect.

---

### Post by lifelesspoet on 2009-04-28
I had very same problem, though im having a different one now which is how i found this thread, anyway.
my fix was 
lspci
find your video card on the list, should look like this
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GTS 512 (rev a2)
then edit your /etc/X11/xorg.conf and add this
BusID "03:00.0"
to your device section.
Hope that helps.

---

### Post by futuroimperfetto on 2009-05-07
It seems lots of people are having problems with nVidia drivers and Jaunty 9.04.

There are other reports and suggested solutions here

[http://ubuntuforums.org/showthread.php?t=1136343]("http://ubuntuforums.org/showthread.php?t=1136343")

and here

[http://ubuntuforums.org/showthread.php?t=1136766]("http://ubuntuforums.org/showthread.php?t=1136766")

and here

[http://ubuntuforums.org/showthread.php?t=1139101]("http://ubuntuforums.org/showthread.php?t=1139101")

and here

[http://ubuntuforums.org/showthread.php?t=1129280]("http://ubuntuforums.org/showthread.php?t=1129280")

If I find other related threads, I'll add them here.

I tried some of these solutions, but none of them worked for me. I'm now running an older nVidia driver, but the CPU is working way too much and slowing my computer down (I have Jaunty installed on an older computer with an ATI card on it and it runs way better than this new and performing machine which I'm writing from).

Any other hint might help.

Thanks

---

### Post by futuroimperfetto on 2009-05-09
> **lifelesspoet said:**
>  [...]
my fix was 
lspci
find your video card on the list, should look like this
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GTS 512 (rev a2)
then edit your /etc/X11/xorg.conf and add this
BusID "03:00.0"
[...]


I managed to use lifelesspoet's fix on my Dell XPS m1330 with an nVidia 8400 GS and am now running the latest drivers. It worked for me with a small difference from what's written above. The line one should add to the */etc/X11/xorg.conf* file is the following

```

BusID "PCI:3:0:0"

```

and not BusID "03:00.0". Note the presence of PCI and the semi-colons (instead of a period) inside BusID. Recapping, if the VGA line of lspci is *01:00.0*, the line you should add is *BusID "PCI:1:0:0"*.

The same fix is also suggested by ed-koala here

[http://ubuntuforums.org/showthread.php?t=1139101]("http://ubuntuforums.org/showthread.php?t=1139101")

Thanks to lifelesspoet and ed-koala!

---

### Post by allstar1971 on 2009-05-14
When I have the screensaver run more than ten minutes, my mouse freezes when trying to access the desktop.

However, my keyboard works fine.


I have nvidia 96xx video card, amd 3700+ cpu with 2mb memory.

---

