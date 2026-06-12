---
title: "Cannot start X Server after Gutsy Upgrade"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by ladgrove on 2007-12-29
Hey there,

long time Forum reader, first time poster. Ubuntu is a great community to be a part of :)

I recently upgraded from Feisty to Gutsy using Update Manager. During the final steps of the upgrade, the part where the upgrade asks you questions relating to debconf, I checked the "Keep the old configuration files" in relation to my display settings, thinking this would be prudent. However, when I rebooted, I got stuck in a gdm login loop. I would login, get as far as the Nvidia splash screen and then get thrown to login.

My vidcard is Nvidia 5200 which ran fine using the 'nvidia' driver in xorg.conf file, and thus I believe I was using the restricted driver, which worked well under Feisty.

I have scoured the forums and tried a few things. For instance, the simple things like changing to vesa, vga & nv in xorg.conf - none of these work; vga & vesa turns the screen off and nv gives similar problems to nvidia.

Since then, I have tried dpkg --reconfigure xserver-xorg all to no avail. I also tried deleting my .gnome and other folders as one topic suggestsed, but to no avail. I used apt-get to install the nvidia-glx drivers which got me as far as the Nvidia splash and then the grey screen with the black cross.

Before doing any of these changes, I was able to login as root using the nv drivers, but now I can't even get that far. This is the message that I get when I try to start X from RunLevel 3:

```
 EE: Failed to load /usr/lib/xorg/modules/libglx.xo
EE: Failed to load module "glx"
II: Module already built in
Failed to initialize the GLX Module; please check in your X log file that the GLX module has been loaded in your X server...

```

Interestingly, now when I reboot, I also receive this message:

```
kinit trying to resume from /dev/disk/by-uuid etc
no resume image found 
```

I'm really rather flummoxed, and I feel my Ubuntu install has gone to buggery, it's getting all a bit missy so I might just bite the bullet and reinstall, it's just that, from reading forums, I've never seen a non-bug topic that couldn't be solved without re-installing.

Apologies if I haven't posted enough information, if you need any log files, config file output, just let me know.

Cheers, Josh

---

### Post by foolsh on 2007-12-29
the safe bet would be to edit the /etc/X11/xorg.conf and change "nvidia" to "nv" on the drivers line for your video card
then use ubuntu restricted driver manager to install the "nvidia" driver
this is easy, as soon as gnome starts you should get a message telling you a restricted driver is avialible.

---

### Post by ladgrove on 2007-12-29
Hey there, thanks for the quick response. I'm not sure whether I mentioned but I have no GUI. Changing my xorg.conf to nv does not cause Xserver to start, I can't even get to gdm login. 

The problem I have now with Gutsy is that I'm not entirely sure which driver I'm supposed to be using for my 5200 card, but from what I've read simply getting the nvidia-glx should work, but it's just not working for me.

---

### Post by ladgrove on 2007-12-29
I'm going to bite the bullet and re-install. I would still appreciate any comments though, purely for the learning aspect.
Cheers.

---

