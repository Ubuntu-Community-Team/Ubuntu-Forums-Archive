---
title: "No Visual Effects - ASUS N61J and Nvidia GeForce GT 325M"
date: 2010-05-11
forum: Hardware
---

### Post by buddywilliams on 2010-05-11
I recently installed Ubuntu 10.4. Ubuntu suggested I install the nvidia driver and so I did. After installing and rebooting I got a black screen that never changed. I remove the driver and was able to get my screen back.

My graphics card is a GeForce GT 325M which uses Nvidia Optimus which isn't supported in linux. Therefore, I have actually have two graphics cards:
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a35 (rev a2)
```

So since I can't use the Nvidia card I should be able to use the Intel card. Therefore, I removed all my xorg configs since Ubuntu 10.4 doesn't need them.

I would have given up trying to make this better except the following occurs:
If I boot with a live CD (in my case a USB drive) I get Visual Effects. But if I boot normally I do not.

How can I get the configuration the live cd gives me without a fresh install?

---

### Post by Azegul on 2010-05-13
I have the same laptop and the same problem.
The Nvidia GPU worked fine on the Live CD but I can't get it to work on an installed system. I'll keep searching the net in the meantime to find a solution. I know that there will be one eventually. We just have to be patient.

Post number 2 here activated my nvidia driver, but I still can't enable desktop effects.
[http://ubuntuforums.org/showthread.php?t=1481016&highlight=driver+activated](http://ubuntuforums.org/showthread.php?t=1481016&highlight=driver+activated)

---

### Post by palmira on 2010-05-29
Hi.
[quote="Azegul"]The Nvidia GPU worked fine on the Live CD but I can't get it to work on an installed system.[/quote]
Are you sure the Nvidia card was used by the Live CD and not the Intel card?

It seems to be an error of Ubuntu to suggest an inappropriate driver. Do you know what happens if, after a fresh install, one doesn't follow Ubuntu's suggestion to install the Nvidia driver? Would Ubuntu then just use the Intel graphics (with 3D effects working)?

It's really frustrating that even Nvidia cards can cause such problems nowadays. Could you find a solution?

palmira

---

### Post by buddywilliams on 2010-06-08
After tons of digging, here's the solution or at least where I am.

First, the nVidia card isn't supported by Linux. Secondly, the Intel card has 3D support! Therefore, when I am running Linux I let the OS use the Intel card (as if I had a choice) but if I run Windows it can use the nVidia card based on the Optimus technology.

I am pretty sure I am using the MESA driver to get the 3D support because glxinfo | less (near the top) gives me:
- server glx vendor string: SGI
- client glx vendor string: Mesa Project and SGI
- OpenGL vendor string: Tungsten Graphics, Inc
- OpenGL renderer string: Mesa DRI Intel(R) IGDNG_M GEM 20091221 2009Q4

The only way I could get 3D support was to:
[LIST=1]
[*] remove the xorg.conf file altogether (Ubuntu 10.4)
[*] restart
[*] enable desktop effects: System > Preferences > Appearance > Visual Effects > Click Normal
[*] cancel the option, once asked, to install the nVidia driver
[*] reboot and repeat steps if needed (may require multiple tries)
[*] you'll know it's working once the option for Normal continues being selected
[/LIST]

---

### Post by XwyhyX on 2011-01-03
How to delete xorg.conf? And is is the xorg.conf only?

---

### Post by buddywilliams on 2011-01-03
Yes, you only need to delete xorg.conf.

You should move it rather than delete it so that you can keep a backup. Remember if your settings get really messed up and your can't see your screen, Ctrl+Alt+F1 is your friend.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then you will need to restart your computer.

```
sudo shutdown -r
```

---

### Post by XwyhyX on 2011-01-03
Ok, I dont have a xorg.conf in that directory. Aww, I dont know why, all I have there are backups,


 But I've resolved it anyway by using -uninstall parameter in the nvidia driver. Then I searched for MESA in the synaptic package manager and voila! Effects are working! Thank you for providing what driver worked! Haha

---

### Post by buddywilliams on 2011-01-03
Glad I could help ;) That's why posting the details is so important - you never know what will actually help...

---

