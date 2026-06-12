---
title: "Very high temperatures + loud fan"
date: 2016-03-04
forum: Hardware
---

### Post by pxie on 2016-03-04
I have dual-boot Windows 8.1 alongside with Ubuntu. I had to remove the old Ubuntu - format partition and reinstall ubuntu again. Since the last instalation i have got a problems with temperatures of all my notebook components. All components have temperature around 65-70 while i do not do basically anything except surfing on the internet. When i start watching stream for example twitch even in low quality i'm getting temperature around 85 - 91 fan is super laud and the twith video is lagging it's not fluent it freezes in intervals etc. I did not have those problems with previous Ubuntu. In windows i got temperatures around 50-55 and notebook is not laud.

The changes i made in the last instalation :

[LIST]
[*]Before intalation when i wanted to boot Ubuntu i had to edit grub menu and change "Quick splash" to nomodeset because i was getting restarts and spammed by noveau ( i heard it's graphical driver ).
[/LIST]

My notebook specs : 
[LIST]
[*]Lenovo IdeaPad y50-70
[*]nVdia Gefore GTX 980 4 GB
[*]Intel i7 haswell 4720 HQ
[*]SSD 256 GB
[*]Windows 8.1 / Ubuntu
[/LIST]

Another differences from the last instalation :
[LIST]
[*]Now when my notebook is booting the grub menu does not show i have to press F12 and choose Ubuntu there to start grub menu.
[/LIST]

I will be really thankful for all your advices and please keep in mind that i have not that much experiences with Ubuntu.

---

### Post by houstonbofh on 2016-03-04
Two things to easily check.

First, do you have the same behavior when booting from a Live-CD/Live-USB?

Second, can you blow out the vents and openings with compressed air?  They do collect an amazing amount of junk.

---

### Post by pxie on 2016-03-05
Yes it has got the same behavior when booting from a Live-USB

---

### Post by Linuxisfast on 2016-03-05
Have you tried installing nvidia-drivers from driver install applet and then turn of the graphic card via nvidia-settings.

---

### Post by pxie on 2016-03-05
No i have not tried do u have any reliable source?

---

### Post by Linuxisfast on 2016-03-05
> **pxie said:**
> No i have not tried do u have any reliable source?


Its in the distro itself. Go to System Settings>Software and Updates>Additional Drivers.

Make sure to tick the newer 352 driver for your laptop and not the older 340 series. Install and any other drivers shown there for wifi etc. Reboot and then in dash type nvidia-settings and disable nvidia CPU, log out and relogin and you will have cooler laptop. Also install TLP.

---

### Post by Frogs Hair on 2016-03-05
I found htop system monitor helpful  for discovering the cause of  heat problem on the development version recently. ```
sudo apt-get install htop
``` To start the monitor ```
htop
```

---

### Post by Yellow Pasque on 2016-03-06
> **pxie said:**
> i had to edit grub menu and change "Quick splash" to nomodeset

That will disable GPU acceleration and make the CPU do everything. That's why your laptop is running hot.

---

