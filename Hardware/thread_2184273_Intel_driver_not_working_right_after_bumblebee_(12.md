---
title: "Intel driver not working right after bumblebee (12.04LTS)"
date: 2013-10-28
forum: Hardware
---

### Post by johngiok on 2013-10-28
hello to all.

First post and thank you in advance .
I'm new to ubuntu and loving it .. but i own a laptop Allienware M11xr3 which runs in :
 lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108M [GeForce GT 540M] [10de:0df4] (rev ff)

after a clean install in ubuntu 12.04LTS everything worked fine .. except the heating problem and battery life
so i installed nvidia drivers but had issues with the resolution ,and i used purge and  --fix missing command to get ubuntu start again.

So i installed bumblebee+nvidia at the same command and by miracle it worked and battery life increased almost 3 times .
But.. then i realized that **i am running in unity 2D** allthough i have the latest xserver-xorg drivers and in synaptics package manager i even reinstalled the packages for intel VGA.
In **'System Settings' details in graphics** it has **Blanc** and in experience it says Standard
But now after LONG hours searching forums and googleing i cant get a solution to the problem.. 

im lost..

---

### Post by Yellow Pasque on 2013-10-28
Post /var/log/Xorg.0.log (use code tags or pastebin).

> In 'System Settings' details in graphics it has Blanc and in experience it says Standard
[https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)

---

### Post by johngiok on 2013-10-28
> **Temüjin said:**
> Post /var/log/Xorg.0.log (use code tags or pastebin).


[https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)

ok 
[ATTACH]247342[/ATTACH]


also i have installed mesa utils and before installing and purging the intel graphics card was showing in the details. i dont mind showing or not i just want to get Intel graphics to work properly and i think that it has something to do with this.

thanks for the reply though

---

### Post by Yellow Pasque on 2013-10-28
```
[ 12.990] (EE) AIGLX error: dlopen of /usr/lib/x86_64-linux-gnu/dri/i965_dri.so failed (/usr/lib/x86_64-linux-gnu/dri/i965_dri.so: cannot open shared object file: No such file or directory)
[ 12.990] (EE) AIGLX: reverting to software rendering
```

Try (re)installing the package that contains this file: libgl1-mesa-dri

---

### Post by johngiok on 2013-10-28
I think i love you ^^ 

It fixed everything graphics is showing Unity working in 3d all is good..

Having a laptop like this and using it with Ubuntu is showing my resolve to make it work .. And with support community that strong everything will be better for ubuntu.

---

