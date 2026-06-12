---
title: "Unity not working on ATI x1650 (RV535)"
date: 2011-10-12
forum: Hardware
---

### Post by xy2010 on 2011-10-12
Hello,

I need help with following problem. It looks like Unity is not working properly on my system. I'm using Ubuntu 11.04 (clean install, system updated today).

My gxf card:

```

dsu@ubox:~$ lspci -nn | grep VGA
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV535 [Radeon X1650 Series] [1002:71c7] (rev 9e)

```AFAIK this card should be able to run Unity/Compiz and driver seems to be fine as well:

```

dsu@ubox:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV530
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

```But when I log in (logon screen seems to be ok), all I can see is an empty desktop (just default background image, no panels at all) and a mouse cursor (functional, but useless).

I'm using 2 monitors, both connected via DVI-D to VGA adapters (idk if it matters).

There's no /etc/X11/xorg.conf file.

If I log in using "Ubuntu Classic (no effects)" option, I can work without any problems at all. But I would really like to be able to use fully functional Unity as well. 

Any ideas please? I will post more info if needed...

Thanks a lot.

:)

---

### Post by mastablasta on 2011-10-12
you can use Unity 2D, it's a unity without the 3D acceleration and effects. But still unity.
 
it might be able to run Unity but how good is another matter.

---

### Post by Elysius on 2011-10-12
Did you use the ATI proprietary driver? Try to download the latest driver from their website.

---

### Post by xy2010 on 2011-10-12
> **Elysius said:**
> Did you use the ATI proprietary driver? Try to download the latest driver from their website.

I've never used proprietary driver and I don't want to. My card isn't even supported by AMD/ATI anymore. 

People (on the internet) says open source driver should be working fine, even [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) says 3D support is good :)


> **mastablasta said:**
> you can use Unity 2D, it's a unity without the 3D acceleration and effects. But still unity.
 
it might be able to run Unity but how good is another matter.

I'm not sure what do you mean by Unity 2D. I can see these 3 options on logon screen:
1. Ubuntu (Unity, not working)
2. Ubuntu Classic (old compiz I guess, not working)
3. Ubuntu Classic - no effects (working fine)

---

### Post by xy2010 on 2011-10-12
I tried to generate xorg config file, but

```
sudo Xorg -configure
```

finished with this message:

```

(II) [KMS] No DRICreatePCIBusID symbol, no kernel modesetting.
Number of created screens does not match number of detected devices.

```

I'm not sure what does it mean and if it's related to my problem...

---

### Post by xy2010 on 2011-10-12
```

dsu@ubox:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 11.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

dsu@ubox:~$ 

```

It's strange, everything seems to be fine, I can't find anything suspicious in Xorg log either (I can post logs if needed).

---

### Post by xy2010 on 2011-10-30
I've finaly solved my problem. I've got rid of Ubuntu. :mrgreen:

---

