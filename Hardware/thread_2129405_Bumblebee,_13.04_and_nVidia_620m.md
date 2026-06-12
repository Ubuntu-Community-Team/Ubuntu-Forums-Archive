---
title: "Bumblebee, 13.04 and nVidia 620m"
date: 2013-03-26
forum: Hardware
---

### Post by rasmus91 on 2013-03-26
Hello people.

On my UX32VD I can't get optimus working. It's installed with ```
"sudo apt-get install bumblebee-nvidia nvidia-experimental-310"
```

however, when i Run:
```
optirun glxspheres
[ 1808.875145] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) No devices detected.

[ 1808.875203] [ERROR]Aborting because fallback start is disabled.

```

I can run primusrun but it switches to the Ivy bridge onboard GPU:
```
primusrun glxspheres
Polygons in scene: 62464
Visual ID of window: 0xb9
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Ivybridge Mobile 
60.929342 frames/sec - 67.997146 Mpixels/sec

```

I read somewhere that it might work if i did the vblank_mode but it didn't

```
vblank_mode=0 primusrun glxspheres
Polygons in scene: 62464
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
Visual ID of window: 0xb9
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Ivybridge Mobile 
208.169653 frames/sec - 232.317332 Mpixels/sec

```

The windows is looking like whatever is behind it when its run first.
I figure the key to fixing this is to get it to recognise the graphics card, but I have no idea how. I would very much like to have this working so any ideas are appreciated.

Im running the Raring ringtail beta, it is fully updated.

help me ubuntu forum you're my only hope ;)

---

### Post by Pixman on 2013-03-27
Try adding BusID  "PCI xx:xx.x" to the Devices in your xorg.conf

Worked for me.
You can find the PCI value with lspci for your graphic cards. That should help you perfectly.

---

### Post by rasmus91 on 2013-03-27
I can't see that I have a xorg.conf file, it should supposedly be found in:
/etc/X11/xorg.conf

right?

could you give me an example of how it's done properly?

thanks for the help :)

---

### Post by raidflex on 2013-04-05
> **Pixman said:**
> Try adding BusID  "PCI xx:xx.x" to the Devices in your xorg.conf

Worked for me.
You can find the PCI value with lspci for your graphic cards. That should help you perfectly.

This is a very vague response, considering the XORG file does not exist by default. I am also having the same issue, additional assistance would be appreciated.

---

### Post by shakalys on 2013-04-05
problem is with xorg. More info [https://github.com/Bumblebee-Project/Bumblebee/issues/367](https://github.com/Bumblebee-Project/Bumblebee/issues/367)

---

### Post by raidflex on 2013-04-05
> **shakalys said:**
> problem is with xorg. More info [https://github.com/Bumblebee-Project/Bumblebee/issues/367](https://github.com/Bumblebee-Project/Bumblebee/issues/367)

Seems like reverting back to a previous xserver is a work around for now at least.

---

### Post by Dabo Ross on 2013-04-11
According to this[<https://wiki.ubuntu.com/Bumblebee>]("https://wiki.ubuntu.com/Bumblebee"), bumblebee is supported up to 12.10, so do you know if it works on your computer in 12.10?
It will be easier to fix if we know if it is specific to 13.04 or if it is specific to your system.

If you don't know with 12.10, and you don't want to install, you can always - I think - boot into a live usb of 12.10, install bumblebee, test it, and have no changes to your system.

Also creating xorg.conf breaks optimus systems (at least it breaks mine).
When I create a new xorg.cong with whatever settings, my system always starts up in "low graphics mode", or with 640x480 resolution. When I delete xorg.conf, it goes back to normal. So I don't think creating an xorg.conf or having any settings in it is going to help that much.

Also Does anyone else have bumblebee working in 13.04?

---

### Post by shakalys on 2013-04-12
Bumblebee works on 13.04 on my asus ux32vd with nvidia 620m

install bumblebee ( [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee) ) 
you don't need to create any xorg.conf

after install add:

BusID "PCI:01:00:0"  (or find correct id with lspci | grep NVIDIA )

in the DEVICE section in /etc/bumblebee/xorg.conf.nvidia

for more info and status please look at [https://github.com/Bumblebee-Project/Bumblebee/issues/367](https://github.com/Bumblebee-Project/Bumblebee/issues/367)

---

### Post by jackcy on 2013-04-14
I can confirm a orking bumblebee version on 13.04 after adding the BusID to the config file.

01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce GT 520M] (rev ff)

Great job!:)

---

### Post by ryanvade on 2013-04-15
Works great with my GT 630m.  THANK YOU!!!

---

### Post by ospinakamilo on 2013-04-25
Adding the BusID also works for nvidia Geforce 610M ;)

---

### Post by rasmus91 on 2013-05-24
After the official release of 13.04 and a primus reinstall, it works perfectly :)

---

