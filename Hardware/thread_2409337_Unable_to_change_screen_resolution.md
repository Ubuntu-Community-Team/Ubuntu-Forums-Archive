---
title: "Unable to change screen resolution"
date: 2018-12-31
forum: Hardware
---

### Post by dpopp783 on 2018-12-31
I just built my first PC! (WOOT) This is my first time using Linux. My issue is that I'm using a Dell u3415w monitor, with a resolution of 3440x1440 pixels, but the resolution right now is 1024x768 (4:3) and it is the only option available in the settings. (Attachment is image of settings)

How can I change the screen resolution? Thanks for any help!



Note: When I run xrandr in the terminal this was the output:

```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768      76.00* 


```

I'm not really sure what xrandr is, I just saw it when looking around for a way to fix my resolution, but I'm guessing the maximum resolution isn't supposed to me 1024x768

---

### Post by dpopp783 on 2018-12-31
Also if it's relevant my graphics card is a Gigabyte rtx 2070

---

### Post by CatKiller on 2018-12-31
> **dpopp783 said:**
> Also if it's relevant my graphics card is a Gigabyte rtx 2070

Have you installed the proprietary nvidia driver? It will need to be at least version 410 to support that card. 

> **dpopp783 said:**
> I'm not really sure what xrandr is

It's the control for X's Resize and Rotate extension.

---

### Post by dpopp783 on 2018-12-31
> **CatKiller said:**
> Have you installed the proprietary nvidia driver? It will need to be at least version 410 to support that card. 


I don't think so. How do I do that?

---

### Post by dpopp783 on 2018-12-31
[COLOR=#272A34][FONT=&quot]I ended up installing the driver following this tutorial: [/FONT][/COLOR][https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux)

---

