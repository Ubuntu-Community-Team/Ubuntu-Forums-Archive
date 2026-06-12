---
title: "EVGA Video Card=Unknown Card?"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by sonny on 2005-08-04
Hi, I've recently bought a EVGA Video Card with a Nvidia Chipset (6200) and 256 MB, at first when I plug it in my screen went with a black "shadow" (as if you have turned down the brightness) I thought it was because of the configurations of the previous card so I tried to reconfigure it by running:
sudo dpkg-reconfigure xserver-xorg
After getting all the defaults everything was fine and I was able to see the screen, so I remove and install the ubuntu nvidia drivers, I rebooted to see how it went, but nothing changed, so I went to my xorg.conf file to change the driver "nv" to "nvidia" and to enable the "glx", I did it, while I was doing so I notice that my card type wasn't detected, for it says Unknown Nvidia Card, I rebooted, after that everything went back to the strange darkness, I couldn't see a thing, it took me 10 min to change the new settings to the defaults, in order to see what went wrong I tried changing in the xorg one setting at a time, I found that the driver "nvidia" was causing this, as soon as I change it back to "nv" it was as clear as daylight, so I figure out it has to be the nvidia drivers, so I downloaded the most recent nvidia driver, and installed it, it all went fine, I change the settings again at it worked now I have the driver "nvidia" and it never went black. The only trouble I have now is the Unknown Nvidia Card thing, What can I do so my video card can be recognized? Does it afect the performance? Is this a mayor problem? Has anyone be able to properly configure this card?

---

### Post by mo_x on 2005-08-04
When the nvidia driver detects the card it is ok. Check the file /var/log/Xorg.0.log. I have the following line in it:
> (II) NVIDIA(0): NVIDIA GPU detected as: GeForce 6200 TurboCache(TM)
Mine works with the nvidia-glx packaget. Did you remove dri from your xorg.conf?

---

### Post by sonny on 2005-08-04
[QUOTE=mo_x]Mine works with the nvidia-glx packaget. Did you remove dri from your xorg.conf?[/QUOTE]
I didn't remove it, should I do it? Although now it won't be possible, because the card has problem with the xserver, now it won't load and I can't get into a prompt, I don't know what it's wrong, I'm gonna try reconfiguring the xserver if I manage to get into the secure mode.

After that I'm going to check the xorg.0.log file as you've said. So should I replace the Unknown nVidia Card thing with the one that has the xorg.0.log file?

---

### Post by sonny on 2005-08-04
I got back my xsession, although not quite as I wanted,  ](*,) first of all it doesn't have the "nvidia" driver, and every time I try to change it, the xserver never gets loaded, I don't have the error because my screen goes black, and it doen't respond to any key or combination of keys, my only chance is to reboot and change the xorg.conf file again to the "nv" driver. Now my vidoe card is detected as "generic video card", I need help, I know I can just leave it like this, but I want my games back, removing the "dri" line doesn't help at all, I've used both the nvidia driver and the nvidia-glx from the repo's, I don't know what else to do, help please.  :?  ](*,)

---

### Post by mo_x on 2005-08-05
When you say "detected as generic video card", where does dat show? Please post your xorg.conf file.

---

### Post by sonny on 2005-08-05
[QUOTE=mo_x]When you say "detected as generic video card", where does dat show? Please post your xorg.conf file.[/QUOTE]
Well I manage to fix it... now I can play as long as I want. The problem is that my video card wasn't detected, in the device section of my Xorg.conf file it was writen "generic video card", the only thing I had to do was changing the device section to look like this:

Section "Device"
    Identifier "Device(0)"
    Driver "nvidia"
    VendorName "nVidia"
    BoardName "GeForce 6200"
EndSection

It took care of the driver problem and the glx problem. But thank you mo_x for your replies.

---

