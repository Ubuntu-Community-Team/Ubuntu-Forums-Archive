---
title: "Problem with NVIDIA drivers 66.26 (Warty, using nvidia's run package)"
date: 2005-01-02
forum: General Help
---

### Post by Randabis on 2005-01-02
I've compiled a custom kernel with bootsplash support using kernel-package. The kernel is kernel-source-2.6.9 and it appears everything went well (after a minor fix, had to copy the vanilla kernel /drivers/vga/vesafb.c over to fix a bug with the bootsplash). Instead of using warty's 61.11 driver, I've opted to download nvidia's run package to install the latest 66.26 drivers. I run the package with sh, the menu comes up, and I install the driver. It says the driver has been successfully installed. Since I previously had the older driver running on my 2.6.8-k7 kernel, I left my XF86Config-4 file alone since the necessary changes had already been made (I double checked to make sure anyway). Anyway, instead of rebooting, I just typed startx. The NVIDIA splash screen pops up, and my root desktop initializes and starts up. Everything is fine and dandy.

Now, for the problem. After I reboot, I run my new kernel (got grub configured nicely), my bootsplash comes up just fine and the kernel is loading. Then GDM loads, and instead of the NVIDIA splash screen, I get a plain white screen that flickers a moment, then goes blank, then comes back (it appears that xserver is restarting or something similar), then goes blank again, the comes back, and nothing happens. I hit enter on the keyboard, and the system tells me x won't load and lets me get the output. I don't have the output copied because it really wasn't very interesting and didn't appear to have any information that would help solve the problem. I can try and get this info if I must.

Anyway, does anyone have a solution or an idea to start from to solve this? Like I said, X will run fine until I reboot, then all hell breaks loose.

Thanks in advance, and I hope I'm posting this in the right place. I've been searching for a fix to this for hours and am coming up empty handed.

---

### Post by hardcandy on 2005-01-02
Probably the nvidia module is not getting loaded after a reboot. You will need to add it probably to /etc/modutils (there may be an entry for your older nvidia module, not sure about it remaining after a rebuild. And then run "sudo update-modules". I do not have a whole lot of experience with Debian based distros so I would look for some other post here about adding a rebuilt module to modutils and /etc/modprobe.conf.

---

### Post by Randabis on 2005-01-02
[QUOTE=hardcandy]Probably the nvidia module is not getting loaded after a reboot. You will need to add it probably to /etc/modutils (there may be an entry for your older nvidia module, not sure about it remaining after a rebuild. And then run "sudo update-modules". I do not have a whole lot of experience with Debian based distros so I would look for some other post here about adding a rebuilt module to modutils and /etc/modprobe.conf.[/QUOTE]


Thanks a lot for the suggestion hardcandy.

I have solved the problem on my own (FINALLY, YAY!). I had to do some package removals. 

here's what I did,

First, uninstalled the new driver.
Then I removed the old driver. Then I removed linux-restricted-modules (all of them that I had installed). Finally I installed the new driver.  I did startx to verify it was working, then rebooted. Now everything is just fine.

:) Very happy now. Latest nvidia drivers, plus a nice bootsplash.

---

### Post by LongTooth on 2005-01-02
A remotely related tidbit, one can find steps to remove the Nvidia splash in the 'Ubuntu4.10 Starter Guide,  [http://ubuntuguide.org/#disablenvidialogo](http://ubuntuguide.org/#disablenvidialogo) . I came across it quite by accident. Of course this is done after one is certain all is well.

---

### Post by mark on 2005-01-19
[QUOTE=Randabis]Thanks a lot for the suggestion hardcandy.

I have solved the problem on my own (FINALLY, YAY!). I had to do some package removals. 

here's what I did,

First, uninstalled the new driver.
Then I removed the old driver. Then I removed linux-restricted-modules (all of them that I had installed). Finally I installed the new driver.  I did startx to verify it was working, then rebooted. Now everything is just fine.

:) Very happy now. Latest nvidia drivers, plus a nice bootsplash.[/QUOTE]
I'm currently running the nVidia driver from the Ubuntu repos (6111) on a PNY Verto AGP display adapter (FX-5500, 128MB).  I've downloaded the 6629 driver direct from nVidia, but I've been too chicken to make the switch (if it ain't broke, don't fix it!).

Do you find anything compelling in the later driver?  Is it worth the (admittedly minimal) hassle to make the change?

*Thanks!* 

Mark

---

