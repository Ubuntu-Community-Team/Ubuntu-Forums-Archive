---
title: "[SOLVED] nVidia oddity with Inspiron 1720"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by rboone on 2007-08-12
I've been struggling for 3 days to get my Dell Inspiron 1720 nvidia 8400 GS card to work nicely with Ubuntu 7.04.  I tried the nvidia-glx, nvidia-glx-new and nvidia-legacy packages but none of those worked.  So tried Envy and got the lastest nvidia driver to install.  Here is the oddity:

By default, after Envy installs the driver, the xorg.conf is set for 800x600.  I was able to login once after that.  If I reboot or power down, and then try to login again, I have to manually select "Gnome" from the session list before entering my username/pw.  Otherwise, if I just login using the "Last session", the screen goes black and a few seconds later, I'm returned to the login screen (and I know I'm entering my password correctly each time).

Another oddity -- after manually selecting "Gnome" and getting logged in at 800x600, I run the nvidia-settings script and choose say "1680x1050".  The screen changes to that new resolution and all looks fine.  If I save those settings to the xorg.conf file (via the nvidia-setting tool), then next time I reboot, I get the login screen and after entering my pw, the screen goes black (I see a few blinks of the hard drive light) but the screen stays black.  Trying "Gnome" session manually as above doesn't help.  The only way to recover is to reboot in recovery mode and copy back my 800x600 xorg.conf.

I notice this at the end of the xorg.log file:

NVIDIA: Failed to create the curor surface; disabling cursor
NVIDIA: Setting mode "1680x1050+0+0"
NVIDIA: No video decoder detected

Backtrace:
  /usr/X11R6/bin/X (xf86SigHandler+0x81)
 /usr/lib/modules/drivers//nvidia_drv.so

Fatal server error
Caught signal 11.  Server aborting.

Any ideas on what to try in order to get the high res settings to work after rebooting?
Any ideas why I have to choose "Gnome" session manually for the 800x600 mode to
work?

Thanks in advance,
Rog

---

### Post by guy.murray on 2007-08-18
You've got further than I have on my new 1720 with Ubuntu 7.04! 

Envy (0.8.1) won't install the NVIDIA driver for me, replies...

"Your operative system does not seem to be supported by Envy"

Did you come across this? If so, how did you get round it?

Tried downloading and installing the driver directly from Nvidia - seemed to install OK, but dumped me into run level 1 on reboot. Had to reset xorg.conf to VESA (NV doesn't work either).

Guy

---

### Post by tseliot on 2007-08-19
> **rboone said:**
> By default, after Envy installs the driver, the xorg.conf is set for 800x600.  I was able to login once after that.  If I reboot or power down, and then try to login again, I have to manually select "Gnome" from the session list before entering my username/pw.  Otherwise, if I just login using the "Last session", the screen goes black and a few seconds later, I'm returned to the login screen (and I know I'm entering my password correctly each time).

Another oddity -- after manually selecting "Gnome" and getting logged in at 800x600, I run the nvidia-settings script and choose say "1680x1050".  The screen changes to that new resolution and all looks fine.  If I save those settings to the xorg.conf file (via the nvidia-setting tool), then next time I reboot, I get the login screen and after entering my pw, the screen goes black (I see a few blinks of the hard drive light) but the screen stays black.  Trying "Gnome" session manually as above doesn't help.  The only way to recover is to reboot in recovery mode and copy back my 800x600 xorg.conf.
You might want to report this problem (which is Nvidia's and not Envy's) here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by tseliot on 2007-08-19
> **guy.murray said:**
> You've got further than I have on my new 1720 with Ubuntu 7.04! 

Envy (0.8.1) won't install the NVIDIA driver for me, replies...

"Your operative system does not seem to be supported by Envy"
I guess Envy **0.8.1** is right.

> **guy.murray said:**
> Tried downloading and installing the driver directly from Nvidia - seemed to install OK, but dumped me into run level 1 on reboot. Had to reset xorg.conf to VESA (NV doesn't work either).
Try this:
```
sudo apt-get --purge remove envy
```

```
sudo rm -R /usr/share/envy
```

(just in case)

then get Envy's latest release (**0.9.7**):
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb
```

install it:
```
sudo dpkg -i envy_0.9.7-0ubuntu8_all.deb
```

make sure the dependencies are satisfied
```
sudo apt-get install -f
```

Now, since you have tried Nvidia's installer you will have to follow point B of the instructions:
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

Finally, run Envy

---

### Post by guy.murray on 2007-08-19
Many many thanks tseliot!

Everything works fine now.

Guy

---

