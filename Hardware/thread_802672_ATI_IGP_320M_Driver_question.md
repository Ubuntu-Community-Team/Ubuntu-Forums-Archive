---
title: "ATI IGP 320M Driver question"
date: 2008-05-21
forum: Hardware
---

### Post by NvidiaN on 2008-05-21
Hello all,

I have a question regarding my graphics and Ubuntu (Hardy Herring). I'm currently very very new to Ubuntu, just really installed it yesterday, and for the most part I'm quite pleased. I cannot however figure out how to make my laptop detect/use the ATI driver which is supposedly supported/provided by HH. I have a friend who had me type various commands into the terminal which came up with the following data (he claims it's "low" and that the computer isn't using the driver...I have no idea, lol).

[   34.711438] Linux agpgart interface v0.102
[   34.766417] agpgart: Detected Ati IGP320/M chipset
[   34.774741] agpgart: AGP aperture is 64M @ 0xd4000000
[  178.507237] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  178.509302] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  178.511137] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
-dmesg|grep agp output

1150 frames in 5.0 seconds = 229.785 FPS
1131 frames in 5.0 seconds = 226.189 FPS
1204 frames in 5.0 seconds = 240.750 FPS
1092 frames in 5.0 seconds = 218.277 FPS
1214 frames in 5.0 seconds = 242.789 FPS
1208 frames in 5.0 seconds = 241.416 FPS
1182 frames in 5.0 seconds = 236.208 FPS
1232 frames in 5.0 seconds = 246.205 FPS
1242 frames in 5.0 seconds = 248.345 FPS
1194 frames in 5.0 seconds = 238.791 
-glxgears output

Any help would be greatly appreciated. If I can get my graphics working to where they're at in Windows, I'll be in Ubuntu forever.

Thanks!

---

### Post by overdrank on 2008-05-21
> **NvidiaN said:**
> Hello all,

I have a question regarding my graphics and Ubuntu (Hardy Herring). I'm currently very very new to Ubuntu, just really installed it yesterday, and for the most part I'm quite pleased. I cannot however figure out how to make my laptop detect/use the ATI driver which is supposedly supported/provided by HH. I have a friend who had me type various commands into the terminal which came up with the following data (he claims it's "low" and that the computer isn't using the driver...I have no idea, lol).

[   34.711438] Linux agpgart interface v0.102
[   34.766417] agpgart: Detected Ati IGP320/M chipset
[   34.774741] agpgart: AGP aperture is 64M @ 0xd4000000
[  178.507237] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  178.509302] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  178.511137] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
-dmesg|grep agp output

1150 frames in 5.0 seconds = 229.785 FPS
1131 frames in 5.0 seconds = 226.189 FPS
1204 frames in 5.0 seconds = 240.750 FPS
1092 frames in 5.0 seconds = 218.277 FPS
1214 frames in 5.0 seconds = 242.789 FPS
1208 frames in 5.0 seconds = 241.416 FPS
1182 frames in 5.0 seconds = 236.208 FPS
1232 frames in 5.0 seconds = 246.205 FPS
1242 frames in 5.0 seconds = 248.345 FPS
1194 frames in 5.0 seconds = 238.791 
-glxgears output

Any help would be greatly appreciated. If I can get my graphics working to where they're at in Windows, I'll be in Ubuntu forever.

Thanks!

HI and welcome, you may find some help here
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by NvidiaN on 2008-05-21
> **overdrank said:**
> HI and welcome, you may find some help here
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

Thanks for the welcome!

Unfortunately I'm not understanding how that is helping (not to say that it wouldn't be helpful, if I were smarter). Judging from what I've read so far (~5 pages), it's about a compiz, no?

From what my friend told me my "straight out of the box" ubuntu is using the default VGA driver instead of the proper driver that comes with ubuntu. I'll keep looking to try and understand, hopefully I find it.

---

### Post by overdrank on 2008-05-21
> **NvidiaN said:**
> Thanks for the welcome!

Unfortunately I'm not understanding how that is helping (not to say that it wouldn't be helpful, if I were smarter). Judging from what I've read so far (~5 pages), it's about a compiz, no?

From what my friend told me my "straight out of the box" ubuntu is using the default VGA driver instead of the proper driver that comes with ubuntu. I'll keep looking to try and understand, hopefully I find it.

Hi and I may have misunderstood, If you would like use the driver that comes with HH then you should be able to just reconfigure your xorg from the command line. Then terminal is located under applications, accessories
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x with the keys ctrl, alt, backspace bar all at the same time. Hope this helps and good luck!

---

### Post by NvidiaN on 2008-05-21
> **overdrank said:**
> Hi and I may have misunderstood, If you would like use the driver that comes with HH then you should be able to just reconfigure your xorg from the command line. Then terminal is located under applications, accessories
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x with the keys ctrl, alt, backspace bar all at the same time. Hope this helps and good luck!

Thanks! I tried your suggestion by entering it in the terminal and it says:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080521191959

I don't think I have anything customized...so I'm kinda clueless as to the meaning of that message.

---

### Post by overdrank on 2008-05-21
> **NvidiaN said:**
> Thanks! I tried your suggestion by entering it in the terminal and it says:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080521191959

I don't think I have anything customized...so I'm kinda clueless as to the meaning of that message.

Hi and it is telling you that it reconfigured and that is your backup file incase the xorg fails when you restartx as mention before. that way you can replace that file and fix it. In short terms lol :)

---

### Post by NvidiaN on 2008-05-21
> **overdrank said:**
> Hi and it is telling you that it reconfigured and that is your backup file incase the xorg fails when you restartx as mention before. that way you can replace that file and fix it. In short terms lol :)

Oh would you look at that, it works. Yay! Thank you :) Now I can work on the information you originally posted, and attempt to get that program working ;)

Thank you!

---

### Post by overdrank on 2008-05-21
> **NvidiaN said:**
> Oh would you look at that, it works. Yay! Thank you :) Now I can work on the information you originally posted, and attempt to get that program working ;)

Thank you!

Good luck! :)

---

### Post by NvidiaN on 2008-05-22
Though you've been a great deal of help thus far, I have another question regarding the same topic!

Is it normal for firefox to "lag" when scrolling down a page? It seems to do it with every page I go to. Do I need to type something else into the terminal to make firefox use the drivers too? It just doesn't seem very smooth, like it's skipping or something.

---

### Post by overdrank on 2008-05-22
> **NvidiaN said:**
> Though you've been a great deal of help thus far, I have another question regarding the same topic!

Is it normal for firefox to "lag" when scrolling down a page? It seems to do it with every page I go to. Do I need to type something else into the terminal to make firefox use the drivers too? It just doesn't seem very smooth, like it's skipping or something.

Then you may not be using the correct drivers. take a look at the link I posted earlier
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by NvidiaN on 2008-06-21
-e- nevermind, I fixed it!

---

